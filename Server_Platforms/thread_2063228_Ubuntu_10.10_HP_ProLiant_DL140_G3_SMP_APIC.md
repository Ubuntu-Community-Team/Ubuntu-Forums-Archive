---
title: "Ubuntu 10.10 HP ProLiant DL140 G3 SMP APIC"
date: 2012-09-26
forum: Server Platforms
---

### Post by clancyhood on 2012-09-26
Ubuntu-ers,

This is a ready-solved thread for the sake of googlers suffering from this specific problem.

I have multiple dedicated servers using various flavours of the HP ProLiant DLxxx Gx series, all running 10.10 Maverick. 

2 identical machines (DL140 G3), both running Ubuntu 10.10, identical software in every way, but one would fail to boot without boot option nolapic (resulting in one CPU used out of 4), whilst other ran fine. 

Admins at DC stumped, so used KVM to try various options. DC admin told me bios had been reset on both machines - dunno if he was right about this, but in any case the problem lies with "8042 Emulation Support", which when enabled borks Ubuntu's ability to use multiple CPUs

BIOS => Advanced => "8042 Emulation Support = Disabled" 

Machine boots normally, with all 4 CPUs.

Only took me all day. Hopefully this saves someone time!

;)

---

