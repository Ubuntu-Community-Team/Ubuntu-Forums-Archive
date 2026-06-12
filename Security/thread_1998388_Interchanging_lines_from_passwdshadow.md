---
title: "Interchanging lines from passwd/shadow"
date: 2012-06-06
forum: Security
---

### Post by nfitzkee on 2012-06-06
Hello,

I'm configuring a simple linux network for my research lab.  In the final configuration, the server hosts the home directories, and users should be able to log in to workstations and access their files.  There are currently only three workstations, and I don't anticipate needing much more than this.  We will probably only ever service ~10 total users.

The server is running 64-bit Ubuntu 12.04 (on bare metal), and the workstations are running 32-bit Ubuntu 12.04.  The workstations are virtualbox guest systems, running on Windows 7 hosts.  

As far as networking, I have the firewalls configured like I want them, but for the sake of simplicity, assume that all firewalls are off in the scenario below.  I don't think my problem has to do with virtualbox, but the guest systems are operating behind the virtualbox NAT.  (NFS is mostly working; see below.)

Because the setup is so small, and because we're on an insecure university network, I don't want to use NIS.  Instead, I have copied the appropriate lines from shadow/passwd from my server to the workstation machines.  In other words, if my server has a user 'hawa', with the following lines in the passwd/shadow files:

(from passwd) hawa:x:1002:100:Hawa,,,:/home/hawa:/bin/bash
(from shadow) hawa:(password hash):15313:0:99999:7:::

I would paste those lines into the appropriate files on the workstation (using vipw).  Then, the home directory would be shared via nfs.  I have made sure that there are no UID/GID conflicts.

In principle this should work, and I've used it in the past on older RedHat systems, but it's not working for Ubuntu.  Attempting to login to a workstation as a duplicated user does not work (the password is not accepted).  Only when I change the password of the account on the workstation can that user can log in.  However, after changing the password, all of the other users have been removed from shadow (they still exist in passwd).  Odd.

One other thing: While the NFS shares are working, the user and groups are all listed as nobody/nogroup even when records exist in the workstation's passwd file.  For example, if I change the password on the hawa account, I can log in and access my home directory.  I can even create/delete files in directories that I own, but the user permissions on the workstation all appear as nobody:nogroup.  Here is a copy of my exports (server) and fstab (workstation):

(exports): /home   (ip address mask)(rw,insecure,sync,no_subtree_check)
(fstab): (ip address):/home /home nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

I apologize if some of this is basic; I've used linux for a long time, but it's been a while since I've had to administer a network,and a lot has changed since then.

Thanks,
Nick

---

### Post by nfitzkee on 2012-06-06
Update: I was able to fix the NFS issue by disabling NFS v4.  The usernames appear as expected now, although the password file issue remains unresolved.

---

### Post by Derek Karpinski on 2012-06-08
I was able to fix a somewhat similar issue [http://ubuntuforums.org/showthread.php?t=1969381](http://ubuntuforums.org/showthread.php?t=1969381) by using pwck.

There are also a few more utilities that deal with this stuff


man pwck & man pwconv will show some more.

Hope this helps.

---

