---
title: "Backing up a server to an external drive"
date: 2010-07-17
forum: Server Platforms
---

### Post by poltr1 on 2010-07-17
I have an Ubuntu server running Lucid.  I'd like to be able to back up the hard drive in the server to an external hard drive.  I try to plug in a drive via a USB port and it doesn't appear to mount automatically, as it does on the desktop version.  Questions: 1) What/where should I be looking for to see if the drive is mounted?  (I've looked in /dev and /media; no dice.)  2) What's the mount command I should use to manually mount the external hard drive?  3) What backup commands or programs, other than rsync, are recommended?  (Nothing against rsync.)

---

### Post by kevin11951 on 2010-07-17
> **poltr1 said:**
> I have an Ubuntu server running Lucid.  I'd like to be able to back up the hard drive in the server to an external hard drive.  I try to plug in a drive via a USB port and it doesn't appear to mount automatically, as it does on the desktop version.  Questions: 1) What/where should I be looking for to see if the drive is mounted?  (I've looked in /dev and /media; no dice.)  2) What's the mount command I should use to manually mount the external hard drive?  3) What backup commands or programs, other than rsync, are recommended?  (Nothing against rsync.)

To mount a drive:

```
mount -t auto /dev/<drive> /media/<folder>
```

<drive> - sda1, sda2, etc...  Must include partition number, you cant mount a whole disk.

<folder> - where you want it mounted.  And you can mount in anywhere in your filesystem, just /media/ is standard.

---

### Post by mrtomservo on 2010-07-17
You could try "usbmount", if you'd like it to automount when plugged in.  If you want it auto mounted on boot like your regular hard drive i'd do the following:

Plug in/turn on the usb drive and at the terminal run: ```
sudo fdisk -l
``` and find out the /dev/sdxx name for the drive you want to mount.  You can either add a /dev/sdxx or the UUID as the drive identifier.  To get the UUID run: ```
sudo blkid
``` and find the number for your drive.  Next edit the /etc/fstab file and add a line at the bottom that looks like the following:```
/dev/sdb1	/data		ext4	defaults	0	0
```

Where /dev/sdxx is the device name or UUID, then comes the directory you'd like it to be mounted, then comes the file type, then options for mounting it. Follow that up with a 0, 0 and save.

Then run ```
sudo mount -a
``` and it should be mounted where you told it to mount.  You may need to reboot to get the permissions right on the directory. (ie RW)

---

### Post by sam@hcl on 2010-07-17
> **mrtomservo said:**
> You could try "usbmount", if you'd like it to automount when plugged in.  If you want it auto mounted on boot like your regular hard drive i'd do the following:

Plug in/turn on the usb drive and at the terminal run: ```
sudo fdisk -l
``` and find out the /dev/sdxx name for the drive you want to mount.  You can either add a /dev/sdxx or the UUID as the drive identifier.  To get the UUID run: ```
sudo blkid
``` and find the number for your drive.  Next edit the /etc/fstab file and add a line at the bottom that looks like the following:```
/dev/sdb1    /data        ext4    defaults    0    0
```Where /dev/sdxx is the device name or UUID, then comes the directory you'd like it to be mounted, then comes the file type, then options for mounting it. Follow that up with a 0, 0 and save.

Then run ```
sudo mount -a
``` and it should be mounted where you told it to mount.  You may need to reboot to get the permissions right on the directory. (ie RW)
check whether usb stick is detected or not by "fdisk -l". Then mount that file system /dev/s* using following command using 
 
mount -t [vfat or ntfs] /dev/* [mount-point]

---

### Post by Vegan on 2010-07-18
I found using the LAN was as easy to backup to.

My backup server already has a bunch of USB sticks on it. 

SAMBA makes it easy to work with, I share the mount folder and I have the sticks under that and I can rsync it all to another machine.

---

### Post by poltr1 on 2010-07-29
Thanks, folks.  I had to install usbmount on the server in order for the external hard drive to be even recognized when it was plugged in.  (It's an external hard drive in an enclosure; not a stick.)

```

sudo apt-get install usbmount

```

Then, with the drive identified and visible via fdisk -l, I could then issue the mount command.

```

sudo mount -t ntfs /dev/sdb1 /media/usb

```

I'm currently backing up the server right now, with rsync.  Hope I don't run into any recursion problems here.

```

rsync -av / /media/usb

```

---

