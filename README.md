# aws_sso_git_solution
In this repo I provide solution for windows and mac user to perform git commands on code commit on aws account with SSO sign in /authentication


### The section covers CodeCommit GIT and helpers that are not easily available in AWS Docs.

CodeCommit with Federated Access
AWS CodeCommit requires below configuration with Federated User Access/SSO

CodeCommit For Federated Access

1.  # Replace "my-profile" in below command and execute below before cloning git repo
2. git config --global credential.helper '!aws --profile "my-profile" codecommit credential-helper $@'
3. git config --global credential.UseHttpPath true

Especially for Mac users:
Delete any credential stored already in os-keychain (Finder → Applications → Keychain Access, search for codecommit and delete any entries found - if any)
Go to SSO ang click on command line or programatic access. After logging in, get credentials (#2) and add them to your AWS credentials file (~/.aws/credentials)
Run the following command replacing profile name with yours (something like 81******_Allowed_Access_North_Virginia )
git config --global credential.helper '!aws --profile "<your_profile_name>" codecommit credential-helper $@'
your_profile_name will be like default or if you set any!
Run
git config --global credential.UseHttpPath true

Now you should be able to run
git clone <repo_name>

** Getting new AWS credentials should be repeated about every 24 hours. We are working with AWS to fix that.

** Git credentials can possibly populate again in keychain. In that case, you need to delete them manually. We investigate why this happens to some users and not to others.
