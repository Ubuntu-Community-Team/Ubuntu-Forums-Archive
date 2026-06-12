---
title: "Storage Program"
date: 2007-12-02
forum: Server Platforms
---

### Post by mattc908 on 2007-12-02
Hey I was wondering anyone know of any programs that check how much space you have left on your drive and what things take which so I can see whats hogging all my HDD space? So I can delete unecessay things on my server? I have an 80gig HDD in there and something is taking 40gigs of it, and only has simple things on it....

---

### Post by HermanAB on 2007-12-02
Yeah, there are little routines that can do that - just can't remember it.  Something like df and sort.  Some googling will find it for you.

---

### Post by koenn on 2007-12-02
df -h
disk used/free space 

du -h
list of files + size on disk

you'll need to  find a way to filter or sort the output of 'du'.

---

### Post by MJN on 2007-12-02
I use [KDirStat]("http://kdirstat.sourceforge.net/") on KDE - it maps out your entire drive (or whatever) graphically using squares of relative size proportional to their space usage. This enables you to easily see at a glance which files/folders are taking up the most (relative) space to enable you to optimise the freeing up of space.

[IMG]http://kdirstat.sourceforge.net/thumbnails/kdirstat-main.jpg[/IMG]

When you first run it you might think WTF?! But get clicking around and you'll soon start to get a feel for how it works.

I believe the/a Gnome equivalent is [Baobab]("http://www.marzocca.net/linux/baobab.html") although I've never used it.

Mathew

---

### Post by mattc908 on 2007-12-02
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             2.1G  1.2G  815M  59% /
varrun                379M   60K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M   84K  379M   1% /proc/bus/usb
udev                  379M   84K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm

Okay I have an 80gig Harddrive in there..... Im 99% sure when I installed I told it to use all of it. So shouldn't there be alot more room.

---

### Post by Maxtorm on 2007-12-02
It looks like you are not using the whole drive. Download the Clonezilla Live CD ([http://gpartedclonz.tuxfamily.org/download.php](http://gpartedclonz.tuxfamily.org/download.php)) and boot from it. This will allow you to change the partition size to use the whole disk.

---

### Post by mattc908 on 2007-12-04
For some reason it doesnt recognize my keyboards USB/PS2. No clue why so can it be done with another program?

---

### Post by Maxtorm on 2007-12-04
You could try other good Live CDs like Knoppix, but I imagine the problem with the keyboard detection might have an easy solution. Are there any BIOS options with respect to the USB keyboard? Try monkeying with them. Also, you could try unplugging the keyboard when you get to the screen that it stops at. Then plug the keyboard back in and see if that helps.

---

### Post by mattc908 on 2007-12-09
Alright Fixed GParted
Now it says: 

                 File System                 Size                  Used                 Unused 
/dev/hda1  ext3                          71.25gb             2.91gb               68gb                                         
/dev/hda3  ext3                          2.05gb               1.13                   937
/dev/hda2  extended                  1.23


when I type: df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              2110968   1145916    857820  58% /
varrun                  387824        60    387764   1% /var/run
varlock                 387824         0    387824   0% /var/lock
procbususb              387824        88    387736   1% /proc/bus/usb
udev                    387824        88    387736   1% /dev
devshm                  387824         0    387824   0% /dev/shm

How would I have it start saving and using things on /dev/hda1?

---

### Post by Maxtorm on 2007-12-09
Add the following line to your fstab: ```
/dev/hda1 /mnt/hda1 ext3 users,defaults,umask=000 0 0
```Thereafter, your new drive space is available under /mnt/hda1.

---

### Post by mattc908 on 2007-12-10
What is fstab?

---

### Post by MJN on 2007-12-10
I know we're not meant to say 'Google it' but please please do... It's such a useful tool to get used to using. If you're new to searching let me know and I'll provide some pointers to get you started.

If you then have specific queries do shout (although the current first hit (tuxfiles) will likely answer those queries).

Mathew

---

### Post by mattc908 on 2007-12-10
Alright how do I add things to Fstab? The one in /etc/fstab because I added line: /dev/hda1 /mnt/hda1 ext3 users,defaults,umask=000 0 0, but it did nothing....

---

### Post by MJN on 2007-12-10
Adding the entry to /etc/fstab is just a record of the options to use, to actually mount it you need to execute **sudo mount -a **(this mounts all those entries in fstab that are set to auto (default implies auto)) or just target this particular partition with **sudo mount /dev/hda1**.

Note that you need to ensure the mount point exists first i.e. **sudo mkdir /mnt/hda1**

If I were you I'd want to use this newly-found space as my user's home folders as that's where space is typical consumed the most. However, let's prove the concept first with something simple and then we can progress onto that (which will involve shifting some data around amongst other things).

Mathew

P.S. Is this a fresh install, i.e. with no real significant changes having been made? If so, I'd be inclined to start from scratch as you've got a somewhat peculiar disk layout (it'll work but it's probably not one you'd choose given the option).

P.P.S. Out of interest, can you post the output of the **mount** command (i.e. with no arguments set)?

---

### Post by mattc908 on 2007-12-10
```


sudo mount /dev/hda1
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```

---

### Post by Maxtorm on 2007-12-10
> **MJN said:**
> Adding the entry to /etc/fstab is just a record of the options to use, to actually mount it you need to execute **sudo mount -a **(this mounts all those entries in fstab that are set to auto (default implies auto)) or just target this particular partition with **sudo mount /dev/hda1**.
MJN: Are you sure this is strictly true? I was under the impression that by specifying "defaults" under options that auto was implied and the partition would therefore load at boot time when the fstab was read. Is that not the case?

I expect the problem with it not auto-mounting has to do with the error detailed above.

---

### Post by MJN on 2007-12-11
> **Maxtorm said:**
> MJN: Are you sure this is strictly true? I was under the impression that by specifying "defaults" under options that auto was implied and the partition would therefore load at boot time when the fstab was read.

That's right. It sounds like you're agreeing with what I wrote though so I'm not clear on the confusion? :confused:

Edit: Ah - now I see what you mean. Yes, 'auto' will mean that the partition is mounted at boot but I was assuming the OP just edited fstab and nothing changed - i.e. no reboot was done (hence the mount -a suggestion as this is all that happens during boot). I never reboot my machine hence the lack of assumption that a reboot was a given.

> I expect the problem with it not auto-mounting has to do with the error detailed above.
I think the error in this instance is probably because there is no filesystem on the partition. I'm not familiar with gparted however I suspect it doesn't go further than creating partitions and not the overlying filesystem (unless perhaps asked to do so).

Anyway, you can create an ext3 filesystem on the partition using **sudo mkfs -t ext3 /dev/hda1** although please do note that this is one of those 'use with caution' commands - it'll wipe the specified partition clean so beware.

Mathew

---

### Post by mattc908 on 2007-12-11
Again same error even after doing the re partition:
mattc908@mattc908:~$ sudo mount /dev/hda1
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Maxtorm on 2007-12-11
Did the mkfs complete without errors?

---

### Post by MJN on 2007-12-11
Post the outputs of **sudo tune2fs -l /dev/hda1**, **more /etc/fstab** and **mount**

Mathew

---

### Post by mattc908 on 2007-12-12
sudo tune2fs -l /dev/hda1
```

tune2fs 1.40-WIP (14-Nov-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          (print out but not going to share this)
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              9338880
Block count:              18677562
Reserved block count:     933878
Free blocks:              18338449
Free inodes:              9338869
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Tue Dec 11 15:38:53 2007
Last mount time:          n/a
Last write time:          Tue Dec 11 15:39:22 2007
Mount count:              0
Maximum mount count:      37
Last checked:             Tue Dec 11 15:38:53 2007
Check interval:           15552000 (6 months)
Next check after:         Sun Jun  8 16:38:53 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      (There was a printout but not going to share it.)
Journal backup:           inode blocks


```


more /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=da9db0e2-469c-4734-832c-fa0a72600e82 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda6
UUID=021edbb3-b1ea-40f5-8c7a-c19c554d0f0d none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1 /mnt/hda1 ext3 users,defaults,umask=000 0 0
```

Mount:
```
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
```

---

### Post by MJN on 2007-12-12
I forgot to ask for **dmesg |tail**, but your filesystem seems okay (the journal is in a clean state hence it considers itself healthy).

Perhaps try limiting the options in fstab to just **defaults** (i.e. not users,defaults,umask=000) - I don't think ext3 supports umasks (given its native support for permissions).

Incidentally, there's no need to hide your UUID - it's just a random number and only of relevence to your own system.

Mathew

---

### Post by Maxtorm on 2007-12-12
As well, for my own sake of self correction, I believe the "users" should have been "user", but as MJN has so rightly noted, the parameter isn't even necessary.

---

### Post by MJN on 2007-12-12
*users* is fine - it allows any user to mount/unmount the partition. *user*, singular, means that whilst any user can mount the partition only the mounting user can unmount it again.

In this case it's probably better to leave both options out as it going to be treated as a system drive with one or more users accessing it.

Mathew

---

### Post by mattc908 on 2007-12-12
So just:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=da9db0e2-469c-4734-832c-fa0a72600e82 /               ext3    defaults,erro$
# /dev/hda6
UUID=021edbb3-b1ea-40f5-8c7a-c19c554d0f0d none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1 /mnt/hda1 defaults 

?

because I get:
mattc908@mattc908:~$ sudo mount /dev/hda1
mount: unknown filesystem type 'defaults'

---

### Post by MJN on 2007-12-12
You still need **ext3 **and **0 0**. (Sorry - I should have made it clear that only those entries in the fourth are 'options')

Hence, you want:

**/dev/hda1 /mnt/hda1 ext3 defaults 0 0**

Mathew

---

### Post by KD6TZF on 2007-12-12
> **Maxtorm said:**
> Add the following line to your fstab: ```
/dev/hda1 /mnt/hda1 ext3 users,defaults,umask=000 0 0
```Thereafter, your new drive space is available under /mnt/hda1.

I plugged in a new hard drive to my USB 1.0 port and used the GUI to reformat it and created a EXT2 drive. It is now located at ```
/dev/sda1
```

I tried to use the GUI to copy /etc and /home to the hard drive but it would not allow the operation.  The operation was denied because I didn't have permission?  I'm the one who plugged it in and reformatted it but I don't have permission?  It wants the root password.  I don't remember the root password.  I can log into a root terminal window though.  What am I doing wrong?  What are the commands to backup the /etc directory and /home directory.  Maybe I should backup the whole computer, but when I install my new OS, I only want to restore the /etc and /home directories at this time.  Help please!

Also what is fstab?

---

### Post by mattc908 on 2007-12-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=da9db0e2-469c-4734-832c-fa0a72600e82 /               ext3    defaults,erro$
# /dev/hda6
UUID=021edbb3-b1ea-40f5-8c7a-c19c554d0f0d none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1 /mnt/hda1 defaults 0 0


still prints out: 

mattc908@mattc908:~$ sudo mount /dev/hda1
mount: unknown filesystem type 'defaults'

---

### Post by MJN on 2007-12-13
Sorry, I didn't spot you'd removed ext3. Post above now edited to read:

[B]/dev/hda1 /mnt/hda1 ext3 defaults 0 0

[/B](I know it's confusing but technically speaking only the fourth column are 'options')
Mathew

---

### Post by Maxtorm on 2007-12-13
> **KD6TZF said:**
> What am I doing wrong?  What are the commands to backup the /etc directory and /home directory.  Maybe I should backup the whole computer, but when I install my new OS, I only want to restore the /etc and /home directories at this time. 
Hit Alt-F2 to get a command window and then type
```
gksudo nautilus
```If permissions are the issue, you should be able to copy anything to anywhere with that interface. gksudo is the graphical equivalent of the command line sudo.
> Also what is fstab?See: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by mattc908 on 2007-12-13
Alright It seems to have mounted, so how would I got about moving stuff to it and making it like the main drive because of the storage space on it?

---

### Post by mattc908 on 2007-12-16
Anyone?

---

### Post by MJN on 2007-12-16
This isn't boding well given we're at post #33, but assuming you want to use the drive as your /home partition (which, to me, makes sense) then do the following (note this is pure theory and you perform it at your own risk however I am assuming you've backed up anything and everything of importance and any system restore would be merely an unwanted formality):

1. Change into single-user mode to stop the home directories being written to (root has its home in /root/) with [B]sudo telinit 1
[/B]2. Clear out your new partition (hda1) with **sudo rm -fr /mnt/hda1/*** (WARNING: This will remove everything from /dev/hda1)
3. Copy the home directories/contents over to the new partition with **sudo cp -a /home/* /mnt/hda1/**
4. Edit /etc/fstab so that your new partition is mounted on /home by modifying the current /dev/hda1 line to read: **/dev/hda1 /home ext3 defaults 0 2**
5. Create a unique file on the new partition (to distinguish it from the old /home folder) with **sudo touch /mnt/hda1/newhome**
6. Reboot with **sudo reboot**
7. Following reboot all should be hunkydory - check that the new partition is mounted as /home by confirming our unique file exists in the expected location with **ls -l /home/newhome** (if this doesn't show the file, i.e. 'No such file or directory', then something's gone wrong - stop and post back)
8. Assuming the file exists, and everything seems to be working (open up Firefox etc and confirm the bookmarks are present, and any other onfig/customisations in other programs) then drop back down to single user mode with [B]sudo telinit 1
[/B]9. Unmounted the new partition with **sudo umount /dev/hda1**
10. Confirm the unmount was successful by ensuring /dev/hda1 doesn't appear in the output of the **mount **command and/or seeing if our unique file exists with **ls -l /home/newhome** (we should get 'No such file or directory') 
11. Assuming we're still okay then delete the *old* /home contents with **sudo rm -fr /home/***
12. Reboot with [B]sudo reboot
[/B]13. The output of **df -h** should now show separate **/ **and **/home** locations - the latter with plenty of space remaining.

Finger's crossed that should do it!

Mathew

---

### Post by Maxtorm on 2007-12-16
You have many options available. The easiest would probably be to duplicate the small drive onto the larger one using Clonezilla (see previous post for link). If you do that, beware that you'll need to modify GRUB to point to the new device as the boot device. I expect you could find instructions to do this by searching for forums. I don't feel confident enough in my GRUB skills to provide direction.

However, if you're just using the larger drive for storage space, why not just save files there?

---

### Post by KD6TZF on 2007-12-17
Thank you very much.  I've been looking everywhere for that solution.  It works!!!  Thanks.

Any suggestions on how to upgrade my OS from Drapper to Feisty, or the next better OS via the 'net?  I've downloaded the iso disks but have been unable to burn them to cd.  Not sure what I'm doing wrong.  Is there a thread on here that can help?  Thanks,

:):lolflag:

---

### Post by mattc908 on 2007-12-20
mattc908@mattc908:~$ ls -l /home/newhome
ls: /home/newhome: No such file or directory

I don't think it booted up into HDA1, I looked and the file is on there....

---

### Post by MJN on 2007-12-21
What step are you at? What's the output of **mount** and **ls -l /home** ?


Mathew

---

### Post by mattc908 on 2007-12-21
mattc908@mattc908:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /mnt/hda1 type ext3 (rw)

mattc908@mattc908:~$ ls -l /home
total 12
drwxr-xr-x 2 fmaster  fmaster  4096 2007-10-17 17:26 fmaster
drwxr-xr-x 2 ftp      nogroup  4096 2007-09-21 16:42 ftp
drwxr-xr-x 8 mattc908 mattc908 4096 2007-12-12 18:26 mattc908

Im on the step checking is newhome was found but it was not.

---

### Post by MJN on 2007-12-21
What does your fstab look like? Did you change the fstab line in Step 4?

Mathew

---

### Post by mattc908 on 2007-12-21
Thats what my fstab looks like.. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=da9db0e2-469c-4734-832c-fa0a72600e82 /               ext3    defaults,erro$
# /dev/hda6
UUID=021edbb3-b1ea-40f5-8c7a-c19c554d0f0d none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1 /mnt/hda1 ext3 defaults 0 2

---

### Post by MJN on 2007-12-21
You need to follow Step 4.

Mathew

---

