# Understanding Rebase

## Step 1: Create a new repository

In order to get more familiar with git, we want you to initialize a new repository.
Go to GitHub and click the + beside your username. Then click "new repository".
Go ahead and name the repository and click the button to initialize it with a
README. Now select the "clone or download button". This will give you a url.
Now use the command line to navigate to where you want to initialize this
repository and run
```bash
git clone <url>
```
You now have a folder which contains only the README file. Go ahead and add a
new Python file, you can name it whatever you'd like.

## Step 2: Work on a new branch

Run the command
```bash
git checkout -b new-feature
```
to create a branch called new-feature and switch to it. Now that you are on the
new-feature branch, go ahead and add a hello world function to the Python file.
Now commit these changes by running
```bash
git add .
git commit -m "some comment to explain the code you added"
git push origin new-feature
```

## Step 3: Update the master branch

Go to the repository on GitHub. While still on the master branch, make some
change to the README file. This is essentially a simulation of the master branch
being updated by a teammate while you were working on the new-feature branch.
Now from the command line, run
```bash
git checkout master
git pull origin master
git checkout new-feature
```
These commands updated your master branch with the change you made on GitHub
and then moved you back to the new-feature branch.

## Step 4: Rebase

Here is the problem: the code in the master branch has been updated since you
started working on the new-feature branch. This means that the code you are
writing is built on top of an out of date repository. There are different ways
to fix this but the one we are going to look at now is called rebase. In the
command line, run
```bash
git log
```
Notice how many commits you see. Now run
```bash
git rebase master
```
This has made it so that the changes you made in the new-feature branch, effectively
were built on the up-to-date code in master. You can verify this by again running
```bash
git log
```
You should see that there is now one more commit listed. This is because the
commit which changed the README file is now included in the history of the
new-feature branch.
