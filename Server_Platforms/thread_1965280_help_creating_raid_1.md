---
title: "help creating raid 1"
date: 2012-04-25
forum: Server Platforms
---

### Post by darknoobie on 2012-04-25
I have a small web server that will be hosting files soon. I have a 2 tb hard drive in it now holding all the files. I just bought another 2tb hard drive. Is there any way to create a raid 1 using the existing hard drive without wiping the data?

I followed this tutorial:
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

---

### Post by carreira on 2012-04-25
You can use raider.
[http://raider.sourceforge.net/](http://raider.sourceforge.net/)

---

### Post by elico on 2012-04-25
it depends if you have used lvm or not.
if you didnt used lvm it can be pretty simple.
a recommendation is to always backup your data and then start the process.
what is the current setup of the hd? lvm?basic fs?

---

