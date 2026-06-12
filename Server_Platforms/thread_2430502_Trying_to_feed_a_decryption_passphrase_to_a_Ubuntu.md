---
title: "Trying to feed a decryption passphrase to a Ubuntu 18.04 VM during bootup"
date: 2019-11-02
forum: Server Platforms
---

### Post by Robert_Boutin on 2019-11-02
Been searching for a solution but haven't quite found it (or maybe I have and just didn't recognize it).

I have a Ubuntu 16.04 host running Virtualbox.  Inside Virtualbox I have a number of virtual servers running.  One dedicated VM (Share) is publicly accessible Nextcloud running Ubuntu Server 18.04.  Another VM (Backup) is functioning as a NAS until I can get a separate physical NAS.  I have a script in my Nextcloud server to rsync the data and database files daily to Backup while the server is running.  Then once per month, I use the following script in my host to shut down Share, rsync the entire contents of the VBox folder to Backup, then restart Share.

#!/bin/sh
#
#Backup 3-Share to /mnt/raid2tb/livevmbackups/
#
sudo su - username -c "VBoxManage controlvm 3-Share acpipowerbutton"
sudo su - root -c "rsync -avz /mnt/raidssd/livevms/3-Share/ /mnt/raid2tb/livevmbackups/3-Share/"
sudo su - username -c "VBoxManage startvm 3-Share"

This seems to have worked well to keep Share backed up.  However, for security purposes, I rebuilt Share on a new Ubuntu 18.04 virtual server (using my backups, so +1) and enabled full disk encryption to require a passphrase during bootup.  The problem I have is that the boot process stalls unless I am sitting at my keyboard to enter the passphrase at 1:00 a.m. when Share reboots.  If I don't know Share shut down for its monthly backup, it remains offline.

So my question is this - Is there a way to automatically feed my decryption passphrase to Share (or have it call somewhere for the passphrase) such that the monthly reboot doesn't stall?  And what are the security considerations of such methods?  All inbound SSH traffic from outside my network is blocked so my main concern is if someone walks off with my host machine (which is also the main reason I need to get my backups off my host and onto a NAS).

Thanks as always!

---

### Post by TheFu on 2019-11-02
I don't know anything about 18.04.

I think LUKS can read a passphrase/key from a USB storage device.  Google found many articles on how to do it.
Don't forget to pull the usb-key when it isn't needed to boot/backups.

I use a Yubikey for part of my passphrase to unlock my FDE storage. This will not work for your needs, since it definitely requires a human to activate the Yubikey.

BTW, is there a specific reason not to just have a script in root's crontab? 
```
/usr/bin/rsync -avz /mnt/raidssd/livevms/3-Share/ /mnt/raid2tb/livevmbackups/3-Share/
```

**sudo su -** ... is the same as **sudo -i some-great-command**, if that is really necessary.  Normally it is not.

---

### Post by LHammonds on 2019-11-03
If you are requiring a passphrase during bootup, then it sounds like you want to ensure the data is safe at rest (e.g. someone steals the hardware).

So if you have a USB stick plugged in it while you are not there or some other automated way of bypassing it, then why are you using the option in the 1st place?

And if you continue wanting this setup, then do NOT schedule it to reboot when you are not there.  If you are awake @ 7am, schedule the reboot around that time.  I would even go so far as to setup the reboot process to send you an email or txt message to your phone saying the server is about to reboot.

LHammonds

---

### Post by Robert_Boutin on 2019-11-03
Thanks. I really wouldn’t want to accidentally leave a USB stick with the passphrase in my machine but you did make me wonder... when I put together my NAS it will be physically separated but on the same network for backups. If my encrypted disk can fetch the passphrase off a USB stick, could it also fetch it from the NAS? At least that way if someone walks off with my host machine (and not also with the NAS), my Share disk is still secure. 

And yeah, I’m no coding expert. I searched for a method that would work to do the shutdown/rsync/restart and what I wrote below was what eventually worked. Each server has a similar backup script which is called from crontab. At some point perhaps I’ll go back and clean things up as I learn how but it seems I always have another priority (like this one), so when something isn’t broke I tend not to fix it.

---

### Post by Robert_Boutin on 2019-11-03
LHammonds, thanks, an email alert actually makes the most sense for me. Simple is always better.

---

