---
title: "ups questions."
date: 2013-01-30
forum: Server Platforms
---

### Post by leejewitt on 2013-01-30
hi am looking at getting a budget ups for my server, av been looking at this one

[http://www.ebay.co.uk/itm/600VA-VIX2060-Power-Inspired-UPS-System-/250797065408?pt=UK_Computing_Uninterruptible_Power_Supplies&hash=item3a64ab84c0](http://www.ebay.co.uk/itm/600VA-VIX2060-Power-Inspired-UPS-System-/250797065408?pt=UK_Computing_Uninterruptible_Power_Supplies&hash=item3a64ab84c0)

it has the usb port and comes with software for windows and linux but not sure about that i have heard about NUT and some other software for linux to control it.

if that one would be ok would i have to change the power setting on motherboard, because i have it set to power up after power cut would that be better off or on.

just want it to protect my raid 5 not a power hungry machine, 5 disks, core 2 duo, 4 gb ram.

any suggestions.

cheers

---

### Post by volkswagner on 2013-01-30
> **leejewitt said:**
> hi am looking at getting a budget ups for my server, av been looking at this one

[http://www.ebay.co.uk/itm/600VA-VIX2060-Power-Inspired-UPS-System-/250797065408?pt=UK_Computing_Uninterruptible_Power_Supplies&hash=item3a64ab84c0](http://www.ebay.co.uk/itm/600VA-VIX2060-Power-Inspired-UPS-System-/250797065408?pt=UK_Computing_Uninterruptible_Power_Supplies&hash=item3a64ab84c0)

it has the usb port and comes with software for windows and linux but not sure about that i have heard about NUT and some other software for linux to control it.

if that one would be ok would i have to change the power setting on motherboard, because i have it set to power up after power cut would that be better off or on.

just want it to protect my raid 5 not a power hungry machine, 5 disks, core 2 duo, 4 gb ram.

any suggestions.

cheers

I think NUT is for controlling multiple machines on your LAN.  This is useful if you have only one PC attached to a "smart UPS" and you want to shutdown other PC's on the LAN attached to "dumb" UPS's.

You want your PC to turn on after power failure.  Scenarion is as follows:
[LIST=1]
[*]Power goes out
[*]UPS software starts timer
[*]When software reached programmed time to shutdown due to extend power outage, the PC Will issue a shutdown command and issue shutdown to UPS
[*]The UPS removes power from the PC because it gets shutdown from PC command.
[*]Once power is restored, the resoration of power signals the UPS on, and in turn will power up your server (keep you BIOS set to auto power on after failure).
[/LIST]
 
I found this [blogpost]("http://zackreed.me/articles/40-ups-protect-your-files") very informative for learning about UPS function.

Sorry I can't comment on the referenced UPS nor software.  I'm very happy with my APC units.

---

### Post by leejewitt on 2013-01-31
ok thanks, they have said if i cant get it working a can send back for a refund.

would you say that will be powerful enough for the job. think its 600va but no sure what that means or what i need, as  i say not a power hungry machine.

cheers

---

### Post by tgalati4 on 2013-01-31
Most PC's are 80% efficient, so that 480 watts of power to drive a PC.  So if you have a "500-watt" power supply in the machine, you should be OK.  As a rule, don't connect laser printers, or large monitors (CRT) or TV's because they will suck the power out of the UPS without enough protection for the PC.

The watt ratings are printed on the back of the PC either on the power supply or near it.

---

### Post by leejewitt on 2013-01-31
great thanks that one was out of stock so bought the more expensive one.

1200VA and 720w rating should be better, will only be using for one computer as i don't think it would be enough for my gaming pc, only wanted it for my server anyway.

---

