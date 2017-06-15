# rebasing in mercurial for dimwits.


## Step 1. Get rebase

First, enable the rebase extension by editing:

	$env:userprofile\mercurial.ini
	
And in the `[extensions]` section, write:

	rebase =


Confirm you have the rebase extension installed by typing:

	hg help extensions

And at that bottom of that output you should see:

    enabled extensions:

     color         colorize output from some commands
     extdiff       command to allow external programs to compare revisions
     fetch         pull, update and merge in one command (DEPRECATED)
     mq            manage a stack of patches
     rebase        command to move sets of revisions to a different ancestor


## Using rebase


Let's say while you were making some local revisions, X,Y&Z:


![rebase1](rebase1.png)

Meanwhile, let's assume some other turkey (let's call him Richard) was making other revisions, D and E.

You want to linearize your commits, so that X Y and Z follow D and E.

![rebase2](rebase2.png)

Here's the command:

	hg rebase -s X -d E

You won't use the literal letters "X" and "E". You'll use the revision numbers. i.e. the number that appears before the revision hash:

![revnum](revnum.png)

So you're command might be more like:

	$myEarliestCommit = 100
	$otherPeoplesLastCommit = 115
	hg rebase -s $myEarliestCommit -d $otherPeoplesLastCommit



## Source


 * [Rebase Extension](https://www.mercurial-scm.org/wiki/RebaseExtension)