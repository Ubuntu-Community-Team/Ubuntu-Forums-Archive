---
title: "USB drives not listed in fdisk and unable to mount"
date: 2010-03-12
forum: Server Platforms
---

### Post by willowave on 2010-03-12
New server ubuntu 9.10 install with Samba set up. Drives were mounted before Samba, but after samba was set up and I can see the server on a windows network, I can not get the usb external drives to mount or be seen at all. I also added ubuntu desktop.
I used this link to set up the server and samba. 
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
 
The external drive is a box of 4 drives formatted as ntfs, worked fine before I set up Samba. I am assuming when I edited the fstab toward the end I did something, just not sure what. The drives are (or were showing up as) /dev/sdb1, sdc1, sdd1, and sde1. I tried to follow the wiki on how to maybe set up automounting and thats when I found they werent even showing up in fdisk.

---

