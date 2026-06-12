---
title: "[Ubuntu 18.04 LTS Server] Unable to use zerofree in VirtualBox Guest"
date: 2018-08-23
forum: Virtualisation
---

### Post by cyplex on 2018-08-23
I have set up an Ubuntu 18.04 Server in VirtualBox. I've installed zerofree in it and want to clean things before I do my compressing and backup.

Normally, here is how it worked (in the Ubuntu 14.04 LTS server virtual machines I have):

1. Boot into recovery mode.
2. Log in
3. mount -n -o remount,ro -t ext4 /dev/sda1 /
4. zerofree -v /dev/sda1

Now, I get as far as step 3 in the 18.04 box and I get a notice that the mount point is busy. 

I've tried to use "service [service-name] stop" to stop everything (rsyslog, apache2, proftpd, fail2ban, exim4, mysql). Those stopped but it still said the mount point is busy.

I've turned off and removed the swap file and changed swappiness to 0 (keep in mind in all this I did reboot to be sure changes too effect). Still getting mount point busy.

I've tried to 'killall dhclient' (one old server I had to use 'killall dhclient3') Tried both and was told those services weren't installed/found.

I've tried to do 'service network-manager stop' and was told that the service wasn't installed/found.

I've tried to do 'ps aux | grep root' but I didn't find anything (I'll post the output below).

I did do a mount | grep "sd" and found that / is mounted on /dev/sda2 so I did the 'mount -n -o remount,ro -t ext4 /dev/sda2 /' and mount point is busy (same if I do mount -n -o remount,ro /dev/sda2 /". If I try zerofree it says that the device is mounted rw and won't run.

I went into fstab (had to in order to comment out the swap file part to turn off swap) and found that the only other entry is the one for / but it starts with UUID= and a long number.

I've even tried to go into single-user mode. But no matter what I tried, the mount point is busy.

At this point, I'm stumped. Has anyone got this to work in an 18.04 server virtual machine?

---

### Post by &amp;KyT$0P# on 2018-08-23
Why not just do this instead of using zerofree? -

```
cat /dev/zero > somefile
```
Repeat as needed, or let it continue running, until the disk is almost full; then delete the file(s) created.

---

### Post by cyplex on 2018-08-23
How do I know if I even "need" to 'repeat as needed'? How do I know how long it'll take (no progress indicator)? How do I know it got all the unused space? This is why I rather use zerofree.

---

### Post by cyplex on 2018-08-23
@hologen2 I do want to thank you though because your response led me to an alternative:

$ sudo apt-get install pv
$ dd if=/dev/zero | pv | of=zero.file; sync; rm zero.file

The problem with both yours and my option above is that it takes too long. Zerofree does things much faster (and I don't have a lot of time to spend on things when I do these backups).

---

### Post by cyplex on 2018-08-23
Ok, thank you to hologen2 as the post they gave provided inspiration to me in the right direction. I've resolved the issue.

1. Ensure you have a root password:

$ sudo passwd -u root
$ sudo passwd root
Type in a password you can remember

$ sudo shutdown -r now
When you see the VirtualBox logo screen, hold down the [RIGHT SHIFT] key until you see the grub screen.
Select the advanced options and then recovery mode.
At the next screen select to drop to root console.
At the # prompt enter the root password you set earlier.

[LEFT][COLOR=#990099][FONT=Liberation Mono]# mount | grep "sda"[/FONT][/COLOR]
[FONT=Arial]Takenote of the sda # (ie. sda1, sda2, etc.) that is for the / or rootdirectory. We'll assume [FONT=Liberation Mono]/dev/sda2 [/FONT]for this example.[/FONT]
[COLOR=#990099][FONT=Liberation Mono]
# echo "u" > /proc/sysrq-trigger
[/FONT][/COLOR][COLOR=#990099][FONT=Liberation Mono]# mount /dev/mapper / -o remount,ro
[/FONT][/COLOR][COLOR=#990099][FONT=Liberation Mono]# zerofree -v /dev/sda2[/FONT][/COLOR][COLOR=#990099][FONT=Liberation Mono]
[/FONT][/COLOR][COLOR=#990099][FONT=Liberation Mono]# shutdown -r now

[/FONT][/COLOR][FONT=Liberation Mono][FONT=verdana]**NOTE:** You don't need to remount as rw after using zerofree because once you reboot fstab will mount the drive rw anyway.[/FONT][/FONT][COLOR=#990099][FONT=Liberation Mono]

[/FONT][/COLOR][/LEFT]
Now let it boot normally.

If you want to disable your root password (I am one of those that does this for security reasons):

$ sudo passwd -l root

Now I usually just go and shut down the system and compress the drive:

$ sudo shutdown -hP now

From there I use VBoxManage clonehd [machine].vmdk [machine]-disk1.vmdk to clone it and that compresses it further.

I hope this post helps those who have also had issues with getting zerofree working in Ubuntu 18.04LTS in Virtualbox.

---

