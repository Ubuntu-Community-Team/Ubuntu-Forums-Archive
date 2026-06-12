---
title: "Ubuntu 10.04 Server x64 Random Lockups"
date: 2010-05-08
forum: Server Platforms
---

### Post by jeremymm on 2010-05-08
I recently attempted to convert my OpenSolaris to Lucid.  However, it has not gone well.  I wiped the disks with DBAN and installed Lucid.  The install went well however, now I cannot get the system to stay up for more than 3 hours.

I have run badblocks on the disks and have got no errors. I ran memtest for 2 passes and no errors. The machine with OpenSolaris would run for months with no issues. 

AMD Phenom II 810
8 GB DDR2
GigaByte AM2+ MB
780G Chipset
Radeon 3200 HD (IIRC)
2 Seagate 320 GB Soft Raid 1 (OS)
5 WD Greens 750 GB Soft raid 5 (Data) Currently disabled.
Intel Dual Port 1000 Server Pro NIC (On-broad disabled)

Any suggestions and trying to figure this out.  I disabled the Raid 5 so that it would stop resyncing.  It did not help the lockups.  I think I might have to try going back to 8.04 as it ran fine until I but OpenSolaris on.

There seems to be nothing unusual in dmesg

---

### Post by P4man on 2010-05-08
Anything in the other log files? /var/log/messages and syslog?

Also is it a kernel panic or not?

Lastly, you might want to try experimenting with kernel boot options, like adding "irqpoll" or even "acpi=off". If either would solve it, check for a bios update for your motherboard (you may want to check anyhow)

---

### Post by jeremymm on 2010-05-11
So I updated the bios last Friday. Everything seemed smooth.  It ran for 3 days with not issues and I was able to transfer my 300 GB of data and SVN repositories back onto the system.  

However, Monday night I upgraded kernel using apt-get.  Everything was fine until this morning when I did a 8 GB read from the machine and then it locked up again.

---

### Post by jeremymm on 2010-05-11
Actually the machine did not crash but all network traffic was stopped for quite some time.  Also my ssh sessions are being disconnected/timing out for some reason.  This is odd given network card is pretty reliable and well own card Intel server card.

---

### Post by jeremymm on 2010-05-11
I had this in dmesg if anyone has any ideas

```
[ 3246.010775] JBD: barrier-based sync failed on md1-8 - disabling barriers
[75326.060654] CE: hpet increasing min_delta_ns to 15000 nsec
[75892.801255] Clocksource tsc unstable (delta = 299961061422 ns)
[75892.808108] Switching to clocksource hpet
```

---

### Post by P4man on 2010-05-11
That message is pretty clear. A problem with the tsc clock, not exactly an uncommon issue, and usually... due to a crappy bios.. Try booting with 

```
clocksource=hpet
```

as boot option for your kernel. Disabling cool and quiet may also cure it, but that may not be desirable if the machine is in a datacenter.

---

