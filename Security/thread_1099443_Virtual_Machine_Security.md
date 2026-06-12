---
title: "Virtual Machine Security"
date: 2009-03-18
forum: Security
---

### Post by WatchingThePain on 2009-03-18
Hi,

Does anybody know..

Say for some reason I installed an OS in virtualbox.
Suppose that that OS was something like windows.
If the windows gets a virus, can that virus leave the Virtualbox and cause problems on the host OS (Linux), or is virtualbox like a fully contained sandbox?.

---

### Post by tribaal on 2009-03-18
In short: No.

VMs are fully sandboxed, as far as virus goes. There might be exploitable bugs in the hypervisor, but that's quite unlikely.

- Trib'

---

### Post by WatchingThePain on 2009-03-18
Thank you for that tribaal.

---

### Post by Nxion on 2009-03-19
> **tribaal said:**
> In short: No.

VMs are fully sandboxed, as far as virus goes. There might be exploitable bugs in the hypervisor, but that's quite unlikely.

- Trib'

I kinda agree and disagree with this. While your are kinda right. It would also depend on how he had the networking setup in Virtualbox? Was it setup as host networking or bridged? The difference is on host networking it really doesn't go anywhere, it is kinda like its own separate virtual LAN. 

If it was bridged, then this mean that the virtual machine is acting like its own computer. I mean that it has its own IP address from the router. The problem with this is that if this virus came over the internet, it is possible that it could be spread over the network to other computers. I know that Ubuntu wont be affected but if you have other Windows machine, then it is possible that they can be affected.

---

### Post by marco123 on 2009-03-19
> **WatchingThePain said:**
> Hi,

Does anybody know..

Say for some reason I installed an OS in virtualbox.
Suppose that that OS was something like windows.
If the windows gets a virus, can that virus leave the Virtualbox and cause problems on the host OS (Linux), or is virtualbox like a fully contained sandbox?.

See my thread: [http://ubuntuforums.org/showthread.php?t=1100531](http://ubuntuforums.org/showthread.php?t=1100531)

I'm trying desperately to infect my XP virtual machine and I just can't do it.:(  I don't know if it's because it's a virtual machine running on top of linux, or if my Router's firewall is killing my dream?

Cheers, Marco.

---

### Post by dacorr on 2009-03-19
Nxion is correct in  the term that a virtual machine is not protected from viruses that propagate through networks, they can get infected like anyother computer. however direct infection from guest os to host os would be unlikly unless the virus specifcally targeted the virtual machine control software. There are hidden back doors in VM but they require user action.

It would be likely to obtain a virus from a network share or removeable media

Dac

---

