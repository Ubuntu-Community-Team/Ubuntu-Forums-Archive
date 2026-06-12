---
title: "lucid, linux-kvm, clock/time sources"
date: 2010-06-25
forum: Virtualisation
---

### Post by awry on 2010-06-25
I'm running several new virtual machine servers using kvm on lucid.

I've started noticing clock irregularities on my virtual machines. Their clocks are not properly syncing with the host using kvm-clock in  /sys/devices/system/clocksource/clocksource0/current_clocksource.

I've read various reports around the Interwebs that kvm-clock is still a bit rough around the corners, and so it would seem. Interestingly, the system clock and the hardware clock on these virtual machines are off by a significant margin, as well.

I have also read reports that the TSC clock source (default on ubuntu server and our bare metal vm servers) has problems on SMP systems. So I was surprised to see it as the default in ubuntu server. Or have these been fixed in recent kernels?

I am wondering what the best practice is here. What's everybody else doing for clock sources and time keeping in their lucid kvm environments?

I am contemplating switching all the machines, bare metal and virtual, to the hpet clock source, and running chrony on all. This seems like the least buggy way to go. Thoughts?

---

