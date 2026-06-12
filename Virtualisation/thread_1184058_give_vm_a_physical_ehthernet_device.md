---
title: "give vm a physical ehthernet device?"
date: 2009-06-10
forum: Virtualisation
---

### Post by armstrtw on 2009-06-10
Our server has several ethernet ports.  Is it possible to give a virtual machine exclusive access to one of the ethernet ports?

My first attempt was to set up eth0 as the device for the host with a static ip, and to set up eth1 in a bridge which I could use as the device for all the vm's that were hosted on that machine.  However, having both devices up caused quite a lot of routing issues for outgoing connections on the machine.

Does anyone know the proper steps to give a virtual machine exclusive access to an ethernet card and to route all traffic from the host through a different ethernet card?

I'm using vmbuilder and kvm on ubuntu 9.04.

Thanks in advance,
Whit

---

### Post by evermooingcow on 2009-06-11
Bump because I'd like to know also.

I'll add though that I think this is possible in Xen.

---

### Post by syyid on 2009-06-11
*bump*
Would like to know the same

---

### Post by LiLoather on 2009-07-07
*Bump*

I'd like to know this, too.

In fact I'm baffled by the entire relationship of Jaunty to the physical devices of its machine as I want to run four ethernet connections on it, one on the motherboard and three PCI cards, but can only configure three (through Webmin as I'm running the server edition) so it appears one is not being recognised but I've no idea why or which one.  Nor without extensive juggling with ethernet connections is it possible to tell which which card has been allocated what designation, as unfortunately their MAC addresses are not printed on them.

With Windows you just look at Device Manager and it tells you what you have on board, what drivers have been loaded for it, whether it's working and, sometimes, why it isn't working if it isn't.  With Linux...?

---

### Post by armstrtw on 2009-07-08
3 bumps and no answers...

Is anyone aware of a good linux networking forum?  Or perhaps someone on the Gentoo forums might know how to do this.  If I find out, I'll cross post back here.

-Whit

---

