# DP-8

## Problem1 Arithmetic Slices (https://leetcode.com/problems/arithmetic-slices/)
## Time Complexity:O(n) Space Complexity:O(n)
class Solution {
    public int numberOfArithmeticSlices(int[] nums) {
        if(nums.length<3)
        return 0;
        int[] dp=new int[nums.length];
        Arrays.fill(dp,0);
        for(int i=2;i<nums.length;i++)
        {
            if((nums[i]-nums[i-1])==(nums[i-1]-nums[i-2]))
            {
                dp[i]=dp[i-1]+1;
            }

        }
        int sum=0;
        for(int i=0;i<dp.length;i++)
        {
          sum+=dp[i];
        }
        return sum;
    }
}

## Problem 2 Triangle (https://leetcode.com/problems/triangle/)
## Time Complexity:O(n2) Space Complexity:O(n2)
class Solution {
    
    public int minimumTotal(List<List<Integer>> triangle) {
        int[][] memo=new int[triangle.size()][triangle.size()];
        for(int[] row:memo){
            Arrays.fill(row,Integer.MAX_VALUE);
        }

        return helper(triangle,0,0,memo);
       
    }

    private int helper(List<List<Integer>> triangle,int r,int c,int[][] memo)
    {
        if(r==triangle.size()){
            return 0;
        }

        if(memo[r][c]!=Integer.MAX_VALUE)
        {
            return memo[r][c];
        }

        int left=helper(triangle,r+1,c,memo);
        int right=helper(triangle,r+1,c+1,memo);
        memo[r][c]=triangle.get(r).get(c)+Math.min(left,right);
        return memo[r][c];
    }

    

}
