---
title: "Remote Access to KVM Machine"
date: 2013-03-05
forum: Virtualisation
---

### Post by daz1uk on 2013-03-05
OK,

I have an Ubuntu 12.04 Server which is running KVM with a Windows 7 VM, I can ping Windows 7 from the host and if I go into windows 7 networking it has an assigned IP, connects to the internet fine, etc etc. 

How can I connect to this VM from my ubuntu laptop over my network please?

---

### Post by sanderj on 2013-03-05
Does [https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking](https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking) help?

---

### Post by daz1uk on 2013-03-05
> **sanderj said:**
> Does [https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking](https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking) help?

Yeah, maybe I'm just being thick or something, I have been using that but can;t figure it out, maybe try again after some sleep.

The thing is I can access the kvm client form the host with "vncviewer localhost:0" no problem, so in theory surely, I should be able to do it across the lan with vncviewer 192.168.1.10:0??

I can also ping all other connections on my network from the KVM client. Huh?

---

### Post by daz1uk on 2013-03-05
For anyone that managed to miss the step of installing virt-manager to your remote pc like I did, this is how I solved my problem.

---

### Post by dreamgear on 2013-03-05
> **daz1uk said:**
> 

The thing is I can access the kvm client form the host with "vncviewer localhost:0" no problem, so in theory surely, I should be able to do it across the lan with vncviewer 192.168.1.10:0??


Do "netstat -anp | grep kvm | grep LISTEN".  With libvirt at least, it listens only on 127.0.0.1 by default, and on ports 5900 and up.  You have to tell it to listen on 0.0.0.0 so you can connect to it from vnc clients on other systems.

---

