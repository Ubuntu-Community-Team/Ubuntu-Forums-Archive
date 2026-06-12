---
title: "clocksource tsc unstable"
date: 2009-07-30
forum: Server Platforms
---

### Post by amorfis on 2009-07-30
Hello,

My system is ubuntu-server.

After some time from booting (about one minute) my server hangs. All I can do is hard reset. Then after restart in /var/log/kern.log I can find:

Jul 29 22:38:57 leonidas kernel: [   90.729598] longhaul: Failed to set requested frequency!
Jul 29 22:38:57 leonidas kernel: [   90.731252] longhaul: Enabling "Ignore Revision ID" option.
Jul 29 22:38:57 leonidas kernel: [   91.201461] longhaul: Failed to set requested  frequency!
Jul 29 22:38:57 leonidas kernel: [   91.201482] longhaul: Disabling ACPI C3 support.
Jul 29 22:38:57 leonidas kernel: [   91.204230] longhaul: Disabling "Ignore Revision ID" option.
Jul 29 22:38:58 leonidas kernel: [   91.416133] longhaul: Failed to set requested frequency!
Jul 29 22:38:58 leonidas kernel: [   91.416152] longhaul: Enabling "Ignore Revision ID" option.
Jul 29 22:38:58 leonidas kernel: [   91.960048] Clocksource tsc unstable (delta = -105611479 ns)

I found some resources on the net, and it said to change clocksource, or disable ACPI. I tried disabling ACPI but it didn't help (but I noticed there was longer time before hanging). I can't change clock to hpet, because my system doesn't have such one.

Output of cat /sys/devices/system/clocksource/clocksource0/available_clocksource:
acpi_pm jiffies tsc

Anyone knows what can I do about it?

Best regards
amorfis

---

### Post by Arup on 2009-07-30
If this is an AMD machine, its an old issue, try updating BIOS.

---

### Post by amorfis on 2009-07-30
It's not AMD, but upgrading the BIOS is always a good thing. I'll give it a try.

---

### Post by Arup on 2009-07-30
> **amorfis said:**
> It's not AMD, but upgrading the BIOS is always a good thing. I'll give it a try.

For disabling ACPI you need to add a noapic line to the grub in menu.lst

---

### Post by amorfis on 2009-07-30
> **Arup said:**
> For disabling ACPI you need to add a noapic line to the grub in menu.lst

I already disabled ACPI in bios.

---

### Post by dave37 on 2010-11-23
I've got the same problem but it only occurred after upgrading ram.  It's an old ibm netvista used as a file server with Hardy and has 3 ram slots.  It used to have 2 slots used, I bought new ram and put 512 meg in each slot.  Checked and it will accept the 3 sticks.  With 3 ram sticks in I get the clocksource tsc unstable lockup during boot.  If I remove any 1 of the 3 sticks it will boot normally.

I have tried almost everything as there is quite a bit of info about this.  Has anyone else come across the ram issue?

---

