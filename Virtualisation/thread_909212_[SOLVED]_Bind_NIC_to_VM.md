---
title: "[SOLVED] Bind NIC to VM"
date: 2008-09-03
forum: Virtualisation
---

### Post by MaindotC on 2008-09-03
I have several NIC's on my host machine and I would like to bind one of the interfaces to a VM instead of having the VM share one interface with the host o/s and I don't want it NAT'd.  I've toyed with some of the Network settings in the VBox control panel but I'm a little confused by the interface choices I have from the drop-down menu.  Can anyone give me a direction on how to do that?  Thanks!

---

### Post by MaindotC on 2008-09-03
bump - has no one ever done this or is it just so obvious that I don't deserve a reply?  Isn't this the whole point of a virtual machine so you can have several servers on one machine?

---

### Post by MaindotC on 2008-09-04
bump

---

### Post by Joeb454 on 2008-09-04
Try not to bump more than once every 24 hours if possible :)

That said - I'm also quite interested in doing this for my laptop. I'd like to bind the wired interface to the VM

---

### Post by MaindotC on 2008-09-04
Sorry about that - no offence intended.  I'm also posting on vBox forums so hopefully I'll get an answer there.  I can't believe this is so difficult to find.  Why would you VM if you can't access the VM via a seperate IP address?  Just makes no sense.

---

### Post by MaindotC on 2008-09-04
I got the following from irc #vbox:
```

<strAlan> is there a way to bind a physical interface (not used by the host o/s) to a VM?
<JshWright> sure, attach it to a bridge, attach a tap to that bridge, and give the tap to the VM
<strAlan> JshWright: thank you for replying - isn't bridging involving the host o/s's nic ?
<JshWright> I'm not understanding... is this other NIC not in the host computer?
<strAlan> yes it is
 I have three NIC's on one machine
 I have two VM's and I want each to have its own physical interface
<JshWright> what host OS?
<strAlan> Ubuntu 8.04
 vm's are Fedora 9 and Ubuntu Server 8.04
<JshWright> strAlan: so assuming eth0 is for you host, you need to create br1, and attach eth1 and tap1 to it, then give tap1 to one of your VMs, repeat for eth2, br2, and tap2
<strAlan> JshWright: I've read about bridging but I thought it was specific to the host o/s's nic - I'll read up on bridging and try it out :)
 JshWright: what you said certainly makes sense - I'll get to work on it
<strAlan> JshWright: for some reason I thought bridging was only for the host o/s
 host o/s's nic
<JshWright> you can bridge whatever you'd like
<strAlan> JshWright: for some reason I didn't think of it that way - makes sense now :) I'll let you know how it goes if you're on tomorrow

```

So you follow the directions for [[u]bridging network interfaces[u]](http://samiux.wordpress.com/2007/07/11/bridge-network-interface-on-virtualbox/) (sorry I couldn't immediately find a UF link - change my post if you wish) and instead of bridging the VM interface to the host o/s's interface, you use one of the other availabe interfaces.  For example, my machine has eth0, eth1, eth2, so eth0 will be used by the host o/s, and eth1 will be used for the Fedora VM, and eth2 will be used by the Ubuntu 8.04 Server VM.  I'll post when I get it done tonight about 9 pm EST.

---

### Post by MaindotC on 2008-09-23
Thread solved per [this link](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=912442)

---

