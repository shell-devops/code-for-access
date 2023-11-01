# code-for-access
This script is used to find the people and list whose has access to the s3 bucket
#!/bin/bash

#########
# About: This script will list the people who can access your repo
# Input: your token key
# Date: 18/10/2023
# owner: Yathin 
#########

hilper()
    
# GITHub API URL
API_URL="https://api.github.com"

# GitHub username and personal access token 
USERNAME=$username
TOKEN=$token

#User and Repository information
REPO_OWNER=$1
REPO_NAME=$2

# Function to make a GET request to the GitHub API 
function github_api_get {
local endpoint="$1"
local Url="${git_api_Url}/${endpoint}"

#Send a GET request to the GitHub API with authentication 
curl -s -u "${USERNAME}:${TOKEN}" "$url"
}

#Function to list users with read access to the repository
function list_users_with_read access {
local endpoint="repos/${REPO_OWNER}/${REPOS_NAME}/collabrators"

#Fetch the list of collaborators on the repository
collaborators="$(github_api_get "$endpoint" | jq -r '.[] | select(.permissions.pull == true) | .login')"

# Display the list of collaboraties on the repository
if [[ -z "$collaborators" ]]; then 
echo "No users with read access found for ${REPO_OWNER}/${REPO_NAME}."
else
echo "Users with read access to ${REPO OWNER}/${REPO NAME}:"
echo "$collaborators"
fi
}


function helper{
 expected_cmd_args=2
if[ $# -ne $expected_cmd_args]; then
echo "Please execute the script with required cmd args"
echo "asd"
}

# Main script

echo "Listing users with read access to ${REPO_OWNER}/${REPO_NAME}..."
list_users_with_read_access
