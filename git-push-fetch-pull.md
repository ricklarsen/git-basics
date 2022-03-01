## What is the difference between push, pull, and fetch?

Git provides several commands to share changes between a remote repository and your local repo.

- `git push` - send changes from a local branch to a remote repo.
- `git fetch` - get changes from a remote repo into your tracking branch.
- `git merge` - merge one branch into another; used here to merge your tracking branch into your local branch.
- `git pull` - get changes from a remote branch into your tracking branch and then merge them into your local branch.

The `git push` and `git pull` commands are often described as opposite but equivalent. 
This isn't entirely correct, because `git pull` combines two commands, `git fetch` and `git merge`.

### Get changes from a remote repo

There are two primary options to get changes from a remote repository. 

#### Use `git fetch` then `git merge` to get changes

Some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before merging.
Use `git fetch <remote> <branch>` to check for changes in the remote branch and pull them into the tracking branch. Replace `<remote>` with the name of your remote repo and `<branch>` with the name of your tracking branch.
This does not change your local branch.

To change your local branch to include these changes, use `git merge <remote>/<branch>` to merge those changes into your local branch.

#### Use `git pull` to get changes

If you are confident you understand the changes, use `git pull <remote> <branch>`, which runs `git fetch <remote> <branch>` followed immediately by `git merge <remote> <branch>`.

We recommend getting changes from the remote repository before pushing changes so you can resolve any conflicts locally.

### Send changes to a remote repo

When your local changes are stable, use `git push <remote> <branch>` to send them to the remote repo. This command  checks that there is a tracking branch for a remote repository connected to your local branch. 
If so, your changes are pushed to the remote branch. 

This fails if the remote branch has diverged from your local branch, that is, if not all commits in the remote branch are in your local branch.
When this happens, your local branch needs to be synchronized with the remote branch with `git pull` or `git fetch` and `git merge`.
