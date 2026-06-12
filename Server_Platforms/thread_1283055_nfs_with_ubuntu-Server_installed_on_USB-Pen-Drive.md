---
title: "nfs with ubuntu-Server installed on USB-Pen-Drive"
date: 2009-10-05
forum: Server Platforms
---

### Post by pezzi on 2009-10-05
-- Moved to Server-Platforms
 
I just installed ubuntu 9.04 Server (up to date) on an USB-Pen-Drive (8 GB, MSI Wind PC, 2x 1TB HD Raid1). I am using ram2log and var in RamDisk. As Services are Samba and NFS started. Samba is running fine (Transfer Writing approx. 25 MB/s!). But nfs (kernel-server-Version) is very slow (less than 1 MB/s). I think something (a kind of daemon/log) is writing onto the usb-drive which slows down the transfer rate. Has anybody an idea, where i can search further?
 
Thanks in advance.
 
Regards,
 
pezzi

---

### Post by pezzi on 2009-10-05
I just installed ubuntu 9.04 Server (up to date) on an USB-Pen-Drive (8 GB, MSI Wind PC, 2x 1TB HD Raid1). I am using ram2log and var in RamDisk. As Services are Samba and NFS started. Samba is running fine (Transfer Writing approx. 25 MB/s!). But nfs (kernel-server-Version) is very slow (less than 1 MB/s). I think something (a kind of daemon/log) is writing onto the usb-drive which slows down the transfer rate. Has anybody an idea, where i can search further?
 
Thanks in advance.
 
Regards,
 
pezzi

---

### Post by cariboo on 2009-10-05
If you post in the wrong place please use the report button (Report Abuse) and one of us mods will move it for you.

---

### Post by KillaB7 on 2009-10-07
I installed 9.10 Server (Beta) on my 2GB OCZ Rally today and ended up not being able to run "top" or "free" once installed.  Performed apt-get update and upgrade, but the new packages ended up failing to install.

Love to hear your thoughts on running off of USB and how you go about dealing with /var, etc.
[http://ubuntuforums.org/showpost.php?p=8068277&postcount=8](http://ubuntuforums.org/showpost.php?p=8068277&postcount=8)

---

### Post by pezzi on 2009-10-17
So, i used "rootaufs" and it's running fine. Now nfs (which was really slow before) is now running an avg of 40 MB/s over GB-Network on an MSI Wind PC (Single Atom).

---

### Post by KillaB7 on 2009-10-17
Hey pezzi, what release are you running and did you simply follow the [howto from the wiki](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)?

I loaded 9.10 beta onto an older 2GB Cruzer Micro, but it was painfully slow.
I then tried getting aufs working, but because 9.10 uses GRUB2, perhaps the script will need to be modified. I didn't see separate /ro and /rw entries when running df.

Since we seem to be doing something similar (however I don't need RAID), any chance you could comment on [my new thread](http://ubuntuforums.org/showthread.php?p=8118171)
Not sure if I should buy an OCZ Diesel, or just create a small partition on one of the drives.

---

