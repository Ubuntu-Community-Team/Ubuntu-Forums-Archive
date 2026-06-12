---
title: "Airodump not recieving"
date: 2009-10-20
forum: Security
---

### Post by gabrielshier on 2009-10-20
Hey,
airodump-ng can see computers connected to networks but can't see networks. Even when it sees an AP or two it recives beacons but not data. 
Please help,
Gab

---

### Post by __p1n__ on 2009-10-20
The default curses* airodump-ng output is a list of AP's in whatever mode in the top window.  Any client nodes (associated or not) are displayed in the bottom window.

If you're seeing anything at all then it's working correctly and you're actually suffering from a performance as opposed to a functional condition.

Default remedies:

1. Upgrade the wifi driver - download and build it yourself for best operation.
2. Move the receiver around (get closer or get out from behind any obstruction.)
3. Change wifi interfaces. I'm currently using the patched ralink driver for both the built-in and usb plug-in wifi nic's on my laptop.  Same chipset but I can't get the built-in to inject whereas the plug-in** does injection perfectly (although I have to reset the driver after each run.) 




* I'm presuming that you're running airodump-ng from a shell and not analyzing the packet capture file with wireshark or somesuch.

** Linksys WUSB54GC

---

### Post by gabrielshier on 2009-10-22
Hey,
Thanks. Well, i don't quiet know how to manage linux drivers and devices. This device specifically did not need a driver since it supports linux so i just plugged it in and it works. 
Not using wireshark. The thing it that it worked last night for quiet a while but now it does not work again. Seems as if i leave it long enought connected to the computer it will start working...

---

