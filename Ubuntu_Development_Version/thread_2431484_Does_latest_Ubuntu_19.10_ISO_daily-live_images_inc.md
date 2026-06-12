---
title: "Does latest Ubuntu 19.10 ISO daily-live images includes Radeon Navi firmware"
date: 2019-11-17
forum: Ubuntu Development Version
---

### Post by shamb0 on 2019-11-17
Hi,


This is with reference to post **"Ubuntu 19.10 Doesn't Ship With AMD Navi / Radeon RX 5700 Support Working, But Easy To Enable"** from link


[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700)


In 21-Oct-2019 post it's mentioned that "Radeon Navi firmware wasn't landed for making the official Ubuntu 19.10 ISO"


Is there any update on it. Does Nov-2019 daily-live images in the link [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
includes Radeon Navi firmware ?

---

### Post by oldfred on 2019-11-17
When ISO is released, the daily live are then not updated anymore. 
Note that current has Oct 15th date. That at some point will change to be Focal. 

But pending & each day in index is now 20.04 Focal. And many updates have already been added. But many more will be added some multiple times.
You can test yourself by downloading new Focal ISO and see if it boots without nomodeset boot parameter.

I use zsync to update ISO, so not downloading full ISO every time. I rename 19.10 and zsync it to start. And change from each date in beginning to current once it is Focal based.

Using the 1019 versions just a few days after 19.10 finalized.
Renamed eoan to focal
```
fred@Bionic-Z170N:~/ISO$ zsync http://cdimage.ubuntu.com/daily-live/20191019/focal-desktop-amd64.iso.zsync
Read focal-desktop-amd64.iso. Target 98.9% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/20191019/focal-desktop-amd64.iso:
#################### 100.0% 3487.2 kBps DONE     

verifying download...checksum matches OK
used 2436005888 local, fetched 27980878

```

---

