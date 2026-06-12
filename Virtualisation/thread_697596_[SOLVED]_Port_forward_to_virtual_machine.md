---
title: "[SOLVED] Port forward to virtual machine"
date: 2008-02-15
forum: Virtualisation
---

### Post by darkline on 2008-02-15
Hi,
I have installed XP on vmware, it is set up with an internet connection that works fine as does file sharing between ubuntu and the virtual XP.
However i have a problem with a program that requires portforwarding.
On a real XP all i would do is forward from my router to XP but how do i do it when XP is virtual?

What i need is for it to be forward firsst from my router to ubuntu then on to the virtual xp 
Or for it to got straight from the router to XP (the problem with this is the IP of XP is not in the range that my router gives out for some reason)

How do i go about doing this? I have seen a few things but i dont really understand.
Thhanks

---

### Post by dcstar on 2008-02-16
> **darkline said:**
> Hi,
I have installed XP on vmware, it is set up with an internet connection that works fine as does file sharing between ubuntu and the virtual XP.
However i have a problem with a program that requires portforwarding.
On a real XP all i would do is forward from my router to XP but how do i do it when XP is virtual?

What i need is for it to be forward firsst from my router to ubuntu then on to the virtual xp 
Or for it to got straight from the router to XP (the problem with this is the IP of XP is not in the range that my router gives out for some reason)

How do i go about doing this? I have seen a few things but i dont really understand.
Thhanks

You port forward to the "Virtual" IP address of the VM - the base system running VMware should (in theory) forward the packets from the real address (if it didn't the VM would not have network access).

---

### Post by popch on 2008-02-16
> **darkline said:**
> the problem with this is the IP of XP is not in the range that my router gives out for some reason

There are several ways to configure the virtual NIC of the virtual machine. The two more prominent ones are 'bridged' or 'NAT'. 

The way you describe your problem appears to indicate that you use NAT to access the LAN and whence the LAN with your virtual XP machine. With NAT your virtual machine 'hides behind' the IP address of the host machine. The virtual machine itself thinks it has an entirely different IP address.

Since your router should send all traffic to your XP machine which is addressed to a particular port, your XP machine (rather, its IP address) must be visible to the router. Hiding it behind the Ubuntu machine's IP address will not work.

Therefore, you should use a 'bridged' NIC for your XP machine instead of NAT.

Power off your virtual machine, go in VMWare to the configuration editor for this machine, change the NIC's setting from NAT to bridged.

---

### Post by darkline on 2008-02-20
sry for the late reply but thanks very much.it all works perfectly now

---

### Post by popch on 2008-02-21
Cheers. Good show.

Please mark your thread as 'solved', then.

---

