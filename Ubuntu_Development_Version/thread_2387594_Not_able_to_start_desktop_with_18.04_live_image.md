---
title: "Not able to start desktop with 18.04 live image"
date: 2018-03-21
forum: Ubuntu Development Version
---

### Post by bala on 2018-03-21
I downloaded 18.04 live cd (from daily live) and tried to start using "Try without installing". However, I got only a blank page with a gray bar on top. 

Hardware is a dell laptop with AMD A6 processor. Currently I'm using xubuntu 17.10 installed version and is working fine.
 
What could be the issue and how to debug it?

---

### Post by wildmanne39 on 2018-03-21
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by bala on 2018-03-21
I left the blank screen as such for around  3-4 minutes and eventually I was able to see the desktop. Not sure why it took so long. 

However, after that desktop just hangs. I can move the mouse but the clicks have no effect and keyboard is also not working. I've faced this same behaviour with other distributions(qt, gnome DEs), which makes me believe this is some kind of kernel + driver issue.

I'll wait until for some time before testing with new version again.

---

### Post by wildmanne39 on 2018-03-21
You do realize that this version is in the developmental stage correct? I run it on 3 computers with no issue, it is possible that you just need to log out then log in with xorg and not wayland because wayland is not nearly a developed as xorg, it would help if you posted the specs of your computer here.

---

### Post by bala on 2018-03-21
I tested with xubuntu. I thought it always used xorg. For other DEs(KDE, Gnome) I didn't use ubuntu.

This is the laptop I'm using:
[https://www.bestbuy.com/site/dell-inspiron-11-6-laptop-amd-a6-4gb-memory-32gb-emmc-flash-memory-gray/6188326.p?skuId=6188326](https://www.bestbuy.com/site/dell-inspiron-11-6-laptop-amd-a6-4gb-memory-32gb-emmc-flash-memory-gray/6188326.p?skuId=6188326)

It has AMD A6-9220e processor, R4 graphics chipset, 4GB of ram and eMMC flash drive.

---

### Post by slickymaster on 2018-03-21
Did you checked the integrity of the downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by bala on 2018-03-21
I verified now and checksum looks correct. Anyway, I'll try again after one more week.

---

