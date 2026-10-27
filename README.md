#studyroute
_-cd ~/Desktop
-mkdir devops-git-workflow
-cd devops-git-workflow
-pwd

#If mkdir says the folder already exists, do not create another one.
Run cd ~/Desktop/devops-git-workflow and continue.
Part 2 --- Create your first file
Create a README file and add a heading:
echo "# DevOps Git Workflow Practice" > README.md
next; view file
cat README.md

#Part 3 --- Initialize Git and check the status
Initialize Git inside this project folder:
git init -b main
This creates a local Git repository and names the first branch main.
If your Git version does not support git init -b main, use:
git init
git branch -M main
git status
---

-You should see README.md listed as an untracked file. That means
Git sees the file but is not tracking it in a commit yet.
Part 4 --- Stage and commit your first file
Stage the file:
git add README.md

**Check what is staged**
-git status

-git commit -m "Add project README"

#=Explanation:
•	git add README.md stages this file for the next commit.
•	git commit -m "Add project README" saves a snapshot of the staged
changes in your local Git history.
•	The text after -m is a short description of the change. You can
choose other clear messages, such as "Create project README".
If Git asks you to configure your identity, use your own name and email:

git config --global user.name "Your Name"
git config --global user.email your-email@example.com
Check the history:+
++it log –oneline

You should see your new commit.
Part 5 --- Create the remote repository on GitHub
1.	Open https://github.com and sign in.
2.	Click the + menu, then New repository.
3.	Enter this repository name: devops-git-workflow.
4.	Choose Public or Private according to your preference.
5.	Because you already created a local README and committed it, leave
Add a README file unchecked. Also leave other initialization
options unchecked so the remote repository starts empty.
6.	Click Create repository.
GitHub will show the repository page and its URL. For the SSH method, it
should look like:
git@github.com:YOUR-GITHUB-USERNAME/devops-git-workflow.git


Part 6 --- Connect your local project to GitHub
Return to Git Bash. Confirm you are still in your project folder:
pwd


git remote add origin git@github.com:YOUR-GITHUB-USERNAME/devops-git-workflow.git

Check the remote:
git remote -v

git push -u origin main


Part 7 --- Create a feature branch
Back in Git Bash, create and switch to a branch for a change:
git switch -c feature/add-learning-goals

git branch

part 8 --- Make a change, stage it, and commit it
Append a learning-goals section to the README:
cat >> README.md <<'EOF'

## Learning goals

- Practise Git branches.
- Push changes to GitHub.
- Open and merge a pull request.
- Pull merged changes to the local computer.
EOF

Review the change:
cat README.md
git status
git diff

Stage and commit:
git add README.md
git commit -m "Add DevOps learning goals"

git log –oneline

Check the commit:
git log --oneline
Part 9 --- Push the feature branch to GitHub
git push -u origin feature/add-learning-goals

This uploads the feature branch and its commit to GitHub. It does
not merge the branch into main.
Part 10 --- Open a pull request on GitHub
1.	Open your devops-git-workflow repository on GitHub.
2.	GitHub may show a Compare & pull request button for the branch
you just pushed. Click it. If not, open Pull requests → New
pull request.
3.	Set the base branch to main.
4.	Set the compare branch to feature/add-learning-goals.
Add DevOps learning goals.
7.	Click Create pull request

art 11 --- Merge the pull request
On the pull request page:
1.	Review the changed files.
2.	Click Merge pull request.
3.	Confirm the merge when GitHub asks.
For this practice, you can merge your own PR if GitHub permits it. In a
team, another person may review and approve the PR first.
Part 12 --- Pull the merged changes to your local computer
First return to your local main branch:
git switch main

Pull the latest main branch from GitHub:
git pull origin main

•	git switch main changes your working branch to main.
•	git pull origin main fetches the remote updates and integrates
them into your local main branch.
Now verify the file:
cat README.md
git status
git log --oneline --all

Part 13 --- Optional cleanup after merging
You can keep the feature branch for further practice. If you want to
delete your local feature branch after confirming it has been
merged, run:
git branch -d feature/add-learning-goals


