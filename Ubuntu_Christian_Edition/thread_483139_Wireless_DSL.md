---
title: "Wireless DSL"
date: 2007-06-24
forum: Ubuntu Christian Edition
---

### Post by casawyer on 2007-06-24
I have DSL with wireless, and have wireless in my computer, but having problems with ubuntu keeping connections with it.  When I first bring up firefox after booting up, I get a connection, but when I try to access a different site, or try to post to a site like this one, I  loss my connection.  

Any thoughts?  

Thanks,
Charles

---

### Post by mig5 on 2007-06-24
Is the wireless signal just really weak and so the connection is lost every so often?  Do you have the same problem on other operating systems (other linuxes, windows, etc).
If it is the signal try adjusting the physical position of your wireless card and reciever for a better connection (ie: put them closer together).

---

### Post by bukwirm on 2007-06-24
What wireless adapter do you have?
type "lshw -C network" and look though the output if you don't know.

---

### Post by casawyer on 2007-06-24
> **mig5 said:**
> Is the wireless signal just really weak and so the connection is lost every so often?  Do you have the same problem on other operating systems (other linuxes, windows, etc).
If it is the signal try adjusting the physical position of your wireless card and reciever for a better connection (ie: put them closer together).

The wireless is a strong signal.  I have no problem with it when I run my windows xp.  

It works when I first bring up the Foxfire browser on ubuntu but when I click to go to another site or link, I loss my wireless altogether.  Not sure why.  I have to reboot to get it back and then it does the samething all over.  Hope that helps.

Thanks,

Charles

---

### Post by casawyer on 2007-06-24
> **bukwirm said:**
> What wireless adapter do you have?
type "lshw -C network" and look though the output if you don't know.

NB 802.11g Wireless LAN USB Adapter

---

### Post by casawyer on 2007-06-25
> **casawyer said:**
> NB 802.11g Wireless LAN USB Adapter

It's funny that this evening it is working fine.  I have not been kicked off or lost the wireless as yet, and been on all sorts of area's.

Charles

---

### Post by mig5 on 2007-06-25
Is there an IP address conflict on your network?  That could be causing you to lose the connection.  Check whether the computers on your network are using fixed IP addresses or DHCP.  If there are some fixed and some DHCP then you need to make sure the fixed ones are high numbers, eg: 192.168.1.200 , so that the DHCP doesn't assign the same IP as Ubuntu is using to another PC.  Or maybe you are using all fixed IPs and two of them are the same?

---

