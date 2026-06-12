---
title: "How to get Rosewill RNX-EasyN1 to work with Ubuntu 10.04"
date: 2010-08-25
forum: Tutorials
---

### Post by metalf8801 on 2010-08-25
I did not come up with this How to but it works. I found it in the reviews on [http://www.newegg.com/Product/Product.aspx?Item=N82E16833166041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166041)
I'm posting it here so its easer to find

this applies to the Rosewill RNX-EasyN1 IEEE 802.11b/g/n USB 2.0 Wireless-N 4.0 Dongle (1T1R) 

this was posted by Perl Monkey Bill on Newegg Customer Reviews 
"If using with Ubuntu 10.04 there are two things you need to do.

1. Apparently Ubuntu 10.04 (the newest kernel) is presently having incompatibility issues with WPA (1), so to use this authenticate properly with your router you will have to set your wireless router to WPA2 ONLY (NOT WPA/WPA2 mode). Research on www dot ubuntuforums dot org or launchpad dot net slash ubuntu for updates to check if this has been resolved.

2. You have to blacklist the re2800usb driver in ubuntu (the wrong driver is claiming this hardware in the OS). To do this:
1. Open terminal
2. Type:
sudo gedit /etc/modprobe.d/blacklist.conf
Then a gedit viewer will open
3. At the bottom of the file add a line:
blacklist rt2800usb
4. Save/Exit the conf file.
5. Reboot

I have used this on 4 wildly varying hardware platforms running Ubuntu and it has worked every time."

I hope this helps you 
Dan

---

### Post by ianbrown75 on 2010-09-24
nm

---

### Post by virago81 on 2013-01-03
Just so everyone knows: I just plugged in the Rosewill RNX-EasyN1 to an Ubuntu 12.04 machine and it works like a charm.  No need to go through the steps that were previously needed to get it to work with 10.04.

Cheers!

---

