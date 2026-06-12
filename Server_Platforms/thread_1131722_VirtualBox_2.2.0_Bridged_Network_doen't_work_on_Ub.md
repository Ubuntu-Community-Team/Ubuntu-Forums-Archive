---
title: "VirtualBox 2.2.0 Bridged Network doen't work on Ubuntu 8.10"
date: 2009-04-21
forum: Server Platforms
---

### Post by wolfteeth on 2009-04-21
Hello,

I read the docs and googling about my problem and i didn't find anything, so the moment has come to ask for help...

So i have a windows XP host and a Ubuntu guest. By setting a NAT network, it's working fine and get IP: 10.0.xx.x. 


After this i tried to set up a "real" network in my VM Ubuntu...
First with VirtualBox 2.2, i did a bridge network. 

[IMG]http://occhipin.free.fr/vbox/VMdebian1.JPG[/IMG]

Then that's the problem :
i don't get an ip adress form the dhcp.
I tried the same configuration on a windows guest and it worked perfectly.

but Ubuntu, eth0,eth1 does not appear in ifconfig, but **pan0** appear

I followed: [http://ubuntuforums.org/showthread.php?t=221768](http://ubuntuforums.org/showthread.php?t=221768)
and [http://ubuntuforums.org/showthread.php?t=698729](http://ubuntuforums.org/showthread.php?t=698729) 
I modified this file : /etc/udev/rules.d/70-persistent-net.rules
and put my adresseMAC in eth0 (and change the MAC adress in eth1)... and reboot...

anytime I changed the mac into eth0, it will auto add eth2, eth3, eth4, etc...faint....

I followed to change the 70 and 75 file, still with no luck.

deleted them and still no luck...

anyone who can help on this? thanks.

---

### Post by BkkBonanza on 2009-04-21
I don't have any specific info for your config but I wanted to say I used bridged with Ubuntu under Ubuntu host (in 2.2.0). It worked fine. I have found it's best to remove interfaces from the rules file and let it self-detect. Also as far as dhcp and getting an ip keep in mind that unlike nat mode (which VB handles it's own faked dhcp internally) in bridged mode the guest behaves like it's a new machine on your network and will have to be assigned by dhcp on your router or whatever handles it for your network. It sounds like it's not getting that far though as it needs to bring the interface up before it can even start dhcp.

Be sure to check interfaces with **ifconfig -a** as that will show interfaces that are down as well as up. You may know that but thought I'd mention it in case.

---

### Post by wolfteeth on 2009-04-22
ifconfig -a, eth0,eth1 does not appear in ifconfig, but pan0 appear

---

### Post by BkkBonanza on 2009-04-23
pan0 is your bluetooth.
Perhaps Ubuntu has no driver for the selected model Broadcom NetXtreme. Did you try other adapters as well? I think I have used it fine with PCnet Fast III adapter chosen.

---

### Post by wolfteeth on 2009-04-23
@BkkBonaza,

as talked I am installing this as a VM which doesn't have any bluetooth device. also I choosed any other Adapter for testing but with no luck at all....:(

> **BkkBonaza said:**
> pan0 is your bluetooth.
Perhaps Ubuntu has no driver for the selected model Broadcom NetXtreme. Did you try other adapters as well? I think I have used it fine with PCnet Fast III adapter chosen.

---

