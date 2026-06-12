---
title: "Ubuntu 10.4 server stops accepting connections after a period of time"
date: 2011-04-24
forum: Server Platforms
---

### Post by natdog on 2011-04-24
Hey all,

I'm not sure if this belongs in the Server or Networking section of the forums.  Anyway, last month I upgraded my server to Ubuntu 10.04 LTS.  Since then, I've had a recurring problem wherein after a certain period of time, the server stops accepting network connections.  Ubuntu 10 will continue to reject network connections until someone logs into the server locally, after which time network connectivity is restored and the cycle begins anew.  Essentially, the server goes into a "half sleep mode".  I say half because the computer is still on and the fans are running.

I've done some searching around various forms and initially figured this issue was related to problems with the Network Manager service ([https://bugs.launchpad.net/ubuntu/lucid/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/lucid/+source/network-manager/+bug/524454)), so I removed the service altogether.  However, this problem is still occurring.   

I've poured over /var/log/messages and /var/log/syslog, but have noticed no irregular behavior.  Has anyone else experienced this issues?  I'd rather not resort to downgrading back to Gusty Gibbon if I can help it.

I am happy to provide more information if its needed

---

### Post by elico on 2011-04-24
what is your hardware?
> lspci
you should try to remove ani acpi features on the bios and also on grub\kernel load 
> acpi=offf
if the reason is something related to it.

hope it will help you.

---

### Post by natdog on 2011-04-24
Thanks for the quick reply, elico!  Here is my hardware listing --

> 
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]


I've added acpi=off to my grub boot options and have confirmed that acpi is off in my bios.  I'll post again with a status update as soon as I have one.  Usually it takes about 8-10 hours before the server starts rejecting network connections.

---

### Post by ekool on 2011-04-24
I had a similar issue to this many years ago and it turned out to be the local router causing the problem. Was kind of an issue with the router/switch and the ARP table would forget about the linux box.

If I kept a ping session on the linux box going to an outside host it would never forget and connectivity to the box would stay up no matter how long...

Replacing the switch/router fixed the problem.

You may want to try to keep a ping going to an outside host and see if the problem goes away and that'll give you another direction to look at.

---

### Post by natdog on 2011-04-25
Well, it's been 24 hours and it looks like the server is still accepting network connections!  I think explicitly disabling acpi might have done the trick.  Thanks again for the help everyone!

---

