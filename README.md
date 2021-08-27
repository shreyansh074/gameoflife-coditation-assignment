import java.util.*;
public class Main
{
	public static void main(String[] args) {
		Scanner input=new Scanner(System.in);
		System.out.println("Enter no. of row :");
		int row=input.nextInt();
		System.out.println("Enter no. of col :");
		int col=input.nextInt();
		int grid[][]=new int[row][col];
		for(int i=0;i<row;i++){
		for(int j=0;j<col;j++){
		     grid[i][j]=input.nextInt();
		 }   
	    }
	    GameOfLife ob=new GameOfLife();
	    ob.GoL(grid);
	    for(int i=0;i<row;i++){
		 for(int j=0;j<col;j++){
		 System.out.print(grid[i][j]+" ");
		 }
		System.out.println();
	    }
	}
}
class GameOfLife{
    public void GoL(int[][] board) {
		for (int i = 0; i < board.length; i++) {
			for (int j = 0; j < board[0].length; j++) {
				int count = 0;
				if (i - 1 >= 0 && j - 1 >= 0 && Math.abs(board[i - 1][j - 1]) == 1) {
					count++;
				}
				if (i - 1 >= 0 &&  Math.abs(board[i - 1][j]) == 1) {
					count++;
				}
				if (i - 1 >= 0 && j + 1 < board[0].length && Math.abs(board[i - 1][j + 1]) == 1) {
					count++;
				}
				if (j - 1 >= 0 && Math.abs(board[i][j - 1]) == 1) {
					count++;
				}
				if (j + 1 < board[0].length && Math.abs(board[i][j + 1]) == 1) {
					count++;
				}
				if (i + 1 < board.length && j - 1 >= 0 && Math.abs(board[i + 1][j - 1]) == 1) {
					count++;
				}
				if (i + 1 < board.length && Math.abs(board[i + 1][j]) == 1) {
					count++;
				}
				if (i + 1 < board.length && j + 1 < board[0].length && Math.abs(board[i + 1][j + 1]) == 1) {
					count++;
				}
				if (board[i][j] == 0 && count == 3) {
						board[i][j] = 2;
				} else if (board[i][j]==1 && (count < 2 || count > 3)) {
					board[i][j] = -1;
				}

			}
		}
		for (int i = 0; i < board.length; i++) {
			for (int j = 0; j < board[0].length; j++) {
				if (board[i][j] == 2) {
					board[i][j] = 1;
				} else if (board[i][j] == -1) {
					board[i][j] = 0;
				}
			}
		}

	}
}
