---
title: "GRsync --EXCLUDE command syntax"
date: 2010-07-19
forum: Security
---

### Post by majortom67 on 2010-07-19
Hi.
I apologize if this is not the correct place for my question. Moderators my places it elsewhere.

I'm trying to backup a whole startup disk to another with GRSYNC but I don't need some files or directories. For example, I don't want to backup my 'swapfile1' (I do not have a dedicated swap partition) or the 'media' directory' in order to no enter a looping sync.
I've searched the web for the correct syntax of the --exclude command but none have worked if applied in the advanced option "before" rsync starts. These a sample of NOT workin syntaxes:

-- exclude /media or -- exclude 'media' or -- exclude "media"

same for swapfile1:

-- exclude swapfile1 or -- exclude 'swapfile1' or -- exclude "swapfile1"

Any help is appreciated.

Simon

---

### Post by _Mark_ on 2010-07-19
From what i remember of rsync the --exclude 'media' has to be relative to what you are backing up

So if you are backing up everything you will have to use the fully qualified  path to the folder you want to exclude

---

### Post by majortom67 on 2010-07-19
Thanks _Mark_

The 'media' folder is at the root level so the command should be:

-- exclude '/media'

Right? It doesn't work

The 'swapfile1', also. Should it be:

--exclude 'swapfile1'

or

--exclude '/swapfile1' ?

Many Thanks

Simon

---

### Post by _Mark_ on 2010-07-19
Not sure then matey

Can you post the full command you are using?

Edit: I have never used grsync is in not just a gui for rsync? why are you having to enter command line options

---

### Post by _Mark_ on 2010-07-19
What you are trying to so will never work, the commands before and after rsync starts are for instance to mount and unmount file systems, not for adding switches when rsync is running.

As far as i can see their is no way to use the --exclude switch with grsync

You will have to use good old command line rsync

Edit: Have installed grsync and on the advanced tab at the bottom the additional options field add you're excludes lines there

---

### Post by cariboo on 2010-07-19
You can add excludes under the advanced options tab. See screenshot.

---

### Post by majortom67 on 2010-07-20
THANK YOU EVERYBODY !!!

Simon

---

### Post by The Cog on 2010-07-20
I think the syntax goes along the lines of **--exclude=media** without any spaces. This will of course skip any files/directories named media o you might need to experiment with **--exclude=/media** which I haven't ever tried.

---

### Post by ashv3524 on 2012-01-08
using --exclude=lost+found in the Advanced Options tab in grsync works great for me to exclude the lost+found folders on drives. Thanks very much!!!

---

