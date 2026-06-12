---
title: "Boots into terminal after update/upgrade"
date: 2015-03-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-03-12
Working on a  kubuntu install of 15.04 I booted up this :am after upgrade yesterday and it will not boot into desktop. Only terminal. I tried systemd and other kernels but nothing is working as far as GUI.

Regards..

---

### Post by xc3RnbFO8P on 2015-03-12
Kubuntu 15.04 only works with SDDM in my computer.

---

### Post by Rog131 on 2015-03-12
From the kubuntu-devel: [http://irclogs.ubuntu.com/2015/03/12/%23kubuntu-devel.html#t15:24](http://irclogs.ubuntu.com/2015/03/12/%23kubuntu-devel.html#t15:24)
> mparillo	Last night, I applied updates to Vivid and shut down. This morning, it booted to tty1 instead of SDDM. I applied updates in tty1, and got lots of ufs errors. Is this a known problem? 	15:24
...
Riddell	so sddm isn't starting I guess	15:27
Riddell	systemctl start sddm ?	15:27


---

### Post by lee295012-gmail on 2015-03-12
bug report and a solution on the last comment
[https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1430817](https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1430817)

---

### Post by ventrical on 2015-03-12
> **lee295012-gmail said:**
> bug report and a solution on the last comment
[https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1430817](https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1430817)

This has fixed it temporarily but the screen goes thorugh this broken - bass-half -ackwards loadup with all sort of relics.. etc.... but it is working :) lol

---

