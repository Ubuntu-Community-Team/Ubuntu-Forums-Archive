---
title: "Recovering files from XP HDD using Ubuntu 7.10"
date: 2008-04-27
forum: Security
---

### Post by 1inxs on 2008-04-27
My wifes Windows XP Home edition has crashed or been hacked. She was using a bit torrent program called usenext for approximately a week. Then her system completely stopped working. I tried to mount the HDD, but I get 

kristin@kristin-desktop:~$ sudo fdisk -l

Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007a07

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3579    28748286   83  Linux
/dev/hda2            3580        3738     1277167+   5  Extended
/dev/hda5            3580        3738     1277136   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04000401

Disk /dev/hdd doesn't contain a valid partition table
kristin@kristin-desktop:~$ 

It appears the XP HDD 200.0 GB no longer contains a valid partition table. Any help on recovering her files would be appreciated. Thanks!

---

### Post by kg87 on 2008-04-27
Clutching at straws, you could always pop in your XP cd, and run fixboot, or  fixmbr (or both). I had this on a much smaller scale and used

[http://www.ptdd.com/]("http://www.ptdd.com/")

im not sure it will help in your case, but its worth a shot!

---

### Post by lemming465 on 2008-04-27
You might want to try something more specialized for data recovery such as  [Helix forensics CD]("http://www.e-fense.com/helix/links.php").  This might be easier to use than Ubuntu.  In particular, it has tools to help identify partition boundaries, recover files from unpartitioned space, and so on.

---

### Post by 1inxs on 2008-04-28
> **lemming465 said:**
> You might want to try something more specialized for data recovery such as  [Helix forensics CD]("http://www.e-fense.com/helix/links.php").  This might be easier to use than Ubuntu.  In particular, it has tools to help identify partition boundaries, recover files from unpartitioned space, and so on.

Thanks for the lead. I downloaded and booted from the Helix CD. No instructions. I notice they have forums on their website. I will see if information is available for using Helix. I couldn't find instructions for recovering a Windows XP HDD. The problem with my wifes HDD is it does not boot into an operating system environment.

---

### Post by lemming465 on 2008-04-28
Turns out my peers at the University of Wisconsin-Madison are fond of "GetDataBack" from [Runtime]("http://www.runtime.org"), assuming you have a spare $79 to invest in the project.  That will probably be a lot easier to use than Helix, and they'll let you try it to see if it will work before you buy and use it save the recovered files.

---

### Post by 1inxs on 2008-04-28
> **lemming465 said:**
> Turns out my peers at the University of Wisconsin-Madison are fond of "GetDataBack" from [Runtime]("http://www.runtime.org"), assuming you have a spare $79 to invest in the project.  That will probably be a lot easier to use than Helix, and they'll let you try it to see if it will work before you buy and use it save the recovered files.

GetDataBack seems to be quite easy to use. I was hoping to find a Linux based application to use, but I could build a Windows PC to recover her files. Thanks Much for posting back with this helpful information. I'll follow up with a conclusion to this post.

---

### Post by hyper_ch on 2008-04-29
You might want to try:

[http://www.ontrackdatarecovery.com/](http://www.ontrackdatarecovery.com/)

They offer different services... even remote recovery or software to do so...

if you have another computer you (1) put that harddisk in the other computer (2) download a trial version: [http://www.ontrackdatarecovery.com/data-recovery-downloads/](http://www.ontrackdatarecovery.com/data-recovery-downloads/) (3) see how the trial version handels it and then maybe purchse the program

---

### Post by tliotis on 2008-04-29
and one very nice program is final data for windows xp and you must run it on second xp computer!

---

### Post by bigken on 2008-04-29
if you have a windows xp disc boot from it at the prompt press R for recovery console select your windows partition usually 1 and hit enter then enter again for the admin password type chkdsk enter then chkdsk /p /r if this does not fix it run the repair console again and try fixmbr and fixboot you could also consider the [UBCD]("http://www.ultimatebootcd.com/") with this you can restore your registry to an eariler time or recover your files to a usb device good luck

---

