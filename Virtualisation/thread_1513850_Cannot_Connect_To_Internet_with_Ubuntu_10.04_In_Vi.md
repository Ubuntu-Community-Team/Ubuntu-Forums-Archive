---
title: "Cannot Connect To Internet with Ubuntu 10.04 In VirtualBox"
date: 2010-06-20
forum: Virtualisation
---

### Post by alec100 on 2010-06-20
I am not sure if this is the right section for this, if it is not please move it. I am new here and also new to the whole concept of Linux. I have Installed Ubuntu 10.04 in VirtualBox and it appears to be working fine but no matter what I do I cannot connect to the Internet. I also have Windows XP running in VirtualBox and this connects to the Internet fine using the bridge connection setting and by choosing the adapter I use on my host PC. If I do this under Ubuntu however it will not appear to recognise the Adapter. My Host PC is Windows 7 32-Bit and I use a Netgear WG111v3 Wireless adapter to connect to the Internet. Using Host only adapter won't work as my adapter is a USB one and does not use an ethernet port. I tried Bridging teh Virtualbox adapter and the Netgear adapter together in Windows so the VirtualBox one had internet access however I still couldn't connect. I have even located the Windows Drivers for the Netgear WG111v3, accessed them through Ubuntu and used ndis wrapper to install the driver however it says hardware not present no matter what I do. Someone please help me. 

*Edit* I can also connect to the Internet using the same method I use for XP in Google Chrome OS (Beta)

*Edit* After Setting up the virtual Machine again, using the same hard drive I was able to connect through NAT. On all my Virtual OS's. This Issue is now Resolved.

---

