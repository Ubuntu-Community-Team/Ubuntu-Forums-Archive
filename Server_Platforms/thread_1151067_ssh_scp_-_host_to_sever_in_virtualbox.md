---
title: "ssh scp - host to sever in virtualbox"
date: 2009-05-06
forum: Server Platforms
---

### Post by pantone186 on 2009-05-06
Hello,

I'm struggling to copy a directory over from my ubuntu host to a ubuntu server in virtualbox.

following command dosen't work, connection refused.


sudo scp -r /media/disk/wordpress user@localhost:22:/var/www


nmap on ubuntu-server gives a warning - Hostname localhost resolves to 2 IPs. Using 127.0.0.1.


not sure where i'm going wrong here. any help would be much appreciated.

---

### Post by EXCiD3 on 2009-05-06
check in your guest OS what your IP is first. localhost from your host os will point to that os, not your virtual machine.

---

### Post by pantone186 on 2009-05-06
not sure how to check what the guest os ip is?


I can connect via ssh to the guest using $ ssh -l <user> -p 2222 localhost

---

### Post by albinootje on 2009-05-06
> **pantone186 said:**
>  sudo scp -r /media/disk/wordpress user@localhost:22:/var/www


Are you using NAT for the guest VM or "bridged" with the host interface ?
With NAT the guest will have a 10.0.2.x ip address from within VB.
When bridge is in use it will get an ip address by DHCP from your LAN.
Please check the ip address inside the guest VM.

---

### Post by pantone186 on 2009-05-06
it's using nat with port forwarding.

I thought the 10.0.2.2 was for accessing host from within the guest?


How do I check the ip inside the guest vm?

---

### Post by albinootje on 2009-05-06
> **pantone186 said:**
> it's using nat with port forwarding.

I thought the 10.0.2.2 was for accessing host from within the guest?

How do I check the ip inside the guest vm?

Yes, 10.0.2.2 is the host ip address within NAT on VirtualBox (and also on Qemu).
Try "ifconfig" inside your guest VM.

---

### Post by pantone186 on 2009-05-06
ifconfig gives 

eth0 10.0.2.15

and

local loopback 127.0.0.1

---

### Post by albinootje on 2009-05-06
> **pantone186 said:**
> 
eth0 10.0.2.15


Okay, does it work with that ?

---

### Post by pantone186 on 2009-05-06
no, unfortunately, the terminal just seems to hang

---

### Post by albinootje on 2009-05-06
> **pantone186 said:**
> no, unfortunately, the terminal just seems to hang

In the past I had much better luck with "bridged" vs. NAT in VirtualBox.
NAT would work fine for the guest, but from the host to the guest I had problems afair.
So, if no one else can offer you a better solution, and if it's OK for you, use "bridged" to host interface in VB instead, giving the guest VM its own ip address.

---

### Post by pantone186 on 2009-05-06
Yes I think your right I've just been reading up on that. Looks a little harder to set up for a beginer, but never-the-less ill give it a go, it's all a good learning experience.

And thanks for the help Albinootje

---

### Post by albinootje on 2009-05-06
> **pantone186 said:**
> Yes I think your right I've just been reading up on that. Looks a little harder to set up for a beginer, but never-the-less ill give it a go, it's all a good learning experience.

VirtualBox has bridge support build in since a while, since VirtualBox version 2.1 :
[http://www.dedyisn.net/2009/02/new-feature-virtualbox-21-bridging-in-virtualbox-automatically/](http://www.dedyisn.net/2009/02/new-feature-virtualbox-21-bridging-in-virtualbox-automatically/)

* New Host Interface Networking implementations for Windows and Linux hosts with easier setup (replaces TUN/TAP on Linux and manual bridging on Windows)
> 

And thanks for the help Albinootje

No problem.

---

