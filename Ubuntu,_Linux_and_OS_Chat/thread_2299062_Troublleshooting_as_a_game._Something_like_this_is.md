---
title: "Troublleshooting as a game. Something like this is needed"
date: 2015-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2015-10-15
Please read this bog post

[http://popey.com/blog/2015/10/11/troubleshooting-as-a-choose-your-own-adventure/](http://popey.com/blog/2015/10/11/troubleshooting-as-a-choose-your-own-adventure/)

I would like this thread to be a source of information for Alan Pope. Please supply what you know on these subjects:

1) How an upgrade can fail.
2) How a failure can be fixed.
3) What to do to prevent a broken upgrade in the first place and how to do it.

I will ask Alan Pope to check this thread from time to time to find useful information for this project.

Regards.

---

### Post by TheFu on 2015-10-15
If the current system is broken, upgrading won't fix it.  Don't do an upgrade on a system that is broke in any way. Fix it first.

Always - ALWAYS - make a backup of everything you don't want to lose before starting any upgrade.  I'm always amazed at the people with $1200 computers, who can't be bothered to have a $50 external USB drive dedicated for backups.

---

### Post by oldfred on 2015-10-15
System does not boot, often grub does not install or install correctly. And now with Boot-Repair I see many are able just to use it to fix grub issues. And it advanced repair of a total uninstall/reinstall of grub fixes other issues. It also can run a fsck which solves some corruption issues. Users need to know not to do a hard power off unless nothing else works. REISUB needs to be taught.

We filed bug reports (back with 10.04) on grub or installer putting grub into a NTFS partition, it never is correct. I still am linking users to testdisk and having them repair NTFS with grub in the partition boot sector.

While instructions on full disk install are better, users still do not fully understand that a c: drive in Windows is really a partition. Definitions or more clarity. 

As TheFu mentions, backups are essential, but many users do not do them. They need to be emphasized before user does any install.

Users should really have current version repair CD/DVD or flash drive for every system installed. Even if they upgrade Ubuntu in place they still should down loader live installer as emergency boot or repair drive. And if Windows make the Windows repair flash drive.

---

