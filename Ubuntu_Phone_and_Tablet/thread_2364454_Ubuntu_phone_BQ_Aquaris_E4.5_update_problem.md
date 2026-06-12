---
title: "Ubuntu phone BQ Aquaris E4.5 update problem"
date: 2017-06-23
forum: Ubuntu Phone and Tablet
---

### Post by vagrale on 2017-06-23
I  have a problem with my Ubuntu phone. I can't update. There is available  Ubuntu Version 36, but when i choose restart and install nothing  happens.

 [I]Device: BQ Aquaris E4.5
Last updated: 7/12/16
Version: Ubuntu 15.04-armhf (20161118-171123)[/I]

---

### Post by howefield on 2017-06-23
Updates are stopping this month, if they haven't already. The app store closes at the end of the year.

What is Ubuntu Version 36, the over the air updates didn't get much past OTA-15 ?

---

### Post by vagrale on 2017-06-24
I think i am in OTA-13.
The problem where i have is in the known issues here [https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-14](https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-14)
I tried that it says but without success.
```
:~$ uname -a
Linux ubuntu-phablet 3.4.67 #1 SMP PREEMPT Mon Jun 6 12:04:40 UTC 2016 b75400e armv7l armv7l armv7l GNU/Linux
```
```
:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"
NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

---

### Post by wlbi on 2017-06-25
Canonical stopped the Ubuntu Touch project already. 
The UBports guys are continuing that. Check here: [https://ubports.com/](https://ubports.com/)
I flushed my E4.5 also with the UBports image and everything works fine as expected.
Shee here, how to flush your phone with the new image: [https://ubports.com/page/fs-flash-phone#myCollapse1497451771219](https://ubports.com/page/fs-flash-phone#myCollapse1497451771219)
:D

---

### Post by peter d on 2017-06-29
Another vote for UBports. I use it on my Nexus 5. Unusable three months ago, but a good daily driver now.

---

