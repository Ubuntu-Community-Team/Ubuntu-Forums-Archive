---
title: "Clock drift - is this normal?"
date: 2011-11-08
forum: Server Platforms
---

### Post by chrisjsmith on 2011-11-08
I'm losing 2.8 seconds a day through clock drift on Ubuntu 10.04 LTS.  Is that normal?

I only ask as the machine ran NetBSD before which lost 0.02 seconds a day at average.

I'm running ntpdate against pool.ntp.org daily so it's kept synced but ntpdate is reporting 2.8 seconds drift daily.

This is unfortunately causing a few problems as we have some low latency timestamp based software running.

I have the option of running ntpdate hourly but I'd rather work out if it's a kernel issue first.

Kernel is:

Linux dev-02 2.6.32-34-server #77-Ubuntu SMP Tue Sep 13 20:54:38 UTC 2011 x86_64 GNU/Linux

---

### Post by SeijiSensei on 2011-11-08
Use the **ntpd** daemon, not ntpdate, if you want to maintain synchronization.

And, yes, most PC internal clocks are pretty poor.  That's why you need to use NTP.

---

### Post by chrisjsmith on 2011-11-08
The kernel is responsible for time tracking, not the RTC which is used only between reboots.

The RTC is fine (0.01 sec drift a day).

---

