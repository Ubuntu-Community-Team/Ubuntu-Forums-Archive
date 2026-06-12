---
title: "Linux command line tool to copy files over ssh"
date: 2009-08-01
forum: Server Platforms
---

### Post by mytechguru on 2009-08-01
Hi,
    Present all my site are running at VPS server. i am planing to move all those 2 shared hosting. 

Anyway can me help me @ Server 2 Server copy files.

---

### Post by npallett on 2009-08-01
> **mytechguru said:**
> Hi,
    Present all my site are running at VPS server. i am planing to move all those 2 shared hosting. 

Anyway can me help me @ Server 2 Server copy files.

Have you tried using the "scp" command ?

It is part of the openssh-client package, so if you have ssh , you have the scp command.

Here is a simple example that copies a file called file.txt from your current directory to the home directory of a user called mytechguru on the remote host called mytechhost:

scp file.txt mytechguru@mytechhost:~/.

When your are asked for a paasword, enter your ssh password.

Hope this helps.

---

### Post by MrWES on 2009-08-01
> **mytechguru said:**
> Hi,
    Present all my site are running at VPS server. i am planing to move all those 2 shared hosting. 

Anyway can me help me @ Server 2 Server copy files.

scp -r /pathtofolder/ name@host:/targethetfolder/

---

