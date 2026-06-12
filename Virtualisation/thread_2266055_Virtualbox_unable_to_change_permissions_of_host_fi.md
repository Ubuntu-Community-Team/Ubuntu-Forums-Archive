---
title: "Virtualbox: unable to change permissions of host files"
date: 2015-02-19
forum: Virtualisation
---

### Post by resonator2 on 2015-02-19
I've installed Virtualbox 4.3.20 then Ubuntu 14.04 on a PC running Win7, following [these instructions]("http://www.wikihow.com/Install-Ubuntu-on-VirtualBox"), including the guest additions. I created a shared folder, added myself to the vboxsf group, and can see files on my PC via Ubuntu. However, now matter which variant I try of the many solutions posted online, I'm not able to change the permissions, group or owner of these files, or to replace them inline.

Here's what I observe:
[LIST=1]
[*]The files in the shared folder belong to root (group=vboxsf); chmod and sudo chmod don't produce an error but don't have any impact.
[*]Trying to replace a file inline (perl -i.bak) produces "Can't rename file to file.bak: Text file busy, skipping file.".
[*]I can create files and move existing files. I can also delete and copy files, but the copies inherit the permissions of the originals. Yes, I do see the obvious workaround.
[/LIST]

Here's the setup in Virtualbox. 

[LIST=1|INDENT=1]
[*]Storage
[LIST=1]
[*]Controller: IDE
[LIST=1]
[*]VBoxGuestAdditions.iso (IDE Primary Master, no live CD)
[*]Empty (IDE Secondary Master, no live CD)
[/LIST]

[*]Controller: SATA
[LIST=1]
[*]ubuntu-14.vhd, 8 GB virtual, 6 GB actual, dynamically allocated
[/LIST]
[/LIST]

[*]Shared Folders
[LIST=1]
[*]Machine folders
[LIST=1]
[*]Name: PC
[*]Path: c:\Users\first.last
[*]Automount: yes
[*]Access: Full
[*]Read-only: no
[/LIST]
[/LIST]
[/LIST]

Here's what I've tried so far:
[LIST=1]
[*]Edit /etc/fstab and add "PC /media/sf_PC vboxsf rw,umask=002,gid=1000,uid=1000,auto 0 0"
[LIST=1]
[*]tried this with and without automount above, and with remount as an option to override automount
[*]tried smbfs instead of vboxsf
[*]tried with or without the auto, rw and gid options
[*]_Outcome_: I see the drive flashing in the docker at every change, but nothing happens to the file permissions. In addition, whenever I reboot after any of these additions to fstab, I get "An error occurred while mounting /media/sf_PC".
[/LIST]

[*]Edit /etc/mtab.
[LIST=1]
[*]Outcome: this does nothing. Every time I reboot, mtab is overwritten.
[/LIST]

[*]Edit /etc/rc.local and add "sudo mount -t vboxsf -o rw,umask=002,uid=1000,gid=1000 PC /media/sf_PC". Remove automount option from VM.
[LIST=1]
[*]_Outcome_: this makes me the owner and group of files, but I still can't change permissions or edit files in place. Setting gid to 999 makes the group vboxsf but the outcome is the same.
[/LIST]

[*]Chown -R of /mnt/sf_PC, either before or after mounting.
[LIST=1]
[*]_Outcome_: this does not accomplish anything.
[/LIST]
[/LIST]

I don't think I'm trying to do anything unusual. Thanks.

---

### Post by ajgreeny on 2015-02-19
I'm no great expert in VBox, but surely if your host is Win7 you will never get Linux file permissions to stick on those files that reside in your host; Windows filesystems simply do not understand permissions as the Linux filesystems do, even when being viewed in a folder in your guest OS.

I don't think you need to edit fstab either in order to get the shared folder to be mounted or available; you just need to tick the box for **Auto-mount** when you set up that shared folder pathway.

---

