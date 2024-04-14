# Adding SSH Key to Github Tutorial

### Author : Rahul Bhoyar

Setting up an SSH key for your GitHub account is like giving your computer a special secret handshake to securely communicate with GitHub. It's important because it adds an extra layer of security by ensuring that only your computer, with the correct key, can access your GitHub account. This helps prevent unauthorized access and keeps your account and data safe from potential threats. Additionally, using an SSH key makes it easier to connect to GitHub repositories without having to repeatedly enter your username and password, saving you time and hassle. Overall, it's a simple but effective way to protect your GitHub account and streamline your workflow.

In this tutorial, we shall learn how to set up a SSH key to your Github account in simple steps.

### (A) For iOS
#### Step 1: Check for Existing SSH Keys

Before generating a new SSH key, let's check if you already have one. Open Terminal on your Macbook and type the following command:

```
ls -al ~/.ssh
```

Look for files named id_rsa and id_rsa.pub. If these files exist, you already have an SSH key and can skip to Step 3. Otherwise, proceed to Step 2.

#### Step 2: Generate a New SSH Key

To generate a new SSH key, type the following command in Terminal:
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Replace "your_email@example.com" with the email associated with your GitHub account. Press Enter to accept the default file location (~/.ssh/id_rsa) and to leave the passphrase empty if you don't want to use one.

#### Step 3: Add SSH Key to SSH Agent

Run the following command to start the SSH agent:
```
eval "$(ssh-agent -s)"
```
Then, add your SSH key to the SSH agent:
```
ssh-add ~/.ssh/id_rsa
```
#### Step 4: Add SSH Key to Your GitHub Account

First, copy the SSH key to your clipboard using:
```
pbcopy < ~/.ssh/id_rsa.pub
```
Next, go to GitHub and navigate to **Settings > SSH and GPG keys > New SSH key**.

Paste the SSH key into the "Key" field and give it a descriptive title.

#### Step 5: Test Your SSH Connection

To ensure everything is set up correctly, run the following command in Terminal:
```
ssh -T git@github.com
```
You should see a message indicating a successful connection to GitHub.

### (A) For Windows OS

#### Step 1: Check for Existing SSH Keys

Before generating a new SSH key, let's check if you already have one. Open Command Prompt on your Windows PC and type the following command:
```
dir %userprofile%\.ssh
```
Look for files named id_rsa and id_rsa.pub. If these files exist, you already have an SSH key and can skip to Step 3. Otherwise, proceed to Step 2.

#### Step 2: Generate a New SSH Key

To generate a new SSH key, type the following command in Command Prompt:
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Replace "your_email@example.com" with the email associated with your GitHub account. Press Enter to accept the default file location (%userprofile%\.ssh\id_rsa) and to leave the passphrase empty if you don't want to use one.

#### Step 3: Add SSH Key to SSH Agent

Run the following command to start the SSH agent:
```
eval `ssh-agent -s`
```
Then, add your SSH key to the SSH agent:
```
ssh-add %userprofile%\.ssh\id_rsa
```

#### Step 4: Add SSH Key to Your GitHub Account

First, copy the SSH key to your clipboard using:
```
clip < %userprofile%\.ssh\id_rsa.pub
```
Next, go to GitHub and navigate to Settings > SSH and GPG keys > New SSH key.

Paste the SSH key into the "Key" field and give it a descriptive title.

#### Step 5: Test Your SSH Connection

To ensure everything is set up correctly, run the following command in Command Prompt:
```
ssh -T git@github.com
```
You should see a message indicating a successful connection to GitHub.

### Purpose of Private and Public SSH Keys :

**(A) Private SSH Key:** 
This key is kept on your local device, such as your computer. It is a closely guarded secret and should never be shared with anyone. The private key is used to authenticate your identity when you connect to a remote server, such as GitHub. It's essentially your digital signature that proves you are who you say you are.

**(B) Public SSH Key:** 
On the other hand, the public SSH key is shared with the remote server, such as GitHub. It is stored on the server and is used to verify your identity when you attempt to connect. While the public key is safe to share, as it cannot be used to gain access to your account without the corresponding private key, it plays a crucial role in the authentication process by confirming that you possess the corresponding private key.

In summary, the private SSH key is kept secret and is used for authentication on your local device, while the public SSH key is shared and stored on remote servers to verify your identity when connecting to them.


### Cloning a Repository Using SSH

Once your SSH connection to GitHub is established, you can easily clone a repository using SSH commands. Here's how:

(1) Navigate to the repository on GitHub that you want to clone.

(2) Click on the green "Code" button and select "SSH" to switch to the SSH URL.

(3) Copy the SSH URL provided (e.g., git@github.com:user/repository.git).

Open Command Prompt on your computer and navigate to the directory where you want to clone the repository.

(4) Use the git clone command followed by the SSH URL you copied earlier. For example:

```
git clone git@github.com:user/repository.git
```
Replace user/repository with the appropriate username and repository name.

(5) Press Enter, and Git will clone the repository to your local machine using the SSH protocol.

Congratulations! You've successfully tested your SSH connection to GitHub and cloned a repository using SSH commands. You can now work with the repository locally and push changes back to GitHub securely using SSH.

