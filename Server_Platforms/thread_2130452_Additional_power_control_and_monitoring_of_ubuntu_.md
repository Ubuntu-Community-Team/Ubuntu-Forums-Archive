---
title: "Additional power control and monitoring of ubuntu servers"
date: 2013-03-29
forum: Server Platforms
---

### Post by jonobr on 2013-03-29
Hi There

Apologies for my lack of hardware knowledge here, but hoping someone can set me straight.

I was tasked with controlling two of our ubuntu servers remotely in a hard to reach place.
The idea is to monitor them via snmp and do some port forwarding through a managed switch so we can access the CLI and so on.

I was also asked that as a double redundant method, we could add in two relays to cycle the power (not my preferred method) if the things became totally inaccessible.

I designed a complete box that looks like the attachment. Its using a managed switch, two relays and a power control thingy. It was all placed into one box and its functional , but Im no fan of it.

The question is, is there an off the shelf box out there I can buy that would do all this?
Or a box to control one server and buy install two?

I ask as there are more of these type of things to come

Thanks

jonobr[ATTACH=CONFIG]240692[/ATTACH]

---

### Post by tgalati4 on 2013-03-29
I would think that a smart UPS could perform this function.  Searching "ethernet controlled uninterruptible power supply" I found this:

[http://www.opengear.com/UPS.html](http://www.opengear.com/UPS.html)

That is an interesting box that you designed, but I don't see an UPS or how an UPS could be connected, unless it is upstream of your device.

The more mainstream method would be to add an expensive SNMP card to a smartUPS and use the UPS to issue shutdowns.  Set the BIOS on the servers to reboot on power-on.  Set the UPS to shutdown itself after server power down--so it can recharge its batteries after a power event.  Use SNMP call to wake up the UPS and then power the servers which would cause a cold-boot at power on.

---

### Post by jonobr on 2013-04-01
Hey 

Great idea. There are UPS devices on there, but just for power backup, but swapping them out for something smarter is a great Idea.

As said, I am not really a hardware person.. so thanks for the input!!

---

### Post by tgalati4 on 2013-04-01
What are the existing UPS's?  There's probably some capability that already exists.

---

