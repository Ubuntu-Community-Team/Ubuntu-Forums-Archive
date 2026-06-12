---
title: "Bridging VLANs"
date: 2013-06-20
forum: Server Platforms
---

### Post by proteus4 on 2013-06-20
Hi guysI've recently set up an Ubuntu Server 12.04 build for the company I work for to used as a FOG imaging server.  When tested we have been able to successfully multicast an image but we have now moved the server to another site that has multiple VLANs set up on our Cisco switches.  Multicasting no longer works.  I have spoken with our Data Centre guys and they confirm that the Cisco switches are set up for multicasting etc so it's not that which is causing the problem.After some reading up on the subject it seems that I need to set up VLAN in my network settings.  So here's what i'm looking to do (if i'm completely off mark then im happy to hear what I should be doing):-* The server is patched into a port on the switch that has access to all 3 VLANs that I need to multicast to* Set up 3 VLANs tagged as 204, 208 and 212* Bridge these 3 VLANs so that when I send out a multicast it sends them across all 3 VLANs* Maintain the current static IP of the server on eth0                                    ----->eth0.204 (vlan)                                    |eth0-------> br0-------->eth0.208 (vlan)                                    |                                    ----->eth0.212 (vlan)I hope this makes sense :o)Paul S

---

### Post by Vitsliputsli on 2013-06-21
> [COLOR=#000000]I need to set up VLAN in my network settings[/COLOR]
1. Load module:
modprobe 8021q

2. Create VLAN:
vconfig add eth0 204

3. Up vlan and configure it:
ifconfig eth0.204 up

---

### Post by hawkmage on 2013-06-21
Vitsliputsli: That works to bring up those interfaces manually but they will go away when you reboot.

proteus4: For the VLAN config to be permeant you may want to follow the instructions here: [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

---

### Post by Vitsliputsli on 2013-06-21
Yes, but before use permanent config, it's need to try start manually for check. Only after that add work configuration to boot scripts.

---

### Post by hawkmage on 2013-06-21
I agree that you should do the modprobe 8021q before proceeding but I usually like to edit the /etc/network/interfaces and then use the ifup command to bring the interface up.  That way you know that the interfaces file syntax is correct.

---

### Post by Vitsliputsli on 2013-06-22
I always do manually at first for sure it's all work. In this case I see effect immediately, and know work or not.
But it's youself choice.

---

