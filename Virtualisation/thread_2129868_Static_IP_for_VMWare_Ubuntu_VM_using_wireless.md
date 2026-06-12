---
title: "Static IP for VMWare Ubuntu VM using wireless?"
date: 2013-03-27
forum: Virtualisation
---

### Post by mjremijan on 2013-03-27
I am running a windows 8 machine with VMWare running an Ubuntu VM. This machine also exclusively access the network via Wireless. I am using a VMWare bridged connection and when both the host and vm are running they get distinct IP addresses from my router like they should. However, when I login to my router I see in the attached devices list that the router sees both host and vm as the same MAC address. After much online research, I found this is a known issue with a wireless connection. What I am looking for is if anyone has been successful working around this problem to effectively give the Ubuntu VM a static IP address because getting a reliable IP address for the Ubuntu VM is critical for my work.  Since I can't get the router to hand out a static IP, is there  a way to do this in the Ubuntu VM; set the IP and other networking properties statically?

---

### Post by dcstar on 2013-03-28
> **mjremijan said:**
> I am running a windows 8 machine with VMWare running an Ubuntu VM. This machine also exclusively access the network via Wireless. I am using a VMWare bridged connection and when both the host and vm are running they get distinct IP addresses from my router like they should. However, when I login to my router I see in the attached devices list that the router sees both host and vm as the same MAC address. After much online research, I found this is a known issue with a wireless connection. What I am looking for is if anyone has been successful working around this problem to effectively give the Ubuntu VM a static IP address because getting a reliable IP address for the Ubuntu VM is critical for my work.  Since I can't get the router to hand out a static IP, is there  a way to do this in the Ubuntu VM; set the IP and other networking properties statically?

If you want a Static IP address then simply set that up in the Ubuntu VM. This has nothing to do with the Virtual environment, it is basic networking.

---

