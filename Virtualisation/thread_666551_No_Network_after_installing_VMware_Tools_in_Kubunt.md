---
title: "No Network after installing VMware Tools in Kubuntu 7.10 + VMware Fusion"
date: 2008-01-13
forum: Virtualisation
---

### Post by Jackster on 2008-01-13
Hey, I just installed Kubuntu 7.10 into a VM on my Macbook. The networking works fine up until I install VMware Tools at which point all the other VMware Tools things work like window resizing etc, but the networking then seems to disappear. I get a little picture in the bottom left of my screen with an unplugged cable and a little cross. 

It's wierd because I've used Kubuntu 7.10 in VMware Fusion before and never had any problems with VMware Tools.

I've tried uninstalling and reinstalling Kubuntu but no joy, any ideas?

---

### Post by tedstreete on 2008-01-20
[LIST]
[*]Go into System->Administration->Network.  
[*]Click the Properties Button for the eth0 adapter, uncheck "Enable Roaming Mode" and ensure that the drop-down is set to DHCP.  
[*]Reboot. 
[*]Go back into System->Administration->Network and ensure that the interface is enabled (there should be a check mark in the box on the left in the Connections Tab.
[/LIST]

---

### Post by brutimus on 2008-03-19
Thanks!  I had to do an ifdown/ifup after my reboot to finally get it to take, though.  Not sure why, but it works now.

---

### Post by Tech^CF on 2008-03-27
Thanks, this helped me.


No need to reboot though. I unchecked roaming and set the mode to DHCP, checked the checkbox for wired connection so that the wired connection is enabled. The network connection appeared in ifconfig. I then ran "sudo dhclient eth0" and the connection was working.

---

### Post by toors on 2008-04-24
Great!! This helped me too.

For all the newcomers here: Don't forget the checkbox in front of "wired connection"!! (system->administration->network, checkbox)

No need to reboot, just: "sudo ifdown eth0" (or whichever you use) and then: "sudo ifup eth0" 

There you go!!

---

### Post by Geekkit on 2008-05-11
> **tedstreete said:**
> [LIST]
[*]Go into System->Administration->Network.  
[*]Click the Properties Button for the eth0 adapter, uncheck "Enable Roaming Mode" and ensure that the drop-down is set to DHCP.  
[*]Reboot. 
[*]Go back into System->Administration->Network and ensure that the interface is enabled (there should be a check mark in the box on the left in the Connections Tab.
[/LIST]

Thank you for this! This was exactly what I needed. I could access the network via XP within the VM but not within Ubuntu. Thanks guy!  :)

---

