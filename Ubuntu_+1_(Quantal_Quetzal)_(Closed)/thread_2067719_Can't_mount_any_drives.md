---
title: "Can't mount any drives"
date: 2012-10-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by xeriouxi on 2012-10-07
Hi,

I'm running 12.10 (Beta 2) and I've been unable to mount any of my drives for some time. Whenever I try to mount my Windows partition or my external HDD, I get a message saying:

```
Could not display "/media/[Username]/[Drive label]".
The location is not a folder.
```

I've read that there has been a change to how drives are mounted but I'm at a loss as to how I can start using my drives again. Does anyone know how to fix this problem?

Many thanks! :)

---

### Post by TheFu on 2012-10-07
What specific errors do the log files show?

Check dmesg and syslog.

```
$ dmesg|more
```
and 
```
$ sudo more /var/log/syslog
```

---

### Post by xeriouxi on 2012-10-07
Thanks for your reply, TheFu!

I can't see anything that stands out at me when I checked dmesg and syslog, but I did try after my first post to access the drives via Nautilus running as root and I could access them without any problems?

---

### Post by TheFu on 2012-10-07
Usually when partitions are mounted as read-only, that means there's an issue with either the physical drive or logically in the data on the partition.  An **fsck** needs to be run.  

Running nautilus as root is a bad idea from a security perspective.  Learn to use sudo only when necessary and only for the time that it is necessary.

You can learn more about fsck by opening a terminal and running
```
 $ man fsck
```

For the / mounted partition, you'll probably want to use the **/forcefsck **technique, though you could use a "save-your-butt" LiveCD method too and manually run it against the specific partition on the HDD.

---

### Post by xeriouxi on 2012-10-07
I'm not very keen on using fsck, especially as it says it will damage my file system.

I just viewed the properties of my external HDD (which works fine under Windows) and it says the permissions of the drive could not be determined under the 'Permissions' tab, and the 'Open With' tab has gedit set as the default application to open the folder and other files of type "(null) document".

Could this be related to the issue I have?

---

### Post by TheFu on 2012-10-07
fsck should be used on Linux formatted partitions only, never on NTFS or xfat or vfat partitions.

Warnings are good to understand. They are telling you that you are probably trying to use a command improperly. You should read **AND UNDERSTAND** the entire warning message before moving forward.

If you are using wubi or other non-native Linux partitions, I can't help you.

Just because something "works" under Windows, that doesn't mean it is fine.  Microsoft violates standards all the time.

---

### Post by xeriouxi on 2012-10-07
Well this only started happening after I'd started to try 12.10 and as it works using root I assume it's some kind of issue with the /media/[Username]/ update that's happened recently.

If I go into /media/ and try to select the folder that's my username it says that it's assigned to root and I can't access it but my two mounted drives, when accessing Nautilus as root, show up in there.

What I meant when I said it works under Windows is that I've not had any issues with corrupt partitions or anything.

[UPDATE] It seems I've fixed the problem; I just took permission of the /media/[Username] directory and set the mounted drives in that directory to open with 'Files' and it all works now. Thanks for your help, TheFu!

---

### Post by funicorn on 2012-10-08
It seems to me udev cannot acquire your username and/or the driver label. So check your drive label first. Here is the thing, normally speaking when udev tries to automount the partition, it firstly use the drive label to make the mount point, then user uuid if drive label is not available.

However there is always silly mistake in the codes, the drive label is not accessible then udev gives up trying and send an error.

---

### Post by stewacide on 2012-10-11
Same problem. Can't mount any drives. Get the can't mount / not a folder error. Can mount when I open Nautilus as root.

I had just changed by UID to 501 to match OSX's so I could access my MacOS partition, but now this. Any idea why that broken mounting drives and how I can fix it?

Running 12.10 B2.

edit -- Fixed by changing ownership of /media/username. Should have read more carefully!

---

### Post by TheFu on 2012-10-11
mount is a command that only root can run due to security.  It is possible to many mount run-as root always, but this is a MAJOR security issue, IMHO. Many distros set up mount in this way.

**It is not broken.**

It is only inconvenient, IMHO.

You can setup the /etc/fstab to automatically mount different drives when they are inserted, if you like. Definitely use the uuid-based version of the mount.  In this way, you won't have to decrease security by making mount automatically available to everyone on the system, but the devices will still be automatically available when inserted.

This should help: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

