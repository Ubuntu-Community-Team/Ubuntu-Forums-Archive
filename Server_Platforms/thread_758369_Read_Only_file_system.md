---
title: "Read Only file system"
date: 2008-04-17
forum: Server Platforms
---

### Post by ahardo on 2008-04-17
Hi All
i have a problem in my ubuntu server, all of my system file is read only, i cant modify all file, it happen suddenly. i dont know why. can anyone help me ? 

regards

arya

---

### Post by alan34 on 2008-04-18
Have look at the commands chmod and chown. In a terminal do

man chmod

man chown

for example to give **everybody** read permissions to a directory, its
sub-directories and all the files go

sudo chmod -R ugo+w /whateverpath/whateverdirectory

for execute

sudo chmod -R ugo+x /whateverpath/whateverdirectory

let you guess what read is :)

Hope that helps worth reading up on. I would be careful about altering system files, I assume it is only the files under /home you want to alter.

---

### Post by MJN on 2008-04-18
It's probably because your filesystem has suffered a failure - it is configured by default (in /etc/fstab) to remount as read-only in such cases in order to minimise the risk of data loss.

Unfortunately unless you mount /var/log on a different partition then you will most likely not see any evidence of what went wrong (as being read-only it obviously cannot write such info to the logs).

Given it highly undesirable to perform filesystem checks on a running system I would suggest booting with a LiveCD (e.g. the Ubuntu installer would do) and running fsck on the affected partition (this will be listed in fstab).

Mathew

---

### Post by ibutho on 2008-04-18
Try doing a filesystem check using a live cd. I recommend using the Ubuntu live cd or something like like [System Rescue CD]("http://www.sysresccd.org/").

---

