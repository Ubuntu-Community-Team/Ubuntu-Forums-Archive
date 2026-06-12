---
title: "Automount USB drives"
date: 2009-09-13
forum: Server Platforms
---

### Post by ksenos on 2009-09-13
Hello,

I would like to know if it is possible to automount USB hard disks and flash drives on ubuntu server in a similar way that they are automounted on ubuntu desktop. To be more specific, the drives should be automounted on /media/<LABEL> where <LABEL> is the label of the partition. Is it possible? So far I had no success following several old howtos :confused:. 

Thank you very much in advance.
Kostas

---

### Post by tlarkin on 2009-09-14
I suppose you could add entries for each disk in /etc/fstab and give it specific mount points to your pleasing, and also enable auto mount as well.

---

### Post by cariboo on 2009-09-14
I have two external usb drives mounted in /media, and use this line in /etc/fstab:

```
/dev/sde1 	/media/external	xfs	relatime	0	2
```

I have one formatted as xfs and the other as ext4

---

### Post by ksenos on 2009-09-14
Currently I use mount like you say. The server machine is just a small file server and there is no keyboard or screen attached to it. I need automount mostly for convenience especially when I want to transfer files from and to a friend's hard disk or flash drive. Isn't there a way to "capture events" and run a custom script when a usb mass storage device is attached?

---

### Post by tlarkin on 2009-09-14
Is ssh enabled?  You can always mount it from the command line.  However, adding an entry in /etc/fstab will abide by most rules you set for it.  I have, a few times, seen /etc/fstab not work quite properly on different versions of Unix/Linux.

---

### Post by cmcanulty on 2009-09-14
I can't get my external hard drive to mount and even reformatted   it to ext3 and lost all my backups in trying to get it mounted. I don't know what to type in for mount since it doesn't show up under computer. Do I just make up a name for it? Very frustrating. I have tried to back up all day on it. Tried to use gparted to partition and couldn't. I tried using several backup programs and all return errors. It worked fine yesterday.My windows laptop sees it fine. I have about given up on this.

---

### Post by sherl0k on 2009-09-15
sudo aptitude install pmount

problem solved. :)

---

