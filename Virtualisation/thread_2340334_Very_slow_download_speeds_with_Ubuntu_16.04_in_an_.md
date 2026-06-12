---
title: "Very slow download speeds with Ubuntu 16.04 in an Oracle VM VirtualBox"
date: 2016-10-17
forum: Virtualisation
---

### Post by mermaidman on 2016-10-17
I installed Ubuntu 16.04 in an Oracle VM VirtualBox on windows.  It works well except when I try to watch a video on youtube the download speed is extremely slow.  In windows the download speeds are still much faster.  How do I fix this?

---

### Post by ajgreeny on 2016-10-17
What network settings are you using in the guest VM, NAT or bridged?

What speed info do you get if you go to speedtest.net.?
I use bridged network connection in my VMs, of which I have 6 different OSs, 5 Linux and 1 WindowsXP, all of which give me the same speed as my host OS, 36 or 37Mb/s, very close to the 38Mb/s which is my theoretical top speed.

Do you have the correct guest extensions pack installed?  I'm not sure they actually make a difference to networking, but are worth installing for many other reasons.

---

### Post by mermaidman on 2016-10-17
How do you check the network settings?

I tried speedtest.net and it got stuck on finding a server.

How do you check which guest extensions you have?

---

### Post by howefield on 2016-10-18
Thread moved to the "*Virtualisation*" forum.

---

### Post by ajgreeny on 2016-10-18
With the VM not running go to Settings in the VBox-manager window and you will see a lot of things that can be changed including network settings.

Both NAT and bridged work fine in my VMs but I want an IP direct to the router for a number of reasons including mediaserver installations on some VMs I use.

If speedtest could not find a server you obviously have a problem with networking; what does **ifconfig** in terminal of your VM give you as output?
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

