---
title: "Ubuntu shuts off randomly"
date: 2012-05-23
forum: System76 Support
---

### Post by goldencako on 2012-05-23
I own a serp6, on which I dual boot Ubuntu 12.04 and Windows 7. A few months ago, Ubuntu started to randomly shut down. At the time I was running only Ubuntu 10.10. After I cleanly installed Windows 7 and Ubuntu 12.04, the system persisted on Ubuntu, but so far not on Windows.

The problem I have is that the computer shuts down randomly. Sometimes when it's just starting to book (right after grub), and sometimes after a few minites and sometimes after a few hours.

I thought it was a CPU temperature problem, so I cleaned out the fans and then logged the temperature before crashes. The CPUs' temperatures were never above 70 degrees Celsius.

I check various system logs right after the crashes and nothing suspicious showed up.

I'd like to know what I can do to debug and eventually solve the problem.

---

### Post by isantop on 2012-05-24
> **goldencako said:**
> I own a serp6, on which I dual boot Ubuntu 12.04 and Windows 7. A few months ago, Ubuntu started to randomly shut down. At the time I was running only Ubuntu 10.10. After I cleanly installed Windows 7 and Ubuntu 12.04, the system persisted on Ubuntu, but so far not on Windows.

The problem I have is that the computer shuts down randomly. Sometimes when it's just starting to book (right after grub), and sometimes after a few minites and sometimes after a few hours.

I thought it was a CPU temperature problem, so I cleaned out the fans and then logged the temperature before crashes. The CPUs' temperatures were never above 70 degrees Celsius.

I check various system logs right after the crashes and nothing suspicious showed up.

I'd like to know what I can do to debug and eventually solve the problem.

So, you're only having the problem on Ubuntu? Would it be possible to try running from a LiveCD of Ubuntu 12.04 to rule out a software problem? You'll want to download and burn a fresh CD, rather than re-using the same one from before.

---

### Post by goldencako on 2012-05-24
I'll do this tonight. Since it shuts off randomly, I don't know how long I'll have to run the LiveCD, so I'll just leave it on overnight.

The problem only shows up in Ubuntu. At first it was 10.10 and now 12.04. I've had Windows 7 installed for about 2 weeks now, and I haven't had that problem at all. In contrast, just today in Ubuntu it shut off four times: two right after booting, and 2 more about 1~2 hours after use.

---

### Post by 2F4U on 2012-05-24
In my opinion, 70 degree Celsius is pretty high, but I don't know the specs of your hardware. It might be worth looking at these. If I am experiencing random shutdowns I look at those things:
- syslog, whether it contains error messages releated to the shutdown
- temperature of important system components such as CPU and GPU
- test RAM. I let memtest run through several iterations

---

### Post by goldencako on 2012-05-25
I haven't had time to memtest or try the LiveCD but I have some follow-ups.

First of all, the crash happened on Windows too, for the first time, yesterday. So this might be a hardware problem.

Second, here are the syslogs for three crashes today:

```

May 25 19:00:01 MIMMI2 CRON[6061]: (cako) CMD (/usr/local/bin/flexget --cron)
May 25 19:13:21 MIMMI2 wpa_supplicant[1099]: WPA: Group rekeying completed with f4:ec:38:9d:c3:6e [GTK=CCMP]
May 25 19:17:01 MIMMI2 CRON[6572]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 19:39:08 MIMMI2 dhclient: DHCPREQUEST of 192.168.1.100 on wlan0 to 192.168.1.1 port 67
May 25 19:39:08 MIMMI2 dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
May 25 19:39:08 MIMMI2 dhclient: bound to 192.168.1.100 -- renewal in 3327 seconds.
-- crashed here --
May 25 20:20:01 MIMMI2 kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 25 20:20:01 MIMMI2 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="979" x-info="http://www.rsyslog.com"] start
May 25 20:20:01 MIMMI2 rsyslogd: rsyslogd's groupid changed to 103
May 25 20:20:01 MIMMI2 rsyslogd: rsyslogd's userid changed to 101
May 25 20:20:01 MIMMI2 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 25 20:20:01 MIMMI2 kernel: [    0.000000] Initializing cgroup subsys cpuset
May 25 20:20:01 MIMMI2 kernel: [    0.000000] Initializing cgroup subsys cpu
May 25 20:20:01 MIMMI2 kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon MMay 25 20:20:59 MIMMI2 kernel: imklog 5.8.6, log source = /proc/kmsg started.
-- crashed here --
May 25 20:20:59 MIMMI2 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1038" x-info="http://www.rsyslog.com"] start

```

```

May 25 20:22:23 MIMMI2 AptDaemon.PackageKit: INFO: Get updates()
May 25 20:22:24 MIMMI2 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/0557fa2387d6430f89d06353ba675e0f
May 25 20:28:19 MIMMI2 AptDaemon: INFO: Quitting due to inactivity
May 25 20:28:19 MIMMI2 AptDaemon: INFO: Quitting was requested
-- crashed here --
May 25 20:32:32 MIMMI2 kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

Finally, CPU temperature is not the problem. Below is `sensors` output before the crash.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +46.8°C  (crit = +98.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +46.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +46.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +47.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +46.0°C  (high = +84.0°C, crit = +100.0°C)
```

---

### Post by goldencako on 2012-06-01
I think I have solved the problem at least temporarily. Setting acpi=off on boot time seems to eliminate the random shutdowns on Ubuntu.

---

