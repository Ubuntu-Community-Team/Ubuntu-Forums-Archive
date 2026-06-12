---
title: "2 questions on ssh and sshfs differences"
date: 2008-10-25
forum: Server Platforms
---

### Post by skotos on 2008-10-25
I have been using ssh to remotely login into my computers for years, but in these days I started thinking on using ssh to manage my files, thus I installed sshfs.
First of all, I found that **nautilus correctly shows the mounted file system but, on the contrary, on the command line, I do not see anything: the mount point is empty**. Wow!

First question: _is there anything that has to be run in order to have a command line support too?_

Then, I incurred into another problem. To be sure that everything was good enough to completely forget about samba shares, nfs and definetly simplify my configurations, I wanted to first delete all the files and the directories from my networked client and second recopy them back: I thought that if everything had gone fine, I would have been sure the configuration was good enough to switch.
So I started deleting everything from nautilus and I discovered that I was not able to remove anything but the files inside each directory and then - and only then - remove their parent directory.

Here it is the second question: _if I have the required privileges to remove the files inside a directory and then to remove their parent directory (the directory in which the just deleted files were), I think that nautilus should have all the required authorizations to automatically remove everything:_ **requesting the directory removal should be enough to delete everything inside of it**. _Why is it not possible if I have all the rquired authorization to manually delete everything is inside of it? Is it a bug related to a wrong api call or an error of mine?_

Furthermore, if I go to the prompt and directly login by ssh, I can delete every file and every directory with no security issue...

Any help distinguishing if it is a bug or some feature I might have misconfigured would be greatly appreciated.

The sshfs command I run is```
sshfs myRemoteUser@myRemoteSSHServer:/var/shared/myEBooks /home/myLocalUser/Private/myRemoteSSHServer/myEBooks
```

---

### Post by insineratehymn on 2009-03-05
It seems like this is old... but.... -o allow_other after sshfs should do the trick. :P

---

### Post by skotos on 2009-03-15
> **insineratehymn said:**
> It seems like this is old... but.... -o allow_other after sshfs should do the trick. :P
Thank you. I will try it.

---

### Post by rkdwv on 2009-04-16
> **skotos said:**
> Thank you. I will try it.

That doesn't helped to me. Please say - did you solve the problem?

---

