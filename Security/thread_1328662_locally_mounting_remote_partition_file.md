---
title: "locally mounting remote partition file"
date: 2009-11-16
forum: Security
---

### Post by StefanX on 2009-11-16
Hi!
I use an encrypted partition (dm-crypt) for my home directory. Currently I am evaluating an appropriate and secure strategy for a remote backup. Therefore I could rsync my encrypted partition to a remote backup server. This works but has the drawback that the partition needs to be unmounted while executing backup. To avoid this drawback I had the following idea:

Mount the backup system (with SSHFS because it is available via SSH only) and use a partition container file on the remote system which I mount **locally**. Then I could rsync between my local data and the remote partition while both beeing mounted.

I tried to set up the system the following way:
1. I mounted the remote system and created a container file to act as my backup partition container.
2. Because it is a file and not a block device AFAIK I need to use a loop device before mounting. Therefore I execute "losetup /dev/loop3 /remote/container.img". Unfortunately it does not work out and I retrieve "Permission denied". I tried with two different remote systems (all mounted via SSH) also with root user who definitely has sufficient permissions on the remote system.

I was told that SSH allows file oriented transfer only and therefore does not allow the transfer of specific bytes of a file (which might be a reason for this problem) but this is not conform with my experience of SSH.

Any idea what might be the cause of the problem and how to set up the described scenario?

---

### Post by StefanX on 2009-11-17
I found the problem. The remote directory was mounted via sshfs for current user only while I executed losetup as root who had no permissions to access the directory. Both either activating user_allow_other in /etc/fuse.conf or mounting the remote directory as root solve the problem.

---

### Post by BkkBonanza on 2010-01-06
*You really should have started a new thread for this*...

There are 3 ways that come to mind for doing this. 
Samba - which works well with other OSes like Windows as well as linux.
NFS - which is mostly a Linux solution
SSHFS - as above user was using, is a way to mount file systems over SSH when that is the only option you have for secure remote access.

Probably the simplest method is using Samba, which is available from the gui/desktop. You just enable file sharing on the system with files you want to access and then other computers on the network can get to them. I believe by default the Samba file sharing can be turned on in menu item System, Preferences, Startup Applciations. Look for File sharing there and enable it.

You can then use Nautilus to share folders, and other users on the network can use Nautilus to mount those folders on their system. This method is the closest to Windows gui style file sharing.

---

### Post by HermanAB on 2010-01-06
Rsync over SSH is probably what you need.

rsync -e ssh yadda yadda

---

