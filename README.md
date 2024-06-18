# Getting Started with AWS Amplify and React

1. Install AWS Amplify CLI on your desktop
npm install -g @aws-amplify/cli

2. Configure amplify for your app
amplify configure
launches AWS console
Prompts you to sign in (as administrator)
```
Select your region (e.g. us-east-1)
```
Navigate to user creation page in IAM (create the application user, e.g., my-amplify-dev)
Attach policy directly to user
Select "AdministratorAccess-Amplify"
Select Create User
Capture Access key and Secret Access key for IAM user
Use Command Line when creating new Access Key
```
Enter the access key for newly created user:
? accessKeyId: [hidden]
? secretAccessKey: [hidden]

This would update/create the AWS profile in your local machine
? Profile Name: my-amplify-local
```
3. Create sample React App
npx create-react-app my-amplify-app
cd my-amplify-app

4. Initialize your React app with amplify
```
amplify init

? Enter a name for the project: myamplifyapp
```
Select the defaults after verifying they are correct

```
? Select the authentication method you want to use: (use arrow keys)
> AWS profile
  AWS access keys
```
Select the profile (my-amplify-local)
Select defaults to continue

5. Integrate Amplify with Cognito for user management
```
amplify add auth

```
Select default configuration (for Cognito)
```
Do you want to use the default authentication and security configuration? Default configuration
```
```
How do you want to be able to sign in? (Use arrow keys)
  Username
> Email
  Phone Number
  Email or Phone Number
  I want to learn more.
```
Select Email
Select No to configure advanced settings

### Note:
The configurations so far are stored locally, then need to be pushed to Amplify.

```

```

6. Push the code to Amplify, select the defaults
```
amplify push
```

7. Install the Amplify libraries that will give the login UI and functionality
```
npm install aws-amplify @aws-amplify/ui-react
```

8. Update your code (e.g. App.js) to include amplify libraries

9. Run the application (runs locally on your dev laptop)
```
npm start
```
10. Create an account using a valid email address
Capture the code sent to the email address to verify
Log in with newly created account

11. Upload code to GitHub
Create new Repo in GitHub, call it (e.g.) my-amplify-app
Capture the url for the origin (e.g. https://github.com/ran-github/my-amplify-app.git)

Initialize local Git repo, point to remote origin, push to GitHub
```
git init
git add .
git commit -m "Initial version"
git branch -M main
git remote add origin https://github.com/ran-github/my-amplify-app.git
git push -u origin main
```

12. Configure CI/CD within Amplify (i.e. configure repo for source code)
Within AWS Console browse over to "Backend environments" for your app (myamplifyapp)
Select GitHub
Authorize Cognito to access GitHub
Select the specific project you want to integrate with Amplify
Set branch to main

Set the following as shown:
Select a Backend envoronment to use with this branch: myamplifyapp
Environment: Dev
Enable full-stack continuous deployment (CI/CD): checked

Select an existing service role or create a new one so Amplify Hosting may access your resources

13. Create a new one:
- Trusted entity type: AWS Service
- Use case Amplify
- Amplify - Backend Deployment

-> Next

- Permission policies: AdministratorAccess-Amplify

-> Next

- Role name: amplifyCICDRole

Accept defaults and create role

14. Go back to step 12, select an existing role, choose amplifyCICDRole

-> Next

Save and deploy
