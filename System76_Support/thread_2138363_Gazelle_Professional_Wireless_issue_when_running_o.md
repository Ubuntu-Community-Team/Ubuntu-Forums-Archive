---
title: "Gazelle Professional Wireless issue when running on battery"
date: 2013-04-23
forum: System76 Support
---

### Post by jdwaugh on 2013-04-23
I purchased a Gazelle Professional last december with the Intel Centrino 1030 wireless card. Very happy with laptop but I have been having a really odd issue with the wireless card. 

When the laptop is plugged in I can stream movies and things run just fine, but if I am running on battery power the video stream is very jumpy like instead of maintaining the stream it will download a couple of seconds worth then stop then use up the buffer and download another few seconds . So the stream is completely unwatchable. Hoever, if while it is doing that I plug in the power cable then it starts playing smoothly.

Is this a power saving feature in the dafulat setup from System76? If so how do I change it so that I can watcfh stream without having the laptop plugged in. Similarly it seems like browsing the web is slower when it is running on batter power.

---

### Post by isantop on 2013-04-24
Thanks for bringing this up. We have identified that certain power-management routines on the Intel cards can negtaively affect Wireless performance. We have included a fix in the next version of the System76 Driver, which will be released with 13.04 tomorrow.

---

### Post by freechelmi on 2013-04-30
Just to explain the solution as this problem happen on all intel wifi cards. 

When you go on battery the power-saving mode of the wireless is activated by default and it's awfully bad.

I've made a simple deb which disable power saving (via iwconfig)  when the cord is plugoff : [http://support.ekimia.fr/utilities/Wifi-power-fix/](http://support.ekimia.fr/utilities/Wifi-power-fix/)


@isantop : I guess you made the same technical choice ?

---

