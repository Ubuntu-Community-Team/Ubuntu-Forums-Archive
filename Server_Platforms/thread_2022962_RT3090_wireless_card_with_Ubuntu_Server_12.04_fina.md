---
title: "RT3090 wireless card with Ubuntu Server 12.04 finally working"
date: 2012-07-11
forum: Server Platforms
---

### Post by terminal27 on 2012-07-11
I have tried for a few days to install Ubuntu Server 12.04 on a fit-pc2 with RT3090 wireless card. While at installation time it seems recognize the card after booting fail to load the module (for interference with rt2800 and rt2x00 and because can't find rt3090 module to install).
This is what I did (probably I missed some steps after pulling my hair out for a week, sorry):
 
1.-Install Ubuntu with the wired card option (as you will need internet access)
2.-install python-software-properties as you will need add-apt-repository
3.-install dkms
4.-sudo add-apt-repository ppa:markus-tisof/rt3090
5.-apt-get update
6.-sudo apt-get install dmks rt3090-dkms (for some will fail like me but could work for others)
7.-sudo nano /etc/modprobe.d/blacklist.conf and add:
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
 
(keep in mind that in another installation with same card I actually had to comment out those blacklist)
 
8.-sudo add-apt-repository ppa:marko-technytalk.info/ralink-wireless (i understand there is a rt3590-dkms that cover rt3090 as well)
9.-sudo apt-get install rt5390-dkms
10.- if still fails to install this one then manually download the package xxxxxxx.deb from markus-tisof and then
11.- sudo dpkg -i xxxxxxx.deb
And finally
12.- sudo shutdown -r now 
And good luck. Mine worked (But I am not sure which one did it or if all of them).
 
Before shutdown make sure you edit
sudo nano /etc/network/interfaces
and comment out
#auto eth0 blablabla...
#iface...blablabla..
 
#and add:
 
auto wlan0
iface wlan0 inet dhcp
wireless_mode Managed
wireless_essid yourESSID #I have open but you could add a password
wireless_channel auto
wireless_rate 54G
 
That's all in my case as I don't want eth0
Good luck and hope it helps someone else! (A week of pain....)

---

### Post by terminal27 on 2012-07-14
I found that for some installations the wlan0 will change to wlan1, or even ra0, so I recommend:
sudo lshw -C network and find out the hardware logical name, and update the /ect/network/interfaces accordingly.

---

