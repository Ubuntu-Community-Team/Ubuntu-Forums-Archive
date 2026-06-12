---
title: "Network down on all Ubuntu servers"
date: 2011-04-01
forum: Server Platforms
---

### Post by sus on 2011-04-01
Aghh!

This one has me stumped and I need some help.

We have 8 Ubuntu servers running behind a Routerboard RB750. A mix of machines ranging from blade servers through to HP servers. On the same network, we have several windows machines running XP, server 2003 and SBS 2008.

We also have some Ubuntu servers that are the other side of the Routerboard that are not affected by this problem.

Up until 2 weeks ago everything was playing fine. But..

It seems that the NIC is crashing on all of the Ubuntu servers, randomly but all within a 10 minute time frame.

The Windows machines are not affected and the Ubuntu servers run fine but have no connectivity and drop off the network.

A reboot sorts out the problem and they will work again for a random period of time, then fail again.

Having checked the syslog, this is what I fine on all the Ubuntu servers...

```
Mar 31 02:34:35 www-002 kernel: [185356.000012] ------------[ cut here ]------------
Mar 31 02:34:35 www-002 kernel: [185356.000024] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
Mar 31 02:34:35 www-002 kernel: [185356.000027] Hardware name: R1200 CPU Blade
Mar 31 02:34:35 www-002 kernel: [185356.000030] NETDEV WATCHDOG: eth0 (e1000): transmit queue 0 timed out
Mar 31 02:34:35 www-002 kernel: [185356.000032] Modules linked in: fbcon tileblit font bitblit softcursor vga16fb vgastate nouveau ttm drm_kms_helper drm i2c_algo_bit lp serio_raw intel_agp shpchp$
Mar 31 02:34:35 www-002 kernel: [185356.000060] Pid: 0, comm: swapper Not tainted 2.6.32-30-generic-pae #59-Ubuntu
Mar 31 02:34:35 www-002 kernel: [185356.000063] Call Trace:
Mar 31 02:34:35 www-002 kernel: [185356.000070]  [<c0154bc2>] warn_slowpath_common+0x72/0xa0
Mar 31 02:34:35 www-002 kernel: [185356.000075]  [<c050068e>] ? dev_watchdog+0x1fe/0x210
Mar 31 02:34:35 www-002 kernel: [185356.000078]  [<c050068e>] ? dev_watchdog+0x1fe/0x210
Mar 31 02:34:35 www-002 kernel: [185356.000084]  [<c0154c3b>] warn_slowpath_fmt+0x2b/0x30
Mar 31 02:34:35 www-002 kernel: [185356.000088]  [<c050068e>] dev_watchdog+0x1fe/0x210
Mar 31 02:34:35 www-002 kernel: [185356.000093]  [<c0170030>] ? common_timer_set+0x0/0x170
Mar 31 02:34:35 www-002 kernel: [185356.000098]  [<c014c1cd>] ? scheduler_tick+0xfd/0x270
Mar 31 02:34:35 www-002 kernel: [185356.000105]  [<c0125d4b>] ? lapic_next_event+0x1b/0x20
Mar 31 02:34:35 www-002 kernel: [185356.000111]  [<c01645ce>] run_timer_softirq+0x13e/0x2c0
Mar 31 02:34:35 www-002 kernel: [185356.000116]  [<c017f804>] ? tick_dev_program_event+0x74/0xd0
Mar 31 02:34:35 www-002 kernel: [185356.000120]  [<c0500490>] ? dev_watchdog+0x0/0x210
Mar 31 02:34:35 www-002 kernel: [185356.000126]  [<c015b868>] __do_softirq+0x98/0x1b0
Mar 31 02:34:35 www-002 kernel: [185356.000130]  [<c017fc50>] ? tick_do_update_jiffies64+0x120/0x170
Mar 31 02:34:35 www-002 kernel: [185356.000134]  [<c015b9c5>] do_softirq+0x45/0x50
Mar 31 02:34:35 www-002 kernel: [185356.000138]  [<c015bb15>] irq_exit+0x65/0x70
Mar 31 02:34:35 www-002 kernel: [185356.000143]  [<c05b9cfc>] smp_apic_timer_interrupt+0x5c/0x8b
Mar 31 02:34:35 www-002 kernel: [185356.000148]  [<c010a1b1>] apic_timer_interrupt+0x31/0x40
Mar 31 02:34:35 www-002 kernel: [185356.000152]  [<c01700e0>] ? common_timer_set+0xb0/0x170
Mar 31 02:34:35 www-002 kernel: [185356.000156]  [<c013020a>] ? native_safe_halt+0xa/0x10
Mar 31 02:34:35 www-002 kernel: [185356.000162]  [<c03aa04b>] acpi_idle_do_entry+0x37/0x58
Mar 31 02:34:35 www-002 kernel: [185356.000165]  [<c03aa0d1>] acpi_idle_enter_c1+0x65/0xad
Mar 31 02:34:35 www-002 kernel: [185356.000170]  [<c04c871a>] cpuidle_idle_call+0x7a/0x100
Mar 31 02:34:35 www-002 kernel: [185356.000176]  [<c0108594>] cpu_idle+0x94/0xd0
Mar 31 02:34:35 www-002 kernel: [185356.000181]  [<c05a1738>] rest_init+0x58/0x60
Mar 31 02:34:35 www-002 kernel: [185356.000186]  [<c07e6902>] start_kernel+0x356/0x35c
Mar 31 02:34:35 www-002 kernel: [185356.000190]  [<c07e63d8>] ? unknown_bootoption+0x0/0x19e
Mar 31 02:34:35 www-002 kernel: [185356.000194]  [<c07e60bb>] i386_start_kernel+0xaa/0xb1
Mar 31 02:34:35 www-002 kernel: [185356.000197] ---[ end trace 8c5e70de89dbd4a5 ]---
Mar 31 02:34:37 www-002 kernel: [185357.944406] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

```


After this, I see lots of this in the syslog...

```
kernel: [185357.944406] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
```

Any ideas on where to start to troubleshoot?

Thanks.

---

### Post by Grenage on 2011-04-01
Assuming that a updates weren't installed on all the servers at the same time, lets break this down physically first.  Are the servers all connected to the same switch; if so, are the unaffected workstations connected to the same switch?

---

### Post by sus on 2011-04-01
Yes, all of the affected servers are connected to the same switch.

The windows based servers are also attached to the same switch.

Thanks.

---

### Post by Grenage on 2011-04-01
I'm wondering if there is some sort of connection issue, and the Ubuntu servers aren't handling it as well as the Windows servers.  I've seen a few instances where the connection was lost, and simply not picked up again.

Are you able to replace the switch with a spare, if only temporarily?  With Eight servers, there *must* be a common problem, and that's the logical point to start.

---

### Post by sus on 2011-04-01
Yes, good idea.

I will swap the switch out and report back.

---

### Post by sus on 2011-04-12
Ok. So after much poking and prodding we have found the problem.

One of the Ubuntu blade servers did not show any network card errors in the syslog. We swapped the hard drive into another blade and the problem has gone.

We are putting it down to faulty network hardware on the blade server.

---

### Post by Grenage on 2011-04-12
Excellent, glad to hear that you got it sorted; thanks for posting back.

---

