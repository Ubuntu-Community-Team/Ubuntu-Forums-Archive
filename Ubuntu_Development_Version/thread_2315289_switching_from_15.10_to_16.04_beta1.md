---
title: "switching from 15.10 to 16.04 beta1 ?"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by hms666 on 2016-02-27
Is it safe to [COLOR=#000000][FONT=Ubuntu Mono]sudo do-release-upgrade -d or does it even work with ubuntustudio? Or just download iso from [/FONT][/COLOR]http://cdimage.ubuntu.com/ubuntustudio/releases/16.04/beta-1/.

Nvidia stopped working properly so I guess could make the switch allready, steam stopped working first and I don't have the change options anymore with update system dialog. Now latest updates gave blackscreen for nvidia.

---

### Post by Frogs Hair on 2016-02-27
Try running the following. ```
sudo apt-get update
``` ```
sudo do-release-upgrade -d
``` If no new release is found then there may be  different command/s for Ubuntu Studio . This worked for Ubuntu 15.10.

It's very early to upgrade on a daily user machine, use at your own risk and backup before starting.

---

### Post by Bucky Ball on 2016-02-27
*Thread moved to **Ubuntu Development Version**.*

---

### Post by oldrocker99 on 2016-02-27
> **Frogs Hair said:**
> 
It's very early to upgrade on a daily user machine, use at your own risk and backup before starting.

Just what I was wondering; good to know.

---

### Post by grahammechanical on 2016-02-27
De-activate any proprietary video driver and revert to the open source video driver. Also, revert the desktop to as default state as possible. 

I always run the development version. And there are two times when I would upgrade from a stable release to a development release. 1) During the first four weeks of the development period when there has been little change to the code. 2) During the last 4 weeks of the development period to test the upgrade path.

In between I always do a fresh install. According to the release schedule 24 March is final beta freeze and final Beta.

If it goes well, then it has gone well. If there are problems, then update daily until released day and hope the problems get fixed.

[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

I suggest uninstalling stream. It is not part of the Ubuntu devs upgrade plans.

Regards.

---

