---
title: "Git worktrees"
date: 2020-06-16
---

Did you ever want to check out multiple branches in your Git clone at the same time? Maybe you have a repo for which switching branches takes a prohibitively long time.

You can use the worktrees feature in Git to approximate having multiple clones of the same repo on your machine.  Here's how it works.

When you create a worktree from an existing clone, you specify a directory (must be outside of the existing working directory) and a branch name, and Git creates an additional working directory at the location you specified, with the branch you specified already checked out. You'll be able to have a different branch checked out in the worktree than in the main working tree. Any commits you make in the worktree are visible in the original directory -- immediately -- and vice-versa.  

```cmd

git worktree add ../my-worktree-dir master
git worktree list
git worktree remove ../my-worktree-dir

```

You can create as many worktrees as you like.

One cool way to use this is as an alternative to stashing changes. Say you have a bunch of active changes and you don't want to stash or commit. Add a worktree, do your work, commit, and then remove the worktree. The ongoing work in the original directory remains exactly as it was.

Also, worktrees use less disk space than multiple full-blown clones because Git intelligently manages when it actually duplicates on your hard drive and when it just uses symbolic linking.  

For example, I use a repo that has about 30k files. A clone takes about 1 GB of disk space, but a worktree takes only 150 MB.

Similarly, cloning takes 90 seconds; adding a worktree takes 20 seconds. 

Note that you can't have the same branch checked out simultaneously in different worktrees.

[@tedhudek](https://twitter.com/tedhudek)

## Resources

[Git worktree documentation page](https://git-scm.com/docs/git-worktree)
