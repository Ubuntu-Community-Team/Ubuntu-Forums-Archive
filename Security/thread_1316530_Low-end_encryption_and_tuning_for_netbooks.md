---
title: "Low-end encryption and tuning for netbooks?"
date: 2009-11-06
forum: Security
---

### Post by mikko.ohtamaa on 2009-11-06
Hi,

Encryption causes several performance penalty on netbooks like Asus Eee pc. It affects the user experience (battery, start up speed, using apps) so much that you actually need to consider whether to use it all. 

[http://blog.redmoonit.de/?p=331](http://blog.redmoonit.de/?p=331) (stats for Truecypt/windows, there is also similar article for Karmic Koala, but didn't have the link now)

If the information is confidential, but not critically confidential, and I'd like to crypt the disk just to protect it against non-sophisticated attacks, can I tune encrypted home folder feature somehow to use less taxing encryption methods?

---

### Post by lensman3 on 2009-11-06
Sounds like you need a Rot13 or an xor encryption.

The only thing I can think of is if trucrypt has a way to install your own modules (which I doubt).

Sorry I can't help you more.

---

### Post by bodhi.zazen on 2009-11-06
Well, why encrypt the entire disk then, why not encrypt just a single folder?

You can do this with a number of tools, 

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by Agent ME on 2009-11-06
Ecryptfs sounds like the best bet. With it, you can choose to only encrypt specific files and folders.

---

### Post by shaggy999 on 2009-11-08
> **mikko.ohtamaa said:**
> Hi,

Encryption causes several performance penalty on netbooks like Asus Eee pc. It affects the user experience (battery, start up speed, using apps) so much that you actually need to consider whether to use it all. 

[http://blog.redmoonit.de/?p=331](http://blog.redmoonit.de/?p=331) (stats for Truecypt/windows, there is also similar article for Karmic Koala, but didn't have the link now)

If the information is confidential, but not critically confidential, and I'd like to crypt the disk just to protect it against non-sophisticated attacks, can I tune encrypted home folder feature somehow to use less taxing encryption methods?

I run full-disk encryption on an eeePC 900a (1.6 GHz Atom w/ 2 GB RAM, 16 GB SSD) and performance is fantastic, bootup time is quick, and battery lifetime is no different than unencrypted. I use ext4 for my partitions and the disks are all mounted 'nodiratime', tmp is mounted tmpfs, etc. Are you using an older celeron eeepc?

---

### Post by mikko.ohtamaa on 2009-11-08
> **shaggy999 said:**
> I run full-disk encryption on an eeePC 900a (1.6 GHz Atom w/ 2 GB RAM, 16 GB SSD) and performance is fantastic, bootup time is quick, and battery lifetime is no different than unencrypted. I use ext4 for my partitions and the disks are all mounted 'nodiratime', tmp is mounted tmpfs, etc. Are you using an older celeron eeepc?

I have EeePC 1005HA with encrypted home folder and Ubuntu 9.10 Karmic Koala now. It has *slow* 160 GB hard disk. Adding encryption to the mix is not a good idea. 

The performance difference, depending on what you are doing with the laptop, compared to unecrypted is notable. Mainly, because CPU is taxed during disk access the battery life gets worse when doing disk sensitive tasks (compiling, even video playback).

What's encryption method provided by 9.10 default install? I heard AES 128 (instead of AES 256 if used) would be lighter. 

I hope I could find "light" encryption. It just weighting risks against the other factors. Some applications need fire proof safe, for some cheap lock is enough.

Here are some solid numbers:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1)

---

### Post by mikko.ohtamaa on 2009-11-08
Also, one funny thing I noted getting hitted by disk encryption is Firefox's "AwesomeBar".

When you type anything to address bar SQLite does some huge queries from the browser history. This usually involves disk access. Prior Firefox 3.6 this look-up is UI blocking. If you have encrypted disk and big browsing history, Firefox will freeze for 3-8 seconds when starting typing to the location bar.

---

### Post by shaggy999 on 2009-11-09
ah, yes... a regular HDD. That probably makes a huge difference. You could try mounting unionfs your .mozilla directory to tmpfs. If you want to keep anything just write a script that runs on shutdown that syncs the "real" .mozilla directory w/ the tmpfs one. When initially reading it will be slow, but subsequent reads will be blazing fast.

---

### Post by mikko.ohtamaa on 2009-11-13
Does anyone have pointers how to actually tune /home encryption? E.g. changing the encryption algorithm to something less-CPU-taxing.

---

### Post by movieman on 2009-11-14
I enabled home directory encryption on my netbook and haven't seen any problems so far. That said, I don't copy big files in and out of there on a regular basis.

---

### Post by movieman on 2009-11-14
Actually, I did some measurements and 'dd if=/dev/zero of=[file] bs=1M count=1000" dropped from 70MB/s to 11MB/s when switching from /tmp to $HOME. However, all my big files are on the home server so that's not a big deal compared to knowing that if someone steals the computer they can't access my files.

I am surprised that encryption would slow it down that much: I'm wondering whether the inefficiency of going through FUSE is part of it, or whether the encryption layer is doing extra fsyncs to ensure that the files get written to disk.

---

