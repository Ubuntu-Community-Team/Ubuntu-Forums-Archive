---
title: "Even SUDO can't delete these files."
date: 2009-08-09
forum: Server Platforms
---

### Post by garfonzo on 2009-08-09
Here's my situation. I have two 500GB hard drives. My intention is that one was going to be available as network storage on my home LAN and the other was going to be a mirrored backup (via rsync) for the shared one. However, the backup 500 was NTFS and had some files on it. 

This was my plan of attack:
1) Mount as NTFS
2) Move data off of it
3) Unmount it
4) Format as ext3
5) remount as a backup file.

However, I forgot step 5 and, without realising this tried to to a backup with rsync. Given that the hard drive that the OS is installed on is only 20GB, the backup did not complete. (The 500GB hard drive has 250GB of data on it). 

So, now I have a folder on '/' (which was meant as the mount point) that is full but I can't delete the files! When I try:
```
sudo rm -r 500Betta/
```

(500Betta being the mount point full of files) I get the following error:
```
rm: cannot remove directory `500Betta/lost+found': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090226_0800.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090225_0800.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090227_0300.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090227_1100.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090226_1100.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090228_0300.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090302_0300.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090227_0330.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090227_0800.mpg': Read-only file system
rm: cannot remove `500Betta/2bChecked/CATV 3_20090228_0330.mpg': Read-only file system

```
They are a bunch of TV recordings.
the permissions are:
```

ls -alF 500Betta/
total 16
drwxrwxrwx 4 root root 4096 2009-08-09 09:34 ./
drwxrwxrwx 8 root root 4096 2009-08-07 15:52 ../
drwxr-xr-x 2 root root 4096 2009-08-09 09:34 2bChecked/
drwxr-xr-x 2 root root 4096 2009-08-09 00:06 lost+found/

```
but I can't change them:
```
chmod: changing permissions of `500Betta/': Read-only file system

```
So, how the heck to I remove these files so I can mount that actual drive?!

---

### Post by Narada on 2009-08-09
Please post the contents of your fstab file.
```
cat /etc/fstab
```
It may simply be an issue of the mountpoint not having read/write enabled. If you need, you can create another mountpoint in fstab specifically for this task.

---

### Post by garfonzo on 2009-08-09
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4b4cb102-e9a6-4fca-881e-b39584c6be9f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=31d94036-8446-44a7-939b-3e9801118806 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

############## ADDED - August 6, 2009 ###############

/dev/sdd1       /garfonzo/320Alpha   ext3    defaults        1       2
/dev/sdg1       /garfonzo/320Betta   ext3    defaults        1       2
/dev/sda1       /garfonzo/320Charlie ext3    defaults        1       2
/dev/sde1       /garfonzo/320Delta   ext3    defaults        1       2
/dev/sdb1       /garfonzo/500Alpha   ext3    defaults        1       2
/dev/sdf1       /garfonzo/500Betta   ntfs    defaults        1       2      1       2

```

I realise that the last disk is mounted via ntfs and should be ext3. However, this doesn't matter since after formatting the disk I never issued:
```
mount -a
```
to remount it all again.

It's the very last disk in question

---

### Post by garfonzo on 2009-08-09
> **Narada said:**
> Please post the contents of your fstab file.
```
cat /etc/fstab
```
It may simply be an issue of the mountpoint not having read/write enabled.
But I've not mounted it at all, so I've dumped files on the root filesystem in a folder I created which was intended as the mount point (which was chmod 777 to begin with).

---

### Post by Narada on 2009-08-09
> **garfonzo said:**
> ```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4b4cb102-e9a6-4fca-881e-b39584c6be9f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=31d94036-8446-44a7-939b-3e9801118806 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

############## ADDED - August 6, 2009 ###############

/dev/sdd1       /garfonzo/320Alpha   ext3    defaults        1       2
/dev/sdg1       /garfonzo/320Betta   ext3    defaults        1       2
/dev/sda1       /garfonzo/320Charlie ext3    defaults        1       2
/dev/sde1       /garfonzo/320Delta   ext3    defaults        1       2
/dev/sdb1       /garfonzo/500Alpha   ext3    defaults        1       2
/dev/sdf1       /garfonzo/500Betta   ntfs    defaults        1       2      1       2

```

I realise that the last disk is mounted via ntfs and should be ext3. However, this doesn't matter since after formatting the disk I never issued:
```
mount -a
```
to remount it all again.

It's the very last disk in question

Every time you reboot fstab will automount /dev/sdf1 due to the 'defaults' option you have assigned to it. mount -a is unneeded. (Unless you haven't rebooted since unmounting it.) 

You definitely have one bugger of a situation here. Just so I understand you correctly before continuing, we only care about getting the files off of /dev/sda1, right? /dev/sdf1 is completely irrelevant right now?

---

### Post by garfonzo on 2009-08-09
> **Narada said:**
>  You definitely have one bugger of a situation here.  You got that right!
> **Narada said:**
> Just so I understand you correctly before continuing, we only care about getting the files off of /dev/sda1

No, sda1 is actually blank. I had formatted it but never re-mounted it. It was always on the sidelines watching the show.

> **Narada said:**
> /dev/sdf1 is completely irrelevant right now?
Correct

I'm not concerned with /dev/sdf1 because it has been formatted and is waiting to be re-mounted and used as a backup disk. 

My problem is with the directory: /garfonzo/500Betta 
That directory, after issueing the command: 
```
sudo rsync -ch /500Alpha /500Betta
``` contains a bunch of files now that I can't delete. SUDO doesn't have the permissions to delete them!?!

---

### Post by garfonzo on 2009-08-09
Ok, I rebooted and now I'm thrown into "initramfs" with a console. 

Clearly, because there are files in the mount point (as outlined above) the OS is confused and dropped me into this. I've never used this before.

I think I've made my situation worse.

---

### Post by Narada on 2009-08-09
> **garfonzo said:**
> Ok, I rebooted and now I'm thrown into "initramfs" with a console. 

Clearly, because there are files in the mount point (as outlined above) the OS is confused and dropped me into this. I've never used this before.

I think I've made my situation worse.

What did you change in fstab or GRUB? Did you delete anything from any partition? Did you change which partition was designated to boot from in menu.lst? Need info! D:

---

### Post by garfonzo on 2009-08-09
> **Narada said:**
> What did you change in fstab or GRUB? Did you delete anything from any partition? Did you change which partition was designated to boot from in menu.lst? Need info! D:

Remember, I setup my fstab as outlined above. BUT, before remounting that LAST drive, I did an rsync from 500Alpha (250GB of data) to the mount point (a directory on a 20GB hard drive the OS sits on). In other words, without actually mounting the last drive, I copied stuff to the mount point. So even though the fstab file above is what I will be using (excecpt ntfs will be ext3) I hadn't yet issued "mount -a" to use it. Then I realised my mistake and found myself unable to delete the files.

To answer your questions: 
- I changed the fstab (as outlined above) so the last drive mounted is "ext3" instead of "ntfs". That's all I changed to anything.
- I didn't touch GRUB
- I had been trying to delete the last mount point with no success (hence this whole thread)
- I didn't change which partition is booted from (I don't even know how to do that)

---

### Post by garfonzo on 2009-08-09
In my attempt to fix this issue, the server is now booting into "initramfs" which I'm totally lost in. So, searching to figure out how to use initramfs, I can across[ this thread ]("http://crunchbanglinux.org/forums/topic/2572/initramfs-hang-on-boot/") in which the OP states that "I read somewhere (which I'm not sure if accurate) that ext3 switches to Read Only when there are a lot of write errors."

Is this true? It would make sense as to why I can't delete the files because they are 'read-only'. 

I'm still at a loss. I'm about to try booting off a USB flash drive, mount the root filesystem, edit the fstab to NOT mount anything for the time being, and possibly delete the unwanted files I mentioned in the original post. 
Anyone see anything flawed about my plan or have any further tips?

Worst case scenario: fresh install (crappy though)

---

### Post by Narada on 2009-08-09
I dunno what to tell you. Sorry I couldn't be of more help... this has me in as much confusion as it does you. :( Keep us updated, regardless.

---

### Post by garfonzo on 2009-08-09
> **Narada said:**
> I dunno what to tell you. Sorry I couldn't be of more help... this has me in as much confusion as it does you. :( Keep us updated, regardless.

I very much appreciate the help. These forums, and the support from the community is one of the reasons I chose Ubuntu.

So, here's the status. I followed [this guide ]("http://www.pendrivelinux.com/usb-moolux-install-from-windows/")to boot from a USB flash stick into Linux. I disconnected all of the drives except the one with the OS. I booted from the USB stick, was able to navigate to /etc/fstab and edit it so that it doesn't try to mount anything.

Then, I successfully (I think) deleted the mount point into which I accidently put files and couldn't remove them.

After that, I tried booting from the regular OS. After a LOT of I/O errors that looked like this:
```
.... ata3.00:status: {DRDY ERR}
.... ata3.00:err: {UNC}
.... ata3.00:exception Emask 0x0 SAct SErr 0x0 action 0x0
.... ata3.00:BMDMA stat 0x64
.... cmd ????

```it brought me to a 'recover shell' from which I could hit CTRL-D to reboot.
---note: I had to write that down as it flashed across the screen. The first "...." were numbers similar to: 23.45456.434 and the ???? at the end was a command that looked like a MAC address (but wasn't, just had the same HEX look to it). There were also lines about I/O buffer errors.

While that was flashing across the screen, it was checking the filesystem (with the percentage and all) but was showing LOTS of the above errors with the numbers changing.

It's like there are huge problems with the filesystem now. 

I fear my only hope is a fresh install.

Really, that isn't so bad. I just like the challenge of figuring out why problems occur, and how to fix them so I know for next time. Reinstalling is sort of the 'easy' way. But, maybe that's all I have!?

Anyone have any clue about those errors?

---

### Post by garfonzo on 2009-08-09
Another update:

I think I "fixed" it. At the recovery shell, or maintenance shell (whatever it is called) I typed:
```
fsck /dev/hda1
```
It found a bunch of errors that made no sense to me, all of which I just hit 'yes' to fix. Now it booted normally and I can log in through SSH again as if nothing happened (other than not mounting my drives).

I'm leery though. What the heck happened?! What was affected? I'm thinking that although I was able to get it back up and running, I may want to do a clean install to erase whatever may linger due to this weird excursion of disk problems.

Any thoughts?!

---

### Post by cariboo on 2009-08-09
Can you not use:

```
sudo chmod -R 777 /garfonzo/500Betta
```

to change the permissions, this should work even though the partition is formatted as ntfs.

---

### Post by garfonzo on 2009-08-09
> **cariboo907 said:**
> Can you not use:

```
sudo chmod -R 777 /garfonzo/500Betta
```

to change the permissions, this should work even though the partition is formatted as ntfs.

Thanks for the reply. I did try that, but it didn't work as it only spit back errors. At the time (when the problem first started) that mount point was only a directory. So, the physical hard drive had not yet been mounted to the muont point. Thus, I was dropping files into a normal directory, tried dumping too much, and resulted in the filesystem switching to "read-only" mode (of course, that is what I assumed happened). That was why I couldn't delete the files.

A further update: 
- I have been able to log into the server through SSH
- I checked each disc one at a time to ensure they were okay before running "mount -a"
- they all seem to be fine, so I edited /etc/fstab to look like this:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4b4cb102-e9a6-4fca-881e-b39584c6be9f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=31d94036-8446-44a7-939b-3e9801118806 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

############## ADDED - August 6, 2009 ###############

/dev/sdd1       /garfonzo/320Alpha   ext3    defaults        1       2
/dev/sdg1       /garfonzo/320Betta   ext3    defaults        1       2
/dev/sda1       /garfonzo/320Charlie ext3    defaults        1       2
/dev/sde1       /garfonzo/320Delta   ext3    defaults        1       2
/dev/sdb1       /garfonzo/500Alpha   ext3    defaults        1       2
/dev/sdf1       /garfonzo/500Betta   ext3    defaults        1       2

```
then I ran```
mount-a
``` and everything seems to be fine. 


I think I may have come out of this ok. As I noted earlier, I'm a bit leery of the OS now. I'm not sure what lingering issues I may have, but as far as I can see I'm back to where I was at 9am this morning.

Majour thanks to those who helped! Hopefully this thread will help someone else in a similar situation.

---

### Post by rhcm123 on 2009-08-12
From what i read through here, it appears your file system locked down after trying to copy too many large files. This happened to me when i tried to copy an 8 GB file to a FAT32 file system, as FAT32 only supports 4gb files. I had to run this as root (use sudo):

```
mount -o remount,rw /dev/sdc1 /media/windows

```
That command remounted /dev/sdc1 to it's mountpoint /media/windows, and made it read/writeable. Substitute your device and mount point, of course.

If you want to prevent this from happening in the future, use the nomand  command in the fstab, as in: (this is an example)
```
/dev/sdc1       /media/windows  vfat        user,noauto,exec,utf8,nomand 0       0

```

---

### Post by koenn on 2009-08-13
> **garfonzo said:**
> In my attempt to fix this issue, the server is now booting into "initramfs" which I'm totally lost in. So, searching to figure out how to use initramfs, I can across[ this thread ]("http://crunchbanglinux.org/forums/topic/2572/initramfs-hang-on-boot/") in which the OP states that "I read somewhere (which I'm not sure if accurate) that ext3 switches to Read Only when there are a lot of write errors."

Is this true? It would make sense as to why I can't delete the files because they are 'read-only'. 

It's not exactly true : it's your OS that remounts the filesystem readonly on error, as instructed by fstab :

' ....  /               ext3    relatime,**errors=remount-ro** '

but it's true that this was probably the cause of your problem, and I've seen similar things happen when writing huge amounts of files to disks of questionable quality.

---

