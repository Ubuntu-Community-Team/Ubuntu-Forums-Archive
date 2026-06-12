---
title: "Ubuntu64-bit and VMware"
date: 2008-11-30
forum: Virtualisation
---

### Post by Arukas on 2008-11-30
I currently have Ubuntu (x86) and running windows as a guest os with VMware.

Here's something I've confused myself about?  In order to have more ram avaiable for VMware, If my host os is now Ubuntu64 (so i can have more ram), I'll have to install the 64bit version of VMware.  

My question is can I have a 32-bit guest-os on a system with a host-os of 64bits?

---

### Post by bodhi.zazen on 2008-12-01
Yes you can run a 32 bit guest on a 64 bit host.

---

### Post by Arukas on 2008-12-01
I have another question that need some light on it.

Now, the applications, I need windows to run, are the types that connect to the internet.  In order to get all the net functionality, I went from NAT to a bridge.

Now since I have connected windows to the internet and it can do more than just browse.  Common sense say's install a firewall and anti-virus.  Simple because I want xp to run more than a week at a time.

Is what I'm doing making sense?  Also, do I really need a firewall, since ubuntu is the host os?

---

### Post by bodhi.zazen on 2008-12-01
You need to think of your guests as equivalent to a physical machine in terms of security. Virtualization keeps the two OS separate and bridging your network card means your Windows box has it's own IP address.

So yes, you need antivirus / firewall / etc on the windows guest and no, running on an Ubuntu host does not "protect" windows in any way.

---

### Post by talofo on 2008-12-07
> **bodhi.zazen said:**
> You need to think of your guests as equivalent to a physical machine in terms of security. Virtualization keeps the two OS separate and bridging your network card means your Windows box has it's own IP address.

So yes, you need antivirus / firewall / etc on the windows guest and no, running on an Ubuntu host does not "protect" windows in any way.

Thanks. :)

---

### Post by dcstar on 2008-12-10
> **bodhi.zazen said:**
> 
........
So yes, you need antivirus / firewall / etc on the windows guest and no, running on an Ubuntu host does not "protect" windows in any way.

Well, if gives you a secure O/S to immediately use when you get sick of the usual Windows problems.......           ;-)

---

