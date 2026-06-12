---
title: "Please help me - cannot connecting to enternet"
date: 2016-01-03
forum: Ubuntu/Debian BASED
---

### Post by mohammad22 on 2016-01-03
hello every one...
i cannot speak english well , am from spain
i have a little problem on my elementary OS ferya.
I cannot connect to enternet, also i dont have eithernet to install drivers for my wireless network.
My wireless network info is...

BCM4313 802.11bgn wireless network adapter

am new on linux , and i dont have eithernet and wireless.
what should i do step by step to install wireless driver on my elemntary?
no enternet ... no eithernet ... no wireless :( :(

---

### Post by Bucky Ball on 2016-01-03
*Thread moved to **Ubuntu/Debian Based**. *

Welcome. ElementaryOS is not an officially supported flavour here and therefore not supported in the main areas. Good luck. :)

---

### Post by Elishasmantle on 2016-01-03
Hello,

Try this:
you will need to see if you have an editor in your OS install. Maybe gedit or vi.

from terminal:
sudo vi /etc/network/interfaces
type password when prompted and then it will open file

At the top of the file it should have this entry, if not put it in.

#Loopback Config
auto lo
iface lo inet loopback

Save changes, reboot to file and see if you have a wired internet connection at that point.

report back if that worked. If it did, you can go from there to fix any additional issues.

It would be best if we knew what was already listed in your interfaces file, hate flying blind here. :(
Post contents first if you can.

---

### Post by mohammad22 on 2016-01-03
Thanks for reply , but i didnt found any thing , also i wrote these commend in terminal nothing happen :(  it says command not found did u mean ....

---

