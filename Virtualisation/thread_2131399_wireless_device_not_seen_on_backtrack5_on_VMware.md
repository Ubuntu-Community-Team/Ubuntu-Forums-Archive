---
title: "wireless device not seen on backtrack5 on VMware"
date: 2013-04-01
forum: Virtualisation
---

### Post by dany01 on 2013-04-01
Hey there, 
i have been working on this for the past 2 weeks but not resolve yet. i'm using ubuntu 12.04 and i install backtrack 5 on a vmware. the problem is that my backtrack doesn't not see any wirelss device . i try read across the internet and apply a couple command . but nothing  can someone help me  fix this . 
couple command that will help: 
eth0  up
iwconfig  : display only eth0 not wlan0
dhclient eth0
 wlan0 up or wlan0 mode manager : display error no such device

---

### Post by AndyOpie150 on 2013-04-01
can you plaese post the out put of these commands:
```
lspci
```
```
ifconfig
```
```
lsmod
```
And if the wireless is an external card or USB device then;
```
lsusb
```

---

### Post by QIII on 2013-04-01
[I]Moved to [B]Virtualisation.


[/B][/I]Generally , discussions of other OSes are moved to their own section of the forums.  In this case, however, the question is not about the OS itself.

---

### Post by layers on 2013-04-01
Do the brute force, no-thinking required method: load a live CD to see if it works, so we know where the problem is. If it works there, it's in visualization.

---

### Post by kungfupete on 2013-04-02
dany01:  I just spent a significant amount of time trying to accomplish the same thing about a month ago.  After much research, it appears that you cannot interact directly with the onboard wireless devices this way.  Emulation/bridging for wireless will only appear as a standard LAN port (eth0, etc) inside the VM. 

The way I got around this was simple and works really well:  I bought a USB wireless device and it DOES recognize that as long as you configure the VM as such to access host USB devices (I was using Virtual Box at the time).  The model I purchased was an Alfa USB high gain/high power long-range which was fairly cheap and works really well.

Disclaimer:  I certainly may be wrong about the above, and would love if somebody would tell me otherwise. However I spent ALOT of time trying to make this happen to no avail.

Edit: KB from VMware confirming above:  [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1005256](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1005256)

---

