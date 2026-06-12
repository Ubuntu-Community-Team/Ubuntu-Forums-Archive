---
title: "[SOLVED] Encrypt entire drive after install?"
date: 2008-10-11
forum: Security
---

### Post by davethewave83 on 2008-10-11
Hello! I only recently became aware of the option to use the alternate disk to enable encrypted LVM and was wondering if there is a way to do this post-install? I have all my settings up in a comfortable way, programs installed.. data and files that I would rather keep. I know I could always do a full system backup, send the backup through the network format/encrypt-reinstall then restore the backup but there are factors I do not understand with backups, which folders to backup which to leave alone etc. If there is a way to enable LVM encryption without re-installation please let me know how :) 
Thanks!

---

### Post by Dave_Connor on 2008-10-11
You can encrypt your entire drive after install but it quite a pain to setup. There is Encfs and Fuse kernel driver where you can install and use a directory to store your data in. Or for single file use with gnupg.

---

### Post by tact on 2008-10-11
Seconding what Dave_Connor wrote.   It can be done. Just like rowing a boat across the atlantic can be done.  :)   But it would require you to really KNOW what you are doing, take considerable planning, require adequate supply of spare media for backing up (external HDDs?) and any mistake would be disasterous.

Changing a standard partitioning scheme to LVM will mean destroying existing partitions.  Even if you were already using LVM (non encrypted) partitioning when you encrypt a partition it also destroys all data.  A lot of hoops to jump thru.

Even tho it will involve downloading some of your software again perhaps it will be better to just:
- back up the entire HDD to non encrypted external storage (or if thats too much back up at lease /home)
- completely reinstall the original HDD using alternate installer
- copy back the /home from external storage (only restore /home to start with)
- reinstall all your apps etc.
- if needed you can access the external backup to grab other config files as needed (e.g. smb.conf or xorg.conf if they were customised)

The result of this will be:
-  need to download/reinstall applications/fonts/codecs etc that are not part of standard install.
-  your won't have to reconfigure all your applications again as nearly all store their configurations in hidden files/folders inside /home which you will have backed up and restored.
-  you then get the benefits of a fully integrated "whole" disk encryption, i.e. need only enter the disk passphrase once at boot time as opposed to different passwords for different partitions/folders.  
-  some setting up will be needed (e.g. if you customised xorg.conf or smb.conf etc these would be lost if you only backed up /home)  If you backed up the entire HDD then you can just pull back specific config files as needed.

---

### Post by davethewave83 on 2008-10-11
Thank you both for the great replies and support :) I know now what I must do. (backup-reinstall)

---

### Post by hyper_ch on 2008-10-12
in addition I have some reserveration towards LVM and encryption... in the past there have been issues on this...

---

