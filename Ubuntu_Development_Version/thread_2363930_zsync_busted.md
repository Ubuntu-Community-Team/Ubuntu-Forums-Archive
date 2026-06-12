---
title: "zsync busted?"
date: 2017-06-16
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-06-16
I'm zsyncing an image and it is overwriting rather than updatng the artful-desktop.

 I'm doing this on a 16.04 unity install.

anyone else?

---

### Post by rrnbtter on 2017-06-16
Greetings,
Working fine here from Gnome x11.  I run zsync from a bash file so that I get the proper terminal input every time. 

Read /home/rrnbtter/artful-desktop-amd64.iso. Target 80.6% complete.      
reading seed file artful-desktop-amd64.iso:

Read artful-desktop-amd64.iso. Target 80.6% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso:)
################---- 80.8% 515.6 kBps 9:36 ETA

---

### Post by oldfred on 2017-06-16
From my 16.04 fallback/gnome-panel, it just worked for me. I had updated about 4 days ago, but never got around to installing it yet.

```
Read artful-desktop-amd64.iso. Target 93.1% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso:
#################### 100.0% 2149.3 kBps DONE      

verifying download...checksum matches OK
used 1422999552 local, fetched 106446989
fred@Asusz97:~/ISO$ ls -l art*
-rw------- 1 fred fred 1528430592 Jun 15 08:00 artful-desktop-amd64.iso
-rw------- 1 fred fred 1526726656 Jun 12 09:21 artful-desktop-amd64.iso.zs-old


```

And it copied backup file ok.

---

### Post by rrnbtter on 2017-06-16
Greetings,
rrnbtter@rrnbtter-110-15ISK:~$ apt policy zsync
zsync:
  Installed: 0.6.2-2ubuntu1
  Candidate: 0.6.2-2ubuntu1
  Version table:
 *** 0.6.2-2ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
        100 /var/lib/dpkg/status


I also did a CRTL-Break on my download, rebooted and started over and it correctly updated my .part file. 

Read artful-desktop-amd64.iso. Target 80.6% complete.      
reading seed file artful-desktop-amd64.iso.part: *******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read artful-desktop-amd64.iso.part. Target 97.7% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/current/artful-desktop-amd64.iso:)
###################- 97.7%

---

### Post by ventrical on 2017-06-16
I used a broken code :)

my bad..
regards..

---

