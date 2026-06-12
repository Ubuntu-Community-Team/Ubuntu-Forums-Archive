---
title: "How to install XunLei 7 or Thunder on Wine ?"
date: 2011-03-14
forum: Wine
---

### Post by xmuranox on 2011-03-14
Any idea if XunLei 7 or PPS can be supported in Wine ?

---

### Post by infimax on 2011-05-06
Hi,i know that ppstream has officially support linux,u can download it from [http://dl.pps.tv/](http://dl.pps.tv/),which is in .deb package.

For the thunder installation method u can follow this guide: 

Linux + wine + Thunder 5(but not 7,download from here [http://hi.baidu.com/xxcxz/blog/item/c130e9779489c01ab151b93f.html](http://hi.baidu.com/xxcxz/blog/item/c130e9779489c01ab151b93f.html))

Copy c: \ windows \ system32 \ msvcp60.dll under the dynamic link library and mfc42.dll to the ~ / .wine/drive_c/windows/system32 next. Then wine Thunder can download and use a normal startup. Remember to set the path to save the downloaded file and then select the appropriate points of view the preservation of the path, or so similar to the set (z: \ root \ Desktop \) otherwise it will prompt the wrong path.

Tested, the speed of sensory and Windows under no difference.

Cheer:)

---

