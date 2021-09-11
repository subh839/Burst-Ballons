# Burst-Ballons

   int dp[502][502];
    int help(vector<int>&nums,int i,int j)
    {
        if(i>j)
            return 0;
            if(dp[i][j]!=-1)
                return dp[i][j];
        int maxi=INT_MIN;
        
        for(int k=i;k<=j;k++)
        {
            int temp=help(nums,i,k-1)+help(nums,k+1,j);
            int l=1,r=1;
            if(i-1>=0)
                l=nums[i-1];
            if(j+1<nums.size())
                r=nums[j+1];
            temp+=l*r*nums[k];
            maxi=max(maxi,temp);
        }
        return dp[i][j]=maxi;
        
    }
    int maxCoins(vector<int>& nums) {
        memset(dp,-1,sizeof dp);
        int n=nums.size();
        return help(nums,0,n-1);
        
    }
