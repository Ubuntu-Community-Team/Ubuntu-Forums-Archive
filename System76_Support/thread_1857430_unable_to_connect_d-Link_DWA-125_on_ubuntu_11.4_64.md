---
title: "unable to connect d-Link DWA-125 on ubuntu 11.4 64 bit."
date: 2011-10-10
forum: System76 Support
---

### Post by abhilashpujari on 2011-10-10
Hi ALL,
 
i am not able to connect d-Liink DWA-125 on ubuntu 11.4 64 bit.
 
i followed the below link but unable to connect, 
 
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)
 
i am able to connect the same for 32 bit ubuntu, only problem is with 64 bit....
 
 Please guide me on this issue :(....
 
 
 
 
regards
abhilash

---

### Post by WasMeHere on 2011-10-10
Check the compatibility of wireless cards for linux in the following link: [[COLOR="RoyalBlue"]_http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink_[/COLOR]]("http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")

The entry for your card is not very promising :-(

DWA-125, ralink, RT3070sta, No, Flaky, No Download, compile and install the native driver from source. Reportedly does not support WPA2. Installing Windows drivers (via ndiswrapper) reportedly fails. 2011-04-18 (Ubuntu 10.04)

It is listed as a USB device. Maybe you can give this one to a windows user and buy a new one with documented compatibility.

Maybe someone had luck with it and can describe to you how to use it?

Good luck
Olle

*Edit: Obviously the compatibility is catching up. Would it be an option for you to run 32-bit Ubuntu? Maybe someone can help fix an interface, so that use can use it in your 64-bit system :-)*

---

### Post by chili555 on 2011-10-10
> **abhilashpujari said:**
> Hi ALL,
 
i am not able to connect d-Liink DWA-125 on ubuntu 11.4 64 bit.
 
i followed the below link but unable to connect, 
 
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)
 
i am able to connect the same for 32 bit ubuntu, only problem is with 64 bit....
 
 Please guide me on this issue :(....
 
 
 
 
regards
abhilashPlease post:```
lsusb
lsmod | grep rt2
dmesg | grep rt2
```Thanks.

---

