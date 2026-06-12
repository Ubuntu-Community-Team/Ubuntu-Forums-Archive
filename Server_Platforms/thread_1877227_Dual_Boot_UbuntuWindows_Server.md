---
title: "Dual Boot Ubuntu/Windows Server?"
date: 2011-11-07
forum: Server Platforms
---

### Post by jacknet52 on 2011-11-07
Is it possible to load a dual boot Ubuntu Server in one part with a Windows Server on the other part? I have a Pentium D with 2gb memory and 80 gb hd. I have already 1 machine with a dual boot Ubuntu 11.10 and Win7. Is the install similar? Do I have enough space and power? This is for training only. Maybe 5 nodes at most. Thanks much.

---

### Post by collisionystm on 2011-11-07
> **jacknet52 said:**
> Is it possible to load a dual boot Ubuntu Server in one part with a Windows Server on the other part? I have a Pentium D with 2gb memory and 80 gb hd. I have already 1 machine with a dual boot Ubuntu 11.10 and Win7. Is the install similar? Do I have enough space and power? This is for training only. Maybe 5 nodes at most. Thanks much.

Here is what I would do.......

See if you can throw some more memory in that box. 4gb would be nice.

You have a 'D' CPU so it can do 64 bit.

Install Ubuntu as the main OS. Run Server 2003 and Other Ubuntu's in KVM.

Server 2003 is very lightweight and should only need 256 mb of ram in a virtual enivronment. Virtual memory and hard drive paging files work at the speed of light in a virtual environment. Its just when you start messing with I/O APIC that things get ugly.

Ubuntu Server should do find with 256mb of ram as well.

---

### Post by arrrghhh on 2011-11-07
You can dual-boot Windows Server and Ubuntu Server.  The above recommendation on virtualization would be the better method, unless you need to have it on physical hardware.

---

### Post by jacknet52 on 2011-11-07
Good stuff you guys. Looked up KVM on wiki and rapidly got lost. So you're saying I can run a cloud with Ubuntu 11.10 or some such version and run Win 2003 and Ubuntu server in a cloud on that? I'm really just trying to learn about servers and their hardware/software for networking.

---

### Post by arrrghhh on 2011-11-07
> **jacknet52 said:**
> Good stuff you guys. Looked up KVM on wiki and rapidly got lost. So you're saying I can run a cloud with Ubuntu 11.10 or some such version and run Win 2003 and Ubuntu server in a cloud on that? I'm really just trying to learn about servers and their hardware/software for networking.

KVM is a little more hardcore as far as virtualization suite's go.

Look at VirtualBox - IMHO this is the easiest virtualization suite to use.

But what the previous poster was talking about is simply virtualization, nothing about the cloud.

---

### Post by collisionystm on 2011-11-07
Use 10.04 LTS as a server.
If you want to do KVM just choose Virtualization platform during the install prompts.
Once its installed, log onto your ubuntu desktop
install virt-manager from the software center

run the program and point it to your server using QEMU/KVM

You now have a gui for adding your OS. Its actually really easy.

Virtualbox is good too. Personally I always need a gui for this stuff

---

### Post by jacknet52 on 2011-11-07
Thanks again guys for taking the time to respond. I'll let you know what I end up doing. Fortunately I have a Linux guru at work but I wanted to get a second opinion. Just like going to the doctor and finding out he wants to do something major. This is major to me and I need all the help I can get. Keep the coffee pouring. :D

---

