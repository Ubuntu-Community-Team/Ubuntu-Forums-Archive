---
title: "Automatically mount ext3 usb drive"
date: 2009-07-30
forum: Server Platforms
---

### Post by dualityim on 2009-07-30
I'm using ubuntu 9.04 as a server, and I have an USB external hard drive formatted with ext3 located at /dev/sdb1. I'd like to have it automatically mount to /media/external0 everytime the machine starts. Could someone help me with which configuration file I should edit and what lines I should insert to make this happen? Thank you very much.

---

### Post by Katalog on 2009-07-30
Have you given [PySDM]("http://pysdm.sourceforge.net/") a try (it should be in the Ubuntu repos)? Worked wonders for me in a similar situation.

---

### Post by garfonzo on 2009-07-30
I have the same situation. I have 9.04 server headless with two USB drives with Ext3 that mount automatically everytime the machine boots. 

Find the file: 

/etc/fstab

make a backup:

```
sudo cp fstab fstab.BU

```

then, on the original  fstab file, add the following line for each hard drive:

```
/dev/sdd1       /path/to/mount/point   ext3    defaults        1       2
```

for you, instead of /dev/sdd1 you would use /dev/sdb1 and instead of /path/to/mount/point you would use /media/external0

I'm sure others will chime in with how they've done it, but with that line for me, I have read/write access to the drive from my lan computers running Windows (of course, Samba was set up on the server too)

Hope this helps!

Cheers

---

### Post by R.Bucky on 2009-07-30
chiming in...
I mount my external drive upon boot. i use it for my backup drive...

Insert the bottom line at the bottom of your fstab. restart your box and you are off

```

sudo mkdir /external
sudo vi /etc/fstab
/dev/sdf1 /external ext3 defaults 0 0
```

---

### Post by dualityim on 2009-07-30
Thanks for the help. However the two above posts differ in how I should set the <dump> and <pass> information in the fstab file. Do these settings matter and what are the correct settings?

---

