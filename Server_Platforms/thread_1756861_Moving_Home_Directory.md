---
title: "Moving Home Directory"
date: 2011-05-12
forum: Server Platforms
---

### Post by zaski on 2011-05-12
Hi all,
I have a situation here..
I have setup my server inside a Virtual Machine and all are working fine... after a while, I decided to add a second HardDisk dedicated only for the /home directory.. Now I want to move the current content of my /home directory to the new HD with everything in it all intact.
Any suggestions how may I do that?

Tried several google search but can't find anything really very reliable..
Thanks so much. . .:)

---

### Post by samosamo on 2011-05-12
You were probably googling wrong because this very simple.  Here is the basic idea:

Partition and format your new drive
Boot to single user mode
Unmount /home if needed
Move /home to /home.old
Add new drive to fstab as /home
Reboot to multiuser level
Done

---

### Post by Lars Noodén on 2011-05-13
> **samosamo said:**
> 
Reboot to multiuser level


Those steps will do it well.  The reboot is not necessary [telinit](http://manpages.ubuntu.com/manpages/natty/en/man8/telinit.8.html) can change the runlevel from Single user to something multiuser without rebooting.

For example,
```

telinit 2

```

That will cause it to run all the steps it would normally boot up with.

---

### Post by SeijiSensei on 2011-05-13
> **samosamo said:**
> You were probably googling wrong because this very simple.  Here is the basic idea:

Partition and format your new drive
Boot to single user mode
Unmount /home if needed
Move /home to /home.old
Add new drive to fstab as /home
Reboot to multiuser level
Done

He might have a bit of a problem after rebooting since his new home directory will be empty.  He'll end up with a default desktop.

Before the "reboot to multiuser" step I'd include:

```

cd /home.old
rsync -av . /home

```

to migrate the contents of the old home directories to the new drive.

---

