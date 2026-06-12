---
title: "Full system backup question."
date: 2011-02-26
forum: Server Platforms
---

### Post by Coder68 on 2011-02-26
Ubuntu 10.04 Server. x86_64 - (64bit) with 8 gigs of RAM.
/ is RAID 1

I have been looking around at just what files I should be backing up to be able to do a full restore of my system.  These are the two variations of what seems to be the rule:

[PHP]--exclude=/proc --exclude=/lost+found --exclude=*/backup.tgz --exclude=/mnt --exclude=/dev --exclude=/sys / /boot/ 
--exclude=/proc --exclude=/lost+found --exclude=*/backup.tgz --exclude=/mnt --exclude=/dev --exclude=/sys /
[/PHP]Questions:

1.  /boot is in the root folder, so why do I need to add that? (First line)
2. If I were to wipe my drive, and reinstall Ubuntu and then restore this tape, would my system be exactly the same as before I wiped the drive? I know I would have to create at least some of the excluded folders. (Not exactly sure which ones though.)
3. Do I need to recreate /dev?


I have modified the basic Ubuntu [help]("https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html#backup-shellscript") script to backup to tape.

[PHP]#!/bin/bash
####################################
# Backup to tape drive script.
#
####################################

# What to backup. 
# backup_files="/home /var/spool/mail /etc /root /boot /opt"
# I commented out line 8 to test full backup by adding line 11

backup_files="--exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/dev /"

# Where to backup to.
dest="/dev/st0"

# Print start status message.
echo "Backing up $backup_files to $dest"
date
echo

# Make sure the tape is rewound.
mt -f $dest rewind

# Backup the files using tar.
tar cvzf $dest $backup_files

# Rewind and eject the tape.
mt -f $dest rewoffl

# Print end status message.
echo
echo "Backup finished"
date[/PHP]And am looking at modifying this [script]("http://ubuntuforums.org/showthread.php?t=35087&page=101") to backup to tape:

[PHP]#!/bin/bash
S1='b'
S2='y'
echo "Please enter b for backup or r for restore:"
read action

if [ $action = $S1 ]; then 
    
    echo "These Directories will be excluded:"
    echo -e "\033[1m\033[32m /proc /lost+found */backup.tgz /mnt /sys /dev"
    echo -e "\033[0m"
    echo "To change these values edit this shell"
    echo "continue (y/n):"
        
    read action
    if [ $action = $S2 ]; then 
        echo "Backing up PC ~ timestamp " ;date
        tar cpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=*/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/dev /
    fi
else
    echo -e "\033[1m\033[31mWARNING: this will overwrite every single file on your partition with the one in the archive!"    
    echo -e "\033[0m"    
    echo "Please enter name and location of the archive to restore:"        
    read fileName
    echo "You are about to restore $fileName do you want to continue?(y/n)"
    read action
    echo -e "\033[1m\033[47mJust sit back and watch the fireworks.This might take a while. When it is done, you have a fully restored Ubuntu system!"
    sleep 5
    echo "start"
    if [ $action = $S2 ]; then 
        tar xvpfz $fileName -C /
        echo "Creating excluded directories"    
        #Just to make sure that all excluded directories are re-created
        mkdir /proc
        mkdir /lost+found
        mkdir /mnt
        mkdir /mnt/nas1
        mkdir /mnt/r5
        mkdir/usb1
        mkdir /sys
        
    fi    
fi
echo -e "\033[0m"[/PHP]I have added a few of my mount points already. 

4. Is there anything missing from either script? If so what?
5. What would you change and why?

Thanks,

C68

---

### Post by koenn on 2011-02-27
you're doing fine

best way to test a backup is : make a backup, then try to do a restore (on a spare machine, a virtual machine, or in a directory somewhere. Then you'll know what, if anytrhing,  needs fixing

---

### Post by Coder68 on 2011-02-28
OK, but what about some of my questions?

I am trying to better understand what it is I am doing so I can do this correctly. 

Thanks,

C68

---

### Post by psusi on 2011-02-28
> **Coder68 said:**
> 1.  /boot is in the root folder, so why do I need to add that? (First line)
2. If I were to wipe my drive, and reinstall Ubuntu and then restore this tape, would my system be exactly the same as before I wiped the drive? I know I would have to create at least some of the excluded folders. (Not exactly sure which ones though.)
3. Do I need to recreate /dev?


You don't need to explicitly add /boot, since as you noticed, it is in / which you are already backing up.  You also do not need to reinstall Ubuntu to restore, you can just format the disk and restore the backup all from the LiveCD.

Also rather than explicitly --exclude everything, it is easier to use --one-file-system.  Since /proc, /dev/, /sys, and anything you have mounted in /media are all separate filesystems, this one switch will take care of excluding them.  If you have say, /home, on a separate partition, that will be excluded too, so you will want to back that up separately.

---

### Post by Coder68 on 2011-03-03
Cool, I will keep that in mind. 

So this backup, is basically an "image" of my system other then the formatting of the drive?

I am not sure how I would restore this to a VM, do you have any suggestions?  I have ESXi with an ISCSI target and Virtualbox on my laptop. 

Thanks,

C68

---

### Post by psusi on 2011-03-03
No, it is an archive, not an image, similar to a zip file in Windows.

---

### Post by bsntech on 2011-03-03
You might also look at a solution called fsarchiver.  It works with ext4 partitions - unlike partimage that doesn't work with ext4.

In my circumstance, I have two drives in each of my servers.  When I want to do a backup, I'll go into the /boot/grub/grub.cfg and change the default boot to the number 4.  Then I reboot and it starts in the "backup drive" where I've created a quick script that esentially calls the fsarchiver program and makes an all-inclusive ".fsa" file.  I've worked it in the script to then change the /boot/grub/grub.cfg file back to the default boot location of 0, reboot, and the server is back up.

FSArchiver is also apparently supposed to work when doing in-place backups like what you do as well.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/")

---

### Post by Coder68 on 2011-03-03
I realize it is not an image, but it sounds like it is a lot like one.  Just format your drive and restore your backup to get your system back. Sounds a lot like how an image works.  That is what I was asking. Is it EVERYTHING you need to restore the system?

I will check into FSArchiver.

As for my VM test restore, I am guessing that I can boot the VM to the Ubuntu boot disk, format and then do the restore.  Does this sound right?

Thanks,

C68

---

### Post by psusi on 2011-03-03
> **Coder68 said:**
> I realize it is not an image, but it sounds like it is a lot like one.  Just format your drive and restore your backup to get your system back. Sounds a lot like how an image works.  That is what I was asking. Is it EVERYTHING you need to restore the system?

With an image you don't format the filesystem first; the image IS the filesystem.  It is put back EXACTLY as it was.  With tar, you just put the same files on a new filesystem.  After that you still need to reinstall the boot loader for the system to boot.

---

### Post by Coder68 on 2011-03-03
OK. That was what I needed to know, the restore the boot sector  part that is.

I have been making images of systems for many many years (Mid to late 90's), so I do know how to use them and understand them.  But when someone says you just format and restore the system, no reinstall needed, it made it sound like it was a two step process and almost like an image. A copy of everything to restore the system without a reinstall. (Minus the format part of course.) It sounds like it is three step process.  Format, restore, reinstall the boot loader. 

I will need to figure out how to restore the boot loader. 

C68

---

### Post by aeiah on 2011-03-04
yea it behaves very similarly to an image, except an image has filesystem information and partition information as well as all the data. the archive of your entire system just has all the files.

if you do want to image the whole thing you could look at clonezilla, but the advantage rsync has is that you can incrementally make these system backups. i prefer to make clonezilla images after large system changes (ie, after installing everything for the first time) and incremental rsync backups of the important stuff (/var/www etc) on a regular basis

---

### Post by psusi on 2011-03-04
> **Coder68 said:**
> 
I have been making images of systems for many many years (Mid to late 90's), so I do know how to use them and understand them.  But when someone says you just format and restore the system, no reinstall needed, it made it sound like it was a two step process and almost like an image.

Again, restoring an image is only a one step process; you don't format first.

> **Coder68 said:**
> I will need to figure out how to restore the boot loader. 


```
sudo grub-install --root-directory=/mnt /dev/sda
```

Assuming the disk in question is sda and you have the root filesystem on it that you have restored mounted in /mnt.

---

### Post by Coder68 on 2011-03-27
Thanks.

Sorry for the long delay.  School and work have been crazy!

I am going to try and restore my backup to a spare older machine when I have some free time. 

When that will be is a good question.

Thanks again,

C68

---

