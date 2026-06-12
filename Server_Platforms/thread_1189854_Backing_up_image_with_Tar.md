---
title: "Backing up image with Tar"
date: 2009-06-17
forum: Server Platforms
---

### Post by happyhacker on 2009-06-17
I have now done a backup using by doing this:

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/office/backups --exclude=/backup.tgz /

I've excluded my office directory because that is where I store networked windows backups and the fact that this is an hdb mount point for the servers 2nd drive which I assume, if I tried to restore by untarring would give problems.

Comment welcome if I'm not thinking correctly there?

Has a new method arisen since the original post? I use webmin and this has a tar command but assume it is something different.

---

### Post by grantemsley on 2009-06-17
I'm assuming you the move the backup.tgz somewhere else for safekeeping.

This is pretty much what I do to backup my server as well.  I wrote a script with decent error checking to backup everything, mount a remote smb share and copy it over. 

A couple things I will note:
- You'll want to exclude /dev as well.  It's an automatically generated tmpfs, and restoring /dev will prevent it from mounting properly - probably causing the system not to boot
- Same should go for /var/run, /var/lock and anything else that is mounted as tmpfs
- Make sure you have a way to partition a new drive and install your bootloader.  The ubuntu install CD can do this, or any other linux based live cd.  Then just extract the tgz file

---

### Post by wirelessmonkey on 2009-06-17
You'll want to change --exclude=/backup.tgz to --exclude=./backup.tgz

---

### Post by happyhacker on 2009-06-18
Some useful feedback there, thanks. It raises some queries though before I try with a new drive in hda which I will need to format, etc.

1. Wirelessmonkey -[COLOR="Blue"]"You'll want to change --exclude=/backup.tgz to --exclude=./backup.tgz"[/COLOR]. Wjy the dot? Does this mean I need to do this again?

2. Grantemsley - [COLOR="Blue"]I'm assuming you the move the backup.tgz somewhere else for safekeeping.[/COLOR]. Yes I plan to manually copy it to a USB hard drive for offsite storage. Although I do bring a laptop along when I visit so I could just zap it over there.

[COLOR="Blue"]- You'll want to exclude /dev as well. It's an automatically generated tmpfs, and restoring /dev will prevent it from mounting properly - probably causing the system not to boot. Same should go for /var/run, /var/lock and anything else that is mounted as tmpfs[/COLOR] Are you saying there is volatile (RAM?) system configuration that get's lost in the backup? Where can I learn about this Linux behaviour?

[COLOR="Blue"]- Make sure you have a way to partition a new drive and install your bootloader. The ubuntu install CD can do this, or any other linux based live cd.[/COLOR] So, I put in the new drive, put in the Live server CD and switch on. As I only have one partition which is likey to be larger than the old one will this stop the untar or confuse the system in some way?

Does the CD provide the means to do the format and install bootloader?

Should I make sure I use ext3 as in the old drive?

[COLOR="Blue"] Then just extract the tgz file.[/COLOR] Now, at the end of the extraction will I be able to just type in the 192. address on my network laptop and see all my applications (I configure IE to auto logon to Webmin (:10000), PHPmyAdmin and others)? Or perhaps I need to soft reboot the server?

---

### Post by grantemsley on 2009-06-18
/dev doesn't store any configuration, that's all in /etc.  /dev has all the devices in your computer - it generates them automatically when it loads all the device drivers.  It is stored in RAM, but will automatically get recreated when the system starts.  /var/run and /var/lock are used by running processes, and anything in there should get deleted when a program exits, so they aren't stored on disk either.  They would be useless after a reboot.  The files there are used for example to check if another copy of the program is already running.

If you are replacing the hard drive, the general procedure is:
- Install the new drive
- Boot from Live CD
- Partition the new drive with / and swap partitions.  It won't matter if they are larger than before.  You can use "cfdisk /dev/sda" from the command line to do this

- Mount /dev/sda1 
- Mount whereever the tgz file is (via samba which you will have to install on the live os or a USB drive or whatever is most convenient)
- Extract the tgz file
- Install grub with "grub-install /dev/sda"
- Reboot to get out of the live os and into your restored os

---

### Post by wirelessmonkey on 2009-06-18
As for mine, ./ refers to the current directory, which is where the backup.tgz is stored, as opposed to /backup.tgz, which refers to a file directly under / (root), which is not where your backup.tgz is being created.

---

### Post by happyhacker on 2009-07-27
Regarding SAMBA, will this and all my users be restored or is there likely be work to reinstate them?

I remove the backup file to a usb hard drive. I am assuming I can mount this (or better have it plugged in when I boot the live OS) with the live OS?

---

