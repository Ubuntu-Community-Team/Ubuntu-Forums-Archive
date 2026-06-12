---
title: "Is running a firewall VM secure?"
date: 2006-12-21
forum: Server Platforms
---

### Post by jinx099 on 2006-12-21
I currently have a small home network for myself and my 3 roommates.  I have a box dedicated to a pfsense firewall with interfaces for WAN, LAN, and wireless (OPT1), and I also have a server for my personal use.  Now, what I am thinking of doing is basically combining the 2 boxes into 1 using VMware.  I know that I CAN do it, but the question is if I SHOULD do it.

The WAN would be bridged to the VM, and would NOT be configured at all on the host OS.  The LAN would be briged to the VM and configured on the OS.  

So, how secure would this be?  What COULD happen, and what could I do to prevent it?

---

### Post by x64Jimbo on 2006-12-21
Hah, hey Ryan. Long time no see. From my personal experience, I'm gonna have to say that it would be difficult to pull off, and the stability of your network would be possibly compromised by running critical elements in virtual environments. I also know that VMWare only supports USB for peripheral passthrough, so getting your wireless to work on it might be a bit of a pain. 
Otherwise, as far as security goes, you might still be exposing the VM host box to threats if it is having to pass traffic from the WAN into the VM through its software - I prefer to have all my stuff firewalled at the network border and have it done with there. 
So I guess the question becomes this: which function were you hoping to virtualize? If it's the firewall, I'd skip it. If you want to virtualize your (fileserver/printserver/whatever?) I'd say go for it.

---

### Post by jinx099 on 2006-12-21
Hey Jimmy, you snowed in?

I know it would be reasonably stable to run it in VMWare because I have a Dapper LAMP install running in VMware that I use as my bittorrent server with torrentflux (great software, check it out).  The VM's uptime has always been as long as the Host's uptime.  As for wireless, I just have a standard D-Link wireless router acting as an AP that I just plug into the OPT1 interface, so it's no problem.

> Otherwise, as far as security goes, you might still be exposing the VM host box to threats if it is having to pass traffic from the WAN into the VM through its software - I prefer to have all my stuff firewalled at the network border and have it done with there.

I understand, which is why I'm posting to get opinions.  I want to know what can be done to compromise the network if the firewall is in a VM rather than a dedicated box.  It seems to me like an attacker would still have to break into the firewall to gain access, but maybe I'm unaware of some VMware exploits.

---

### Post by technodigifreak on 2006-12-21
In theory, it is secure....

However, in practical terms it is not secure and it will be difficult to configure.  For which there are several reasons.

1.  A firewall is always one of the major bottlenecks in any network.  This is the main reason it should run on it's own hardware.  Virtual machines will run amazingly fast, but you can never get the full speed in a VM(Guest).  There is always a portion of the hardware that is "inaccessible" in the sense of speed to a VM(Guest).  

2.  Networking.  Running a network accessible VM(Guest) means that all traffic must be routed through the VM(Host) to get to the VM(Guest).  Essentially, the VM(Host) must have a live address on the networks that it's guests are also on.  This means that, unless someone can devise a way for the VM(Host) to be physically attached to the insecure connection (internet) and not have an active connection of it's own, the VM(Host) will be logically outside of the firewall.  Basically, everything on the network that the VM(Guest) is exposed to, so is the VM(Host).

3.  Complexity.  Think about the nature of these devices.  A Firewall is a network/infrastructure device.  It exists to get data elsewhere.  So it makes sense for it to be as dumb as possible.  Keep It Simple!  Would you virtualize a switch?  What about a router?  Maybe a hub?  The reason VM's make the Server and Desktop worlds great are the exact reason they are not used for infrastucture devices.

There are plenty of other reasons, but these are the quickest and easiest to convey.  Let us know if this was helpful.

---

### Post by jinx099 on 2006-12-21
> **technodigifreak said:**
> In theory, it is secure....

However, in practical terms it is not secure and it will be difficult to configure.  For which there are several reasons.

1.  A firewall is always one of the major bottlenecks in any network.  This is the main reason it should run on it's own hardware.  Virtual machines will run amazingly fast, but you can never get the full speed in a VM(Guest).  There is always a portion of the hardware that is "inaccessible" in the sense of speed to a VM(Guest).  
But my server is an Athlon 64 3000+  vs my current firewall which is a PII 350 MHz.  Does this still hold true?  

> **technodigifreak said:**
> 
2.  Networking.  Running a network accessible VM(Guest) means that all traffic must be routed through the VM(Host) to get to the VM(Guest).  Essentially, the VM(Host) must have a live address on the networks that it's guests are also on.  This means that, unless someone can devise a way for the VM(Host) to be physically attached to the insecure connection (internet) and not have an active connection of it's own, the VM(Host) will be logically outside of the firewall.  Basically, everything on the network that the VM(Guest) is exposed to, so is the VM(Host).

Well, I believe I can bridge a NIC from my host to my guest WAN nic and leave the NIC unconfigured on the host.  I've not tested this, but I plan to later today and I'll post back when I do.  I have tested bridging the LAN nic and leaving it unconfigured on the host and it worked fine.

> **technodigifreak said:**
> 
3.  Complexity.  Think about the nature of these devices.  A Firewall is a network/infrastructure device.  It exists to get data elsewhere.  So it makes sense for it to be as dumb as possible.  Keep It Simple!  Would you virtualize a switch?  What about a router?  Maybe a hub?  The reason VM's make the Server and Desktop worlds great are the exact reason they are not used for infrastucture devices.

There are plenty of other reasons, but these are the quickest and easiest to convey.  Let us know if this was helpful.

I understand, but this is a fairly simple home network for myself and 3 roommates (who only use internet).

---

### Post by technodigifreak on 2006-12-22
> **jinx099 said:**
> But my server is an Athlon 64 3000+  vs my current firewall which is a PII 350 MHz.  Does this still hold true?  

Well, I believe I can bridge a NIC from my host to my guest WAN nic and leave the NIC unconfigured on the host.  I've not tested this, but I plan to later today and I'll post back when I do.  I have tested bridging the LAN nic and leaving it unconfigured on the host and it worked fine.

I understand, but this is a fairly simple home network for myself and 3 roommates (who only use internet).

Ok, give it a try.  I'm still unsure why you'd want to run it in a VM though.  Why not just keep using the PII?  That PII should have more than enough horsepower to be a good firewall.  If you are concerned about it's age, look into a Mini-Itx setup.  They're extremely stable and have very low power consumption.

I've only setup WAN connection firewalls in VM's for testing purposes.  It just seems like a really foreign idea to me to set a live firewall up in one though.  Wouldn't it make more sense to have the VM(Host) firewalled and then run the other VM(Guests) on top of that?

Anyway.  Give it a try and update us when you find out for sure!

---

