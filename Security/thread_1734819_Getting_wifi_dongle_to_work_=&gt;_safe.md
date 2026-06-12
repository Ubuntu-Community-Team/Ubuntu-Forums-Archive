---
title: "Getting wifi dongle to work =&gt; safe?"
date: 2011-04-20
forum: Security
---

### Post by xic816 on 2011-04-20
Just got a wifi dongle; [http://www.dealextreme.com/p/usb-54mbps-802-11b-g-wifi-lan-adapter-with-detachable-antenna-24886](http://www.dealextreme.com/p/usb-54mbps-802-11b-g-wifi-lan-adapter-with-detachable-antenna-24886) 

In one of the discussions about driver/support for linux this was stated;

Go to terminal. Type "sudo gedit" it will ask for your password. Once in  the text editor click open file, then browse to the root directory then  the "etc" folder then the "modprobe.d" folder then open the file called  "blacklist.conf" go to the very bottom of the text file and add two  lines "blacklist rt2800usb" and "blacklist rt2970sta", then save the  file. Restart and TADA! it'll work

What exacly is happening/being done here? O.o

Thanks

---

### Post by bodhi.zazen on 2011-04-21
You are configuring what modules your kernel is loading, or in the case of blacklisting, preventing your kernel from loading a conflicting driver.

The linux kernel has the hardware drivers, they can either be built in, or accessed "on demand" or as needed as modules.

Tons of information about the linux kernel is available, see:

[http://www.freeos.com/articles/4051/](http://www.freeos.com/articles/4051/)

---

