---
title: "ACPI Issues With Starling"
date: 2010-03-20
forum: System76 Support
---

### Post by Ian505 on 2010-03-20
I have a star1 system which seems to be shutting down randomly whenever the battery is in the system. No issues running purely from AC, but as soon as the battery is utilized either the system powers down as if the power went out.

I did quick look over of the system log, and found this - leading me to think that it is an issue with ACPI.
```
Mar 20 08:14:57 ian-laptop kernel: [    0.172961] bio: create slab <bio-0> at 0
Mar 20 08:14:57 ian-laptop kernel: [    0.173587] ACPI: EC: Look up EC in DSDT
Mar 20 08:14:57 ian-laptop kernel: [    0.181149] ACPI: BIOS _OSI(Linux) query ignored
Mar 20 08:14:57 ian-laptop kernel: [    0.182155] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar 20 08:14:57 ian-laptop kernel: [    0.696013] ACPI: EC: missing confirmations, switch off interrupt mode.
Mar 20 08:14:57 ian-laptop kernel: [    0.968088] ACPI: Interpreter enabled
Mar 20 08:14:57 ian-laptop kernel: [    0.968097] ACPI: (supports S0 S3 S4 S5)
Mar 20 08:14:57 ian-laptop kernel: [    0.968147] ACPI: Using IOAPIC for interrupt routing
Mar 20 08:14:57 ian-laptop kernel: [    0.978107] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Mar 20 08:14:57 ian-laptop kernel: [    0.978114] ACPI: EC: driver started in poll mode
Mar 20 08:14:57 ian-laptop kernel: [    0.978646] ACPI: No dock devices found.
Mar 20 08:14:57 ian-laptop kernel: [    0.979920] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Mar 20 08:14:57 ian-laptop kernel: [    0.979935] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7012dc8), AE_ALREADY_EXISTS
Mar 20 08:14:57 ian-laptop kernel: [    0.979954] ACPI: Marking method _OSC as Serialized
```

I am running Ubuntu 9.10 Netbook Remix, and have installed all updates thus far. Reinstalling isn't an issue, but I'm getting kind of tired of reinstalling. I've already reinstalled 3 times and have only had the machine for ~4 months. At least it's not the wireless this time.

---

### Post by HotShotDJ on 2010-03-20
> **Ian505 said:**
> I have a star1 system which seems to be shutting down randomly whenever the battery is in the system. No issues running purely from AC, but as soon as the battery is utilized either the system powers down as if the power went out.The first thing I'd look at is the health of the battery itself.  Even on a brand new system, sometimes you get a bad battery.  Based on other posts in this forum, System76 is very good about replacing them.

Please run the following from a command-line and post the results:```
cat /proc/acpi/battery/BAT0/*
```

---

### Post by Ian505 on 2010-03-20
I checked and couldn't find a BAT0 in the above directory, but there was a BAT1. 

```
cat: /proc/acpi/battery/BAT1: Is a directory

```

Of course, now that I've posted asking for help, the machine hasn't crashed yet. Though I have kept it on AC power, I did put in and fully charge the battery.

The battery has been fully discharged maybe 4 times, but it's experienced many partial drains without a hitch.

I was using the netbook in the sun for a while the day the problem started, but not for very long and as soon is I thought it was getting too hot I moved inside. The problem continued into the next day.

---

### Post by HotShotDJ on 2010-03-20
> **Ian505 said:**
> ```
cat: /proc/acpi/battery/BAT1: Is a directory

```I just checked on my friend's Starling, and it is BAT1... sorry about that.  In any case, you left out the last few characters of the command.  Please run:```
cat /proc/acpi/battery/BAT1/*
```Don't forget the /* at the end.

---

### Post by thomasaaron on 2010-03-22
Please try to re-seat the battery. Make sure it is in nice and tight, and ensure the lock tabs are in the locked position.

---

### Post by isantop on 2010-03-23
Building on what Tom said above, good charge/discharge habits are also essential to good battery performance. Make sure to try and charge the battery completely before discharging (partial charges are bad), try to not run the computer on both AC and Battery if the battery is fully charged, and don't kill the battery completely when you discharge (I usually run to about 10% remaining before plugging in).

When you first recieved the computer, did you make sure to chagre the battery fully for the first charge. Sometimes, partial first charges ruin a battery for life.

HotSHotDJ's command would give us some good insight to your battery, or you can right-click on the battery icon in the notification area, click power history, then laptop battery. Scroll down the list to the item titled "Capacity" and post that percentage.

---

