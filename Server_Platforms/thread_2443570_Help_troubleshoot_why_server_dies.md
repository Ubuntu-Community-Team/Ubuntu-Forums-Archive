---
title: "Help troubleshoot why server dies"
date: 2020-05-17
forum: Server Platforms
---

### Post by volkswagner on 2020-05-17
Greetings!

I have one of [these devices]("https://www.amazon.com/Fanless-Industrial-Computer-HUNSN-Barebone/dp/B07JKW5T7R/") running Ubuntu 18.04.4 LTS .

It has 8gigs RAM and an inexpensive Vaskey 128G mSATA SSD.
After some undermined amount of time the server simply "dies".
I don't see any real clue in logs.

This symptom has been present over the past few kernel upgrades.

What can I do to get more info then next time it dies?
Should I turn up verbosity on any logs?
Is there any kind of script/job I can run to do some checks periodically?


Timeline:
fresh boot = May 14 20:05:34 
apparent last breathe = May 16 01:17:01


syslog (last seven lines before it died):
```

May 15 23:05:35 bear dnsmasq[1268]: using nameserver 127.0.0.53#53
May 15 23:05:35 bear dnsmasq[1268]: reading /etc/resolv.conf
May 15 23:05:35 bear dnsmasq[1268]: using nameserver 127.0.0.53#53
May 15 23:05:35 bear systemd-timesyncd[654]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
May 15 23:17:01 bear CRON[9736]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 16 00:17:01 bear CRON[9875]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 16 01:17:01 bear CRON[10000]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

I do see this much earlier in kern.log:
```

May 14 20:05:55 bear kernel: [   31.181361] random: crng init done
May 14 20:05:55 bear kernel: [   31.181364] random: 5 urandom warning(s) missed due to ratelimiting
May 15 00:34:39 bear kernel: [16154.897340] perf: interrupt took too long (2522 > 2500), lowering kernel.perf_event_max_sample_rate to 79250
May 15 03:01:46 bear kernel: [24982.981202] perf: interrupt took too long (3172 > 3152), lowering kernel.perf_event_max_sample_rate to 63000
May 15 06:25:28 bear kernel: [37204.828939] perf: interrupt took too long (3971 > 3965), lowering kernel.perf_event_max_sample_rate to 50250
May 15 14:43:14 bear kernel: [67071.259019] perf: interrupt took too long (4964 > 4963), lowering kernel.perf_event_max_sample_rate to 40250
```

Some general info:

```

Linux bear 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

# free -h
              total        used        free      shared  buff/cache   available
Mem:           7.7G        1.2G        5.9G        972K        571M        6.2G

# lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)


# smartctl -H /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-99-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

---

### Post by LHammonds on 2020-05-17
Is it plugged into a UPS?

If UPS, is the UPS battery good and can hold a charge under stress for several minutes?

If no UPS, are you experiencing brownouts?

Not likely but is there a powersaver mode option in the BIOS that might auto-shutdown the machine?

To see when it goes down, I would have another machine watching it and if it fails to respond, have an alert sent to you or at least log the time when it goes offline.

Also, can you get the temp of the machine and write it to a log file periodically?  I wonder if it gets hot and powers off to save itself.

LHammonds

---

### Post by volkswagner on 2020-05-17
I thought it was power related. Prior to 5/12 it was not on a UPS. I added a UPS and configured apcupsd. No power events have occurred since then, but server died during this time.

I will try your idea to monitor temps.

The server is remote and headless.

---

### Post by volkswagner on 2020-05-21
I just wanted to update while I wait to see if the server dies.

I'm already past three days of uptime (yay)!

I think perhaps the BIOS or something may be causing a 
low power or sleep state????

I say this because I'm past the 29hrs of the last failure.

The only change; I set a cron job to run the following
script every five minutes. Perhaps this activity is
keeping the server "alive"???

```
#!/bin/bash
/bin/date >> /home/eric/temp.txt
/bin/ping -c 2 google.com >> /home/eric/temp.txt
/usr/bin/sensors >> /home/eric/temp.txt
/usr/bin/free -h >> /home/eric/temp.txt
```

---

### Post by LHammonds on 2020-05-21
If it was trying to go to sleep, that activity writing to the HD and hitting the NIC should keep it awake.

I usually see options in the BIOS to wake up a server rather than have it shutdown.  Sleep, hibernation and poweroff are usually controls of the operating system.

If it continues to stay up, poke around the bios and see if there are any options for powering down.  Also, look out for power buttons that can get pushed by "animals" accidentally and cover/protect the power button.  Also check for loose power connections or faulty power cord.   I still wonder if there is an overheat heat issue or faulty power supply...which would not allow any warnings/log entries if it dies.

LHammonds

---

