---
title: "Convert Cent OS server to Ubuntu"
date: 2011-11-28
forum: Server Platforms
---

### Post by alex.rayu on 2011-11-28
We have a dedicated server that came initially with Cent OS 5. It's a clean install, we have nothing there yet. We want to have it switched to Ubuntu Server. We have no physical access to it. Is it possible to do through SSH?

---

### Post by volkswagner on 2011-11-28
I don't believe this is possible.  

Does the server have hardware to support running VirtualMachines?  How much RAM does it have?  What do you plan on running on the server?  

Perhaps you can run CentOS as the host and run Ubuntu in a VM using KVM or VirtualBox, or other HyperVisor.

---

### Post by arrrghhh on 2011-11-28
If you have some sort of DRAC, iLO, etc - some remote access to the box that is out-of-band, then it is possible.

Otherwise, no - you'll need someone to at least put in the CD/DVD for you, plus the initial configuration to get back in with SSH.

So out-of-band management, or remote hands.  Those are the only ways I could think of achieving this.

---

### Post by collisionystm on 2011-11-28
> **alex.rayu said:**
> We have a dedicated server that came initially with Cent OS 5. It's a clean install, we have nothing there yet. We want to have it switched to Ubuntu Server. We have no physical access to it. Is it possible to do through SSH?

Is there any particular reason you are trying to switch?
CentOS makes a nice server.

---

### Post by hawkmage on 2011-11-28
It is possible but almost imposable to do successfully.  You would not be able to use the standard installer, you have to do most of the steps of building the boot filesystem and the supporting packages manually.  

I second the question collisionystm aasked, why do you want to switch Linux distros?

---

### Post by alex.rayu on 2011-11-29
We are using CentOS 5 for tangodemon.com. And it fails to match libraries at all. We have had a lot of problems with it, and indian server admins also. My research in internet indicates, that Ubuntu server has a better library base and more support these days. No mistmatched version libraries will be installed. We are considering switching to Ubuntu.

---

### Post by collisionystm on 2011-11-29
> **alex.rayu said:**
> We are using CentOS 5 for tangodemon.com. And it fails to match libraries at all. We have had a lot of problems with it, and indian server admins also. My research in internet indicates, that Ubuntu server has a better library base and more support these days. No mistmatched version libraries will be installed. We are considering switching to Ubuntu.

Oh. I thought you said in your first post it was a clean install.

Regardless I assume you are paying to have this server hosted somewhere? You will probably just need to pay for a hosted Ubuntu Server, move your stuff over and cancel the centos. You can have a server hosted directly from canonical.

---

