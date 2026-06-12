---
title: "Pangolin Performance will not boot"
date: 2012-03-20
forum: System76 Support
---

### Post by MacDaddy1660B on 2012-03-20
Hi all,

Running a Pangolin Performance laptop (panp7) with Ubuntu 11.10 64-bit. I began having some issues with this laptop about a month ago when the display would intermittently scramble and show all kinds of random colors scattered about the screen. In this state the computer would be frozen and I could do nothing but turn it off and try to restart. Restarting was often futile, as the display would remain scrambled for several reboot cycles. Finally, I found that inserting my Ubuntu 11.10 disc and booting a system from that would fix the problem and the system would boot normally after that. I haven't had this problem for a few weeks and figured that it was a problem with Xserver. Until...

Today I was using my laptop and the screen turned grey. The machine was frozen, so as before, I shut it off and tried to restart it. When it came back on, the screen stayed black. The "System 76" BIOS splash never came up. Worse, if I hit a key (like CTRL+ALT+F1), the computer beeps at me. Inserting my installation disk does nothing -- the CD drive doesn't even spool up or read the disk.

What could I do to find out what is wrong with the machine? From the looks of things, I wouldn't be surprised if I will be needing a new motherboard. I really need this machine as I am in the middle of writing a master's thesis. Any and all help would be appreciated.

-Gordon

---

### Post by MacDaddy1660B on 2012-03-20
...and but not a minute later after posting this, and after 10-15 reboot tries, it fired up. Checked the following /var/log files:


[LIST]
[*]syslog
[*]boot.log
[*]dmesg (no idea what any of it means)
[*]kern.log
[/LIST]
I see nothing except I see a few mentions of graphic interfaces in kern.log. Where else could I look for a probable cause? I really need this computer to perform reliably for the next several months or I am screwed. I will take this opportunity to back everything up just in case.

-Gordon

---

### Post by MacDaddy1660B on 2012-03-22
Anybody?

---

### Post by 2F4U on 2012-03-22
Since the problem did not happen under the control of Ubuntu, it is unlikely that you will find anything in the log files. The problem happens even before Ubuntu is booted, so I would assume that it is a hardware problem. Some computers indicate hardware problems during the POST phase by different manufacturer specific beep codes, which may be used to do some diagnosis.

Since it came back after some time, could it be a heat issue?

---

### Post by isantop on 2012-03-22
Backing up is definitely a good idea at this point. 

I can't think of anything else that might cause a problem like that. It could be a bad xorg.conf file, so you might try running this command:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by MacDaddy1660B on 2012-03-22
Here's my xorg.conf file:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

```

I'll give this a try.

I agree with 2F4U in that this is probably a hardware problem. I was going to mention that I also think that it may be a heat issue, as the problem typically shows up at the end of a long day of scientific computing. I wanted to see if somebody could come up with it independently. It takes an hour or so for the computer to come back to life though, which I find odd. Usually semiconductors cool pretty quickly, right? I should start logging when it happens. It doesn't seem to happen often.

That being said, I am going to open her up and have a look inside. I have already blown out the CPU heatsink. I don't recall seeing any dust on any other heat sinks in there. Is there anything that I should look out for in particular? Any thermal compound that I should check? Thermocouples or anything?

Thanks for the help, guys.

-Gordon

---

### Post by isantop on 2012-03-22
I wouldn't remove the copper CPU cooler, as the thermal compound will need to be cleaned off and reapplied. Otherwise, just make sure everything is clean and that there are no large dust deposits in the computer.

---

### Post by MacDaddy1660B on 2012-03-22
Thank you, isantop.

---

### Post by MacDaddy1660B on 2012-03-23
Actually opened the computer and blew it out with a blow gun. I found a decent amount of dust underneath the exhaust fins of the CPU heatsink, right above and next to the video component of the MB. Let's see if this was the problem.

Thanks again.

-G

---

### Post by MacDaddy1660B on 2012-03-25
Something interesting happened, though I do not know if it is related to my problem. I tried taking isantop's suggestion and did
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
I went to reboot, and the computer display went kinda nuts. Booting took a very long time and froze on several attempts, ending once with the computer beeping a code at me. I wasn't able to take down the numbers as I didn't have a pen near me. After several more reboots, the computer kinda "settled" and would boot OK, still with the delays and crazy graphics. Checked syslog:

```
Mar 25 11:14:20 fatpie-Pangolin-Performance kernel: imklog 5.8.1, log source = /proc/kmsg started.
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="866" x-info="http://www.rsyslog.com"] start
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd: rsyslogd's groupid changed to 103
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd: rsyslogd's userid changed to 101
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar 25 11:14:20 fatpie-Pangolin-Performance modem-manager[887]: <info>  ModemManager (version 0.5) starting...
Mar 25 11:14:20 fatpie-Pangolin-Performance avahi-daemon[890]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Mar 25 11:14:20 fatpie-Pangolin-Performance avahi-daemon[890]: Successfully dropped root privileges.
Mar 25 11:14:20 fatpie-Pangolin-Performance avahi-daemon[890]: avahi-daemon 0.6.30 starting up.
...
...
...
```
It kept going after this for a long time, looking for addresses, getting permissions, etc. Could this be related to my problem?

---

### Post by isantop on 2012-03-28
> **MacDaddy1660B said:**
> Something interesting happened, though I do not know if it is related to my problem. I tried taking isantop's suggestion and did
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
I went to reboot, and the computer display went kinda nuts. Booting took a very long time and froze on several attempts, ending once with the computer beeping a code at me. I wasn't able to take down the numbers as I didn't have a pen near me. After several more reboots, the computer kinda "settled" and would boot OK, still with the delays and crazy graphics. Checked syslog:

```
Mar 25 11:14:20 fatpie-Pangolin-Performance kernel: imklog 5.8.1, log source = /proc/kmsg started.
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="866" x-info="http://www.rsyslog.com"] start
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd: rsyslogd's groupid changed to 103
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd: rsyslogd's userid changed to 101
Mar 25 11:14:20 fatpie-Pangolin-Performance rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar 25 11:14:20 fatpie-Pangolin-Performance modem-manager[887]: <info>  ModemManager (version 0.5) starting...
Mar 25 11:14:20 fatpie-Pangolin-Performance avahi-daemon[890]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Mar 25 11:14:20 fatpie-Pangolin-Performance avahi-daemon[890]: Successfully dropped root privileges.
Mar 25 11:14:20 fatpie-Pangolin-Performance avahi-daemon[890]: avahi-daemon 0.6.30 starting up.
...
...
...
```
It kept going after this for a long time, looking for addresses, getting permissions, etc. Could this be related to my problem?

Those look fine. Certainly not indicative of a problem. 

Do you have the proprietary AMD drivers installed?

---

### Post by MacDaddy1660B on 2012-03-29
Hi isantop,

I'm assuming that you mean the *ATI/AMD Proprietary FGLRX Graphics Driver*?  This is installed and enabled. Interestingly, when this problem began I tried switching to the other "post-release update" driver. For some reason, it was not able to install, so I stuck with the original one mentioned above.

This reminds me. I could try restoring my System76 drivers. Maybe the problem could be there? But then why would I have problems getting the computer to boot in the first place if that were it?

By the way, this problem has come up two or three more times since my first post. It seems the frequency at which it occurs is increasing. As of two days ago, I tried reducing the CPU power thinking that it may be a heat issue. No problems since then, but I cannot conclude yet, of course.

Thanks.

-Gordon

---

### Post by MacDaddy1660B on 2012-04-02
Ok, limiting the CPU power doesn't change things. Restored all my System76 drivers. Trying that. Probably need some new hardware though.

---

### Post by MacDaddy1660B on 2012-04-02
Ok, this problem happened three separate times today. At each of the times, like before, the display scrambled. I went into syslog and found this same error duplicated at the same time each of the three times the computer crashed. Its long--sorry. It mentions BIOS settings and errors from ext-4 with regards to mounting.

```
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: imklog 5.8.1, log source = /proc/kmsg started.
Apr  2 15:03:09 fatpie-Pangolin-Performance rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="901" x-info="http://www.rsyslog.com"] start
Apr  2 15:03:09 fatpie-Pangolin-Performance rsyslogd: rsyslogd's groupid changed to 103
Apr  2 15:03:09 fatpie-Pangolin-Performance rsyslogd: rsyslogd's userid changed to 101
Apr  2 15:03:09 fatpie-Pangolin-Performance rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Linux version 3.0.0-17-generic (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 (Ubuntu 3.0.0-17.30-generic 3.0.22)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=ea094614-3f08-4d06-b875-117cb08c087c ro quiet splash quiet splash vt.handoff=7
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] KERNEL supported cpus:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   Intel GenuineIntel
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   AMD AuthenticAMD
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   Centaur CentaurHauls
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf27c000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf27c000 - 00000000bf282000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf282000 - 00000000bf3e9000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf3e9000 - 00000000bf40f000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf40f000 - 00000000bf46f000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf46f000 - 00000000bf470000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf470000 - 00000000bf4f1000 (ACPI NVS)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf4f1000 - 00000000bf70f000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf718000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf718000 - 00000000bf71f000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf71f000 - 00000000bf77f000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf77f000 - 00000000bf79f000 (ACPI NVS)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf79f000 - 00000000bf7e3000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf7e3000 - 00000000bf7ff000 (ACPI data)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000f070a000 - 00000000f070b000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000017c000000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  BIOS-e820: 0000000180000000 - 00000001bc000000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] DMI present.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] DMI: System76, Inc.                   Pangolin Performance              /W76x/M77xCUH                      , BIOS CALPELLACRB.86C.0000.X.0000000000 03/18/2010
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] No AGP bridge found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] last_pfn = 0x1bc000 max_arch_pfn = 0x400000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] MTRR default type: uncachable
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   00000-9FFFF write-back
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   A0000-BFFFF uncachable
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   C0000-D3FFF write-protect
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   D4000-DBFFF uncachable
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DC000-FFFFF write-through
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] MTRR variable ranges enabled:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   0 disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   3 base 100000000 mask F80000000 write-back
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   4 base 180000000 mask FC0000000 write-back
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   5 base 1BC000000 mask FFC000000 uncachable
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   6 disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   7 disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] original variable MTRRs
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 1, base: 0GB, range: 2GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 2, base: 2GB, range: 1GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 3, base: 4GB, range: 2GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 4, base: 6GB, range: 1GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 5, base: 7104MB, range: 64MB, type UC
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] total RAM covered: 6080M
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Found optimal setting for mtrr clean up
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 5      lose cover RAM: 0G
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] New variable MTRRs
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 2, base: 4GB, range: 2GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 3, base: 6GB, range: 1GB, type WB
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] reg 4, base: 7104MB, range: 64MB, type UC
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] last_pfn = 0xbf800 max_arch_pfn = 0x400000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] found SMP MP-table at [ffff8800000f6890] f6890
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] initial memory mapped : 0 - 20000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 20480
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bf800000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  0000000000 - 00bf800000 page 2M
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] kernel direct mapping tables up to bf800000 @ 1fffc000-20000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] init_memory_mapping: 0000000100000000-00000001bc000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  0100000000 - 01bc000000 page 2M
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] kernel direct mapping tables up to 1bc000000 @ bf7db000-bf7e3000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] RAMDISK: 365c0000 - 372d8000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: RSDP 00000000000f67d0 00024 (v02 PTLTD )
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: XSDT 00000000bf7f6309 00074 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: FACP 00000000bf7e5000 000F4 (v03 INTEL  CALPELLA 06040000 PTEC 00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: DSDT 00000000bf7e6000 08765 (v02 Intel  CALPELLA 06040000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: FACS 00000000bf79bfc0 00040
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: HPET 00000000bf7fec7a 00038 (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: MCFG 00000000bf7fecb2 0003C (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: APIC 00000000bf7fecee 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: SLIC 00000000bf7fed72 00176 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: BOOT 00000000bf7feee8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: SPCR 00000000bf7fef10 00050 (v01 PTLTD  $UCRTBL$ 06040000 PTL  00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: ASF! 00000000bf7fef60 000A0 (v16   CETP     CETP 06040000 PTL  00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: DMAR 00000000bf7ef000 00080 (v01 INTEL  CP_DALE  00000001 INTL 00000001)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: SSDT 00000000bf7e4000 009F7 (v01  PmRef    CpuPm 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] No NUMA configuration found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Faking a node at 0000000000000000-00000001bc000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Initmem setup node 0 0000000000000000-00000001bc000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   NODE_DATA [00000001bbffb000 - 00000001bbffffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]  [ffffea0000000000-ffffea00061fffff] PMD -> [ffff8801b5600000-ffff8801ba9fffff] on node 0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Zone PFN ranges:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   Normal   0x00100000 -> 0x001bc000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Movable zone start PFN for each node
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] early_node_map[10] active PFN ranges
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x00000010 -> 0x0000009c
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x00000100 -> 0x000bf27c
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x000bf282 -> 0x000bf3e9
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x000bf40f -> 0x000bf46f
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x000bf70f -> 0x000bf718
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x000bf71f -> 0x000bf77f
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x000bf79f -> 0x000bf7e3
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x000bf7ff -> 0x000bf800
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x00100000 -> 0x0017c000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     0: 0x00180000 -> 0x001bc000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] On node 0 totalpages: 1537149
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA zone: 5 pages reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA zone: 3919 pages, LIFO batch:0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   DMA32 zone: 765225 pages, LIFO batch:31
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   Normal zone: 10528 pages used for memmap
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]   Normal zone: 743136 pages, LIFO batch:31
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] nr_irqs_gsi: 40
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf27c000 - 00000000bf282000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf3e9000 - 00000000bf40f000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf46f000 - 00000000bf470000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf470000 - 00000000bf4f1000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf4f1000 - 00000000bf70f000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf718000 - 00000000bf71f000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf77f000 - 00000000bf79f000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf7e3000 - 00000000bf7ff000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f070a000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000f070a000 - 00000000f070b000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000f070b000 - 00000000feaff000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000feaff000 - 00000000feb00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000fec00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed1c000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PM: Registered nosave memory: 000000017c000000 - 0000000180000000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff8801bbc00000 s79616 r8192 d22784 u524288
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1512280
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Policy zone: Normal
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=ea094614-3f08-4d06-b875-117cb08c087c ro quiet splash quiet splash vt.handoff=7
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Checking aperture...
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] No AGP bridge found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Memory: 5967056k/7274496k available (6140k kernel code, 1125900k absent, 181540k reserved, 6894k data, 988k init)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Hierarchical RCU implementation.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Extended CMOS year: 2000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] vt handoff: transparent VT on vt#7
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] console [tty0] enabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] allocated 50331648 bytes of page_cgroup
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] hpet clockevent registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000000] Fast TSC calibration using PIT
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004000] Detected 2660.219 MHz processor.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5320.43 BogoMIPS (lpj=10640876)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000006] pid_max: default: 32768 minimum: 301
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000028] Security Framework initialized
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000041] AppArmor: AppArmor initialized
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000043] Yama: becoming mindful.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.000694] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.003113] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004199] Mount-cache hash table entries: 256
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004311] Initializing cgroup subsys cpuacct
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004315] Initializing cgroup subsys memory
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004321] Initializing cgroup subsys devices
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004323] Initializing cgroup subsys freezer
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004325] Initializing cgroup subsys net_cls
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004326] Initializing cgroup subsys blkio
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004332] Initializing cgroup subsys perf_event
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004355] CPU: Physical Processor ID: 0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004356] CPU: Processor Core ID: 0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004361] mce: CPU supports 9 MCE banks
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004369] CPU0: Thermal monitoring handled by SMI
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.004376] using mwait in idle threads.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.006042] ACPI: Core revision 20110413
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.018266] ftrace: allocating 25750 entries in 101 pages
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024924] DMAR: Host address width 36
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024926] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024932] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c9008020e30272 ecap 1000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024933] DMAR: DRHD base: 0x000000fed93000 flags: 0x1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024938] IOMMU 1: reg_base_addr fed93000 ver 1:0 cap c9008020630272 ecap 1000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024939] DMAR: RMRR base: 0x000000bf6e9000 end: 0x000000bf6fefff
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.024941] DMAR: No ATSR found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.025551] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.065139] CPU0: Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz stepping 02
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171222] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171227] ... version:                3
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171228] ... bit width:              48
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171229] ... generic registers:      4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171230] ... value mask:             0000ffffffffffff
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171231] ... max period:             000000007fffffff
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171232] ... fixed-purpose events:   3
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171233] ... event mask:             000000070000000f
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171551] Booting Node   0, Processors  #1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.171553] smpboot cpu 1: start_ip = 97000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.259019] CPU1: Thermal monitoring handled by SMI
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.279130]  #2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.279132] smpboot cpu 2: start_ip = 97000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.366746] CPU2: Thermal monitoring handled by SMI
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.386875]  #3 Ok.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.386876] smpboot cpu 3: start_ip = 97000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.474472] CPU3: Thermal monitoring handled by SMI
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.494464] Brought up 4 CPUs
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.494467] Total of 4 processors activated (21280.06 BogoMIPS).
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.496750] devtmpfs: initialized
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.496861] PM: Registering ACPI NVS region at bf470000 (528384 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.496871] PM: Registering ACPI NVS region at bf77f000 (131072 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498021] print_constraints: dummy: 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498048] Time: 22:02:51  Date: 04/02/12
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498075] NET: Registered protocol family 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498164] Trying to unpack rootfs image as initramfs...
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498166] ACPI: bus type pci registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498231] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.498233] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.542545] PCI: Using configuration type 1 for base access
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.543146] bio: create slab <bio-0> at 0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.544274] ACPI: EC: Look up EC in DSDT
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.545279] ACPI: Executed 1 blocks of module-level executable AML code
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548095] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548358] ACPI: SSDT 00000000bf71aa18 00466 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548599] ACPI: Dynamic OEM Table Load:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548601] ACPI: SSDT           (null) 00466 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548679] ACPI: SSDT 00000000bf71a518 004C5 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548908] ACPI: Dynamic OEM Table Load:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.548910] ACPI: SSDT           (null) 004C5 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.570456] ACPI: SSDT 00000000bf719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.570739] ACPI: Dynamic OEM Table Load:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.570741] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.594289] ACPI: SSDT 00000000bf718d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.594554] ACPI: Dynamic OEM Table Load:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.594556] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    0.693029] Freeing initrd memory: 13408k freed
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.025171] ACPI: Interpreter enabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.025179] ACPI: (supports S0 S3 S4 S5)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.025199] ACPI: Using IOAPIC for interrupt routing
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.030619] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.030863] ACPI: No dock devices found.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.030865] HEST: Table not found.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.030868] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031158] \_SB_.PCI0:_OSC invalid UUID
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031160] _OSC request data:1 8 1f 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031163] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031611] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031612] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031614] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031616] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031618] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031620] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031630] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031647] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031664] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031691] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031694] pci 0000:00:01.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031739] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031766] pci 0000:00:16.0: reg 10: [mem 0xf0704000-0xf070400f 64bit]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031861] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031866] pci 0000:00:16.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031906] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.031930] pci 0000:00:1a.0: reg 10: [mem 0xf0706000-0xf07063ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032035] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032039] pci 0000:00:1a.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032067] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032087] pci 0000:00:1b.0: reg 10: [mem 0xf0700000-0xf0703fff 64bit]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032181] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032185] pci 0000:00:1b.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032210] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032307] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032312] pci 0000:00:1c.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032338] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032434] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032439] pci 0000:00:1c.1: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032465] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032562] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032566] pci 0000:00:1c.2: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032594] pci 0000:00:1c.3: [8086:3b48] type 1 class 0x000604
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032691] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032695] pci 0000:00:1c.3: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032733] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032757] pci 0000:00:1d.0: reg 10: [mem 0xf0707000-0xf07073ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032862] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032866] pci 0000:00:1d.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032889] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.032973] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033102] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033128] pci 0000:00:1f.2: reg 10: [io  0x1830-0x1837]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033140] pci 0000:00:1f.2: reg 14: [io  0x1824-0x1827]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033151] pci 0000:00:1f.2: reg 18: [io  0x1828-0x182f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033161] pci 0000:00:1f.2: reg 1c: [io  0x1820-0x1823]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033171] pci 0000:00:1f.2: reg 20: [io  0x1800-0x181f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033182] pci 0000:00:1f.2: reg 24: [mem 0xf0708000-0xf07087ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033246] pci 0000:00:1f.2: PME# supported from D3hot
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033250] pci 0000:00:1f.2: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033272] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033291] pci 0000:00:1f.3: reg 10: [mem 0xf0709000-0xf07090ff 64bit]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033320] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033380] pci 0000:02:00.0: [1002:9553] type 0 class 0x000300
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033389] pci 0000:02:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033395] pci 0000:02:00.0: reg 14: [io  0x2000-0x20ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033401] pci 0000:02:00.0: reg 18: [mem 0xcfef0000-0xcfefffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033422] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033448] pci 0000:02:00.0: supports D1 D2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033463] pci 0000:02:00.1: [1002:aa38] type 0 class 0x000403
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033471] pci 0000:02:00.1: reg 10: [mem 0xcfeec000-0xcfeeffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033525] pci 0000:02:00.1: supports D1 D2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033551] pci 0000:00:01.0: PCI bridge to [bus 02-02]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033554] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033556] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033559] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033612] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033617] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033621] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033628] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033682] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033686] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033690] pci 0000:00:1c.1:   bridge window [mem 0xf0200000-0xf02fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033697] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033781] pci 0000:06:00.0: [8086:4235] type 0 class 0x000280
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.033819] pci 0000:06:00.0: reg 10: [mem 0xf0300000-0xf0301fff 64bit]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.034003] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.034010] pci 0000:06:00.0: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041104] pci 0000:00:1c.2: PCI bridge to [bus 06-06]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041114] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041118] pci 0000:00:1c.2:   bridge window [mem 0xf0300000-0xf03fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041125] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041198] pci 0000:07:00.0: [197b:2382] type 0 class 0x000880
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041221] pci 0000:07:00.0: reg 10: [mem 0xf0404000-0xf04040ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041429] pci 0000:07:00.2: [197b:2381] type 0 class 0x000805
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041452] pci 0000:07:00.2: reg 10: [mem 0xf0405000-0xf04050ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041656] pci 0000:07:00.3: [197b:2383] type 0 class 0x000880
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041679] pci 0000:07:00.3: reg 10: [mem 0xf0406000-0xf04060ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041885] pci 0000:07:00.5: [197b:0250] type 0 class 0x000200
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041908] pci 0000:07:00.5: reg 10: [mem 0xf0400000-0xf0403fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041939] pci 0000:07:00.5: reg 18: [io  0x4400-0x447f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.041956] pci 0000:07:00.5: reg 1c: [io  0x4000-0x40ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.042087] pci 0000:07:00.5: PME# supported from D0 D3hot D3cold
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.042093] pci 0000:07:00.5: PME# disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049086] pci 0000:00:1c.3: PCI bridge to [bus 07-07]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049095] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049099] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049106] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049176] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049181] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049185] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049192] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049194] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049196] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049197] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049199] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049201] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049202] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049234] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049696] \_SB_.PCI0:_OSC invalid UUID
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049697] _OSC request data:1 1f 1f 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049700]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049724] \_SB_.PCI0:_OSC invalid UUID
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049725] _OSC request data:1 0 1d 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049728]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.049729] ACPI _OSC control for PCIe not granted, disabling ASPM
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.052937] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.052984] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.052999] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053015] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053030] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053047] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053061] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053086]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053088]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053089] ACPI _OSC control for PCIe not granted, disabling ASPM
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053239] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053276] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053309] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053341] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053374] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053406] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053439] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053472] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053559] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053563] vgaarb: loaded
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053564] vgaarb: bridge control possible 0000:02:00.0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053695] SCSI subsystem initialized
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053757] libata version 3.00 loaded.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053787] usbcore: registered new interface driver usbfs
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053794] usbcore: registered new interface driver hub
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053812] usbcore: registered new device driver usb
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.053872] PCI: Using ACPI for IRQ routing
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063470] PCI: pci_cache_line_size set to 64 bytes
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063554] reserve RAM buffer: 000000000009c000 - 000000000009ffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063556] reserve RAM buffer: 00000000bf27c000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063559] reserve RAM buffer: 00000000bf3e9000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063562] reserve RAM buffer: 00000000bf46f000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063564] reserve RAM buffer: 00000000bf718000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063566] reserve RAM buffer: 00000000bf77f000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063568] reserve RAM buffer: 00000000bf7e3000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063569] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063649] NetLabel: Initializing
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063651] NetLabel:  domain hash size = 128
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063652] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063662] NetLabel:  unlabeled traffic allowed by default
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063704] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.063708] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.065722] Switching to clocksource hpet
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.068961] Switched to NOHz mode on CPU #0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.069013] Switched to NOHz mode on CPU #3
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.069045] Switched to NOHz mode on CPU #1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.069062] Switched to NOHz mode on CPU #2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070279] AppArmor: AppArmor Filesystem Enabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070304] pnp: PnP ACPI init
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070317] ACPI: bus type pnp registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070590] pnp 00:00: [bus 00-fe]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070593] pnp 00:00: [io  0x0000-0x0cf7 window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070594] pnp 00:00: [io  0x0cf8-0x0cff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070596] pnp 00:00: [io  0x0d00-0xffff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070597] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070599] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070600] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070602] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070603] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070604] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070606] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070607] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070609] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070610] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070611] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070613] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070614] pnp 00:00: [mem 0x000ec000-0x000effff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070616] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070617] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070618] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070683] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070704] pnp 00:01: [io  0x0000-0x001f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070708] pnp 00:01: [io  0x0081-0x0091]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070709] pnp 00:01: [io  0x0093-0x009f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070710] pnp 00:01: [io  0x00c0-0x00df]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070712] pnp 00:01: [dma 4]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070727] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070733] pnp 00:02: [mem 0xff000000-0xffffffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070749] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070806] pnp 00:03: [irq 0 disabled]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070816] pnp 00:03: [irq 8]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070818] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070834] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070841] pnp 00:04: [io  0x00f0]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070846] pnp 00:04: [irq 13]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070865] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070873] pnp 00:05: [io  0x002e-0x002f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070874] pnp 00:05: [io  0x004e-0x004f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070875] pnp 00:05: [io  0x0061]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070876] pnp 00:05: [io  0x0063]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070877] pnp 00:05: [io  0x0065]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070879] pnp 00:05: [io  0x0067]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070880] pnp 00:05: [io  0x0070]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070881] pnp 00:05: [io  0x0080]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070882] pnp 00:05: [io  0x0092]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070883] pnp 00:05: [io  0x00b2-0x00b3]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070884] pnp 00:05: [io  0x0680-0x069f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070885] pnp 00:05: [io  0x0500-0x050f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070887] pnp 00:05: [io  0x0600-0x0603]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070888] pnp 00:05: [io  0xffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070889] pnp 00:05: [io  0x0400-0x047f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070890] pnp 00:05: [io  0x1180-0x11ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070891] pnp 00:05: [io  0x164e-0x164f]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070893] pnp 00:05: [io  0xfe00]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070939] system 00:05: [io  0x0680-0x069f] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070941] system 00:05: [io  0x0500-0x050f] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070942] system 00:05: [io  0x0600-0x0603] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070944] system 00:05: [io  0xffff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070946] system 00:05: [io  0x0400-0x047f] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070947] system 00:05: [io  0x1180-0x11ff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070949] system 00:05: [io  0x164e-0x164f] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070951] system 00:05: [io  0xfe00] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070953] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070976] pnp 00:06: [io  0x0070-0x0077]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.070993] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071004] pnp 00:07: [io  0x0060]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071006] pnp 00:07: [io  0x0064]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071010] pnp 00:07: [irq 1]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071034] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071043] pnp 00:08: [irq 12]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071059] pnp 00:08: Plug and Play ACPI device, IDs PNP0f13 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071303] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071305] pnp 00:09: [mem 0xfed10000-0xfed13fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071306] pnp 00:09: [mem 0xfed18000-0xfed18fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071307] pnp 00:09: [mem 0xfed19000-0xfed19fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071308] pnp 00:09: [mem 0xe0000000-0xefffffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071310] pnp 00:09: [mem 0xf070a000-0xf070afff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071311] pnp 00:09: [mem 0xc0000000-0xc0000fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071312] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071314] pnp 00:09: [mem 0xfed90000-0xfed93fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071315] pnp 00:09: [mem 0xfed40000-0xfed44fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071318] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071319] pnp 00:09: [mem 0xff000000-0xffffffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071321] pnp 00:09: [mem 0xfee00000-0xfeefffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071364] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071366] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071368] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071370] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071371] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071373] system 00:09: [mem 0xf070a000-0xf070afff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071375] system 00:09: [mem 0xc0000000-0xc0000fff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071377] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071378] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071380] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071382] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071384] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071387] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.071389] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.072091] pnp 00:0a: [bus ff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.072126] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.072134] pnp: PnP ACPI: found 11 devices
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.072135] ACPI: ACPI bus type pnp unregistered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077705] PCI: max bus depth: 1 pci_try_num: 2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077760] pci 0000:00:1c.3: BAR 15: assigned [mem 0xc0100000-0xc02fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077763] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0300000-0xc04fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077766] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077768] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0500000-0xc06fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077771] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0700000-0xc08fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077773] pci 0000:00:1c.0: BAR 13: assigned [io  0x6000-0x6fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077776] pci 0000:02:00.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077778] pci 0000:00:01.0: PCI bridge to [bus 02-02]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077780] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077782] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077785] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077788] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077791] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077796] pci 0000:00:1c.0:   bridge window [mem 0xc0500000-0xc06fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077801] pci 0000:00:1c.0:   bridge window [mem 0xc0700000-0xc08fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077808] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077811] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077816] pci 0000:00:1c.1:   bridge window [mem 0xf0200000-0xf02fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077821] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077828] pci 0000:00:1c.2: PCI bridge to [bus 06-06]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077831] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077836] pci 0000:00:1c.2:   bridge window [mem 0xf0300000-0xf03fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077841] pci 0000:00:1c.2:   bridge window [mem 0xc0300000-0xc04fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077848] pci 0000:00:1c.3: PCI bridge to [bus 07-07]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077851] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077857] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077861] pci 0000:00:1c.3:   bridge window [mem 0xc0100000-0xc02fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077868] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077869] pci 0000:00:1e.0:   bridge window [io  disabled]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077875] pci 0000:00:1e.0:   bridge window [mem disabled]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077879] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077896] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077899] pci 0000:00:01.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077906] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077910] pci 0000:00:1c.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077920] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077924] pci 0000:00:1c.1: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077933] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077937] pci 0000:00:1c.2: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077946] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077950] pci 0000:00:1c.3: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077958] pci 0000:00:1e.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077962] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077963] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077965] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077966] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077968] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077969] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfeafffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077971] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077972] pci_bus 0000:02: resource 1 [mem 0xcfe00000-0xcfefffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077974] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077975] pci_bus 0000:03: resource 0 [io  0x6000-0x6fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077977] pci_bus 0000:03: resource 1 [mem 0xc0500000-0xc06fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077978] pci_bus 0000:03: resource 2 [mem 0xc0700000-0xc08fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077980] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077981] pci_bus 0000:04: resource 1 [mem 0xf0200000-0xf02fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077983] pci_bus 0000:04: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077985] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077986] pci_bus 0000:06: resource 1 [mem 0xf0300000-0xf03fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077987] pci_bus 0000:06: resource 2 [mem 0xc0300000-0xc04fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077989] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077991] pci_bus 0000:07: resource 1 [mem 0xf0400000-0xf04fffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077992] pci_bus 0000:07: resource 2 [mem 0xc0100000-0xc02fffff 64bit pref]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077994] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077995] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077997] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.077998] pci_bus 0000:08: resource 7 [mem 0x000d4000-0x000d7fff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.078000] pci_bus 0000:08: resource 8 [mem 0x000d8000-0x000dbfff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.078001] pci_bus 0000:08: resource 9 [mem 0xc0000000-0xfeafffff]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.078031] NET: Registered protocol family 2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.078225] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.079282] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.081572] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.081869] TCP: Hash tables configured (established 524288 bind 65536)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.081871] TCP reno registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.081885] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.081940] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082074] NET: Registered protocol family 1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082176] pci 0000:02:00.0: Boot video device
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082205] PCI: CLS 64 bytes, default 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082210] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082212] Placing 64MB software IO TLB between ffff8800bb27c000 - ffff8800bf27c000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082213] software IO TLB at phys 0xbb27c000 - 0xbf27c000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082231] Simple Boot Flag at 0x36 set to 0x80
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082623] audit: initializing netlink socket (disabled)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.082632] type=2000 audit(1333404170.920:1): initialized
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.110692] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.133925] VFS: Disk quotas dquot_6.5.2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.133969] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.134442] fuse init (API version 7.16)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.134505] msgmni has been set to 11680
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.134910] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.134945] io scheduler noop registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.134947] io scheduler deadline registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.134976] io scheduler cfq registered (default)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135066] pcieport 0000:00:01.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135093] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135337] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135351] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135384] intel_idle: MWAIT substates: 0x1120
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135385] intel_idle: v0.4 model 0x25
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135386] intel_idle: lapic_timer_reliable_states 0xffffffff
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.135981] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.136723] ACPI: AC Adapter [ADP0] (on-line)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.136811] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137834] ACPI: Lid Switch [LID0]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137861] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137865] ACPI: Power Button [PWRB]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137892] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137895] ACPI: Sleep Button [SLPB]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137918] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137920] ACPI: Power Button [PWRF]
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.137939] ACPI: acpi_idle yielding to intel_idle
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.145364] thermal LNXTHERM:00: registered as thermal_zone0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.145369] ACPI: Thermal Zone [THM0] (73 C)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.145389] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.145405] ERST: Table is not found!
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.145454] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.145934] ACPI: Battery Slot [BAT0] (battery absent)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.377174] Linux agpgart interface v0.103
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.377898] brd: module loaded
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378211] loop: module loaded
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378464] Fixed MDIO Bus: probed
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378480] PPP generic driver version 2.4.2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378502] tun: Universal TUN/TAP device driver, 1.6
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378503] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378553] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378569] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378589] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378593] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378616] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.378647] ehci_hcd 0000:00:1a.0: debug port 2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.382590] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.382606] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0706000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.396866] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.396989] hub 1-0:1.0: USB hub found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.396993] hub 1-0:1.0: 3 ports detected
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.397043] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.397054] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.397057] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.397081] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.397104] ehci_hcd 0000:00:1d.0: debug port 2
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.401083] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.401096] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0707000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.416816] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.416932] hub 2-0:1.0: USB hub found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.416935] hub 2-0:1.0: 3 ports detected
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.416976] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.416984] uhci_hcd: USB Universal Host Controller Interface driver
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.417022] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.420747] i8042: Detected active multiplexing controller, rev 1.1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422626] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422632] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422639] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422640] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422642] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422748] mousedev: PS/2 mouse device common for all mice
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422935] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.422966] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423032] device-mapper: uevent: version 1.0.3
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423078] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423145] cpuidle: using governor ladder
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423243] cpuidle: using governor menu
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423244] EFI Variables Facility v0.08 2004-May-17
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423406] TCP cubic registered
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423486] NET: Registered protocol family 10
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423822] NET: Registered protocol family 17
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423832] Registering the dns_resolver key type
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423900] PM: Hibernation image not present or could not be loaded.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.423908] registered taskstats version 1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.438810] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.447902]   Magic number: 8:432:46
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.448065] rtc_cmos 00:06: setting system clock to 2012-04-02 22:02:52 UTC (1333404172)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.449439] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.449440] EDD information not available.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.450711] Freeing unused kernel memory: 988k freed
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.450848] Write protecting the kernel read-only data: 12288k
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.455303] Freeing unused kernel memory: 2032k freed
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.458632] Freeing unused kernel memory: 1388k freed
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.541653] sdhci: Secure Digital Host Controller Interface driver
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.541657] sdhci: Copyright(c) Pierre Ossman
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.541891] sdhci-pci 0000:07:00.0: SDHCI controller found [197b:2382] (rev 80)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.541918] sdhci-pci 0000:07:00.0: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.541969] sdhci-pci 0000:07:00.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.541984] mmc0: no vmmc regulator found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.542015] Registered led device: mmc0::
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.542056] mmc0: SDHCI controller on PCI [0000:07:00.0] using ADMA
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.542068] sdhci-pci 0000:07:00.2: SDHCI controller found [197b:2381] (rev 80)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.542082] sdhci-pci 0000:07:00.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.542087] sdhci-pci 0000:07:00.2: Refusing to bind to secondary interface.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.542094] sdhci-pci 0000:07:00.2: PCI INT B disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544466] jme: JMicron JMC2XX ethernet driver version 1.0.8
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544535] jme 0000:07:00.5: PCI INT C -> GSI 17 (level, low) -> IRQ 17
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544553] jme 0000:07:00.5: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544561] ahci 0000:00:1f.2: version 3.0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544570] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544625] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544669] ahci: SSS flag set, parallel bus scan disabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544715] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544718] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.544723] ahci 0000:00:1f.2: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.545629] jme 0000:07:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:00:90:f5:a0:53:c4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561349] scsi0 : ahci
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561488] scsi1 : ahci
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561573] scsi2 : ahci
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561645] scsi3 : ahci
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561713] scsi4 : ahci
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561768] ata1: SATA max UDMA/133 abar m2048@0xf0708000 port 0xf0708100 irq 41
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561773] ata2: SATA max UDMA/133 abar m2048@0xf0708000 port 0xf0708180 irq 41
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561775] ata3: DUMMY
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561777] ata4: DUMMY
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.561780] ata5: SATA max UDMA/133 abar m2048@0xf0708000 port 0xf0708300 irq 41
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.708189] usb 1-1: new high speed USB device number 2 using ehci_hcd
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.840561] hub 1-1:1.0: USB hub found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.840728] hub 1-1:1.0: 6 ports detected
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.879735] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.917565] ata1.00: ATA-8: ST9320423AS, 0002SDM1, max UDMA/133
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.917570] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.919658] ata1.00: configured for UDMA/133
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.919906] scsi 0:0:0:0: Direct-Access     ATA      ST9320423AS      0002 PQ: 0 ANSI: 5
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.920031] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.920044] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.920078] sd 0:0:0:0: [sda] Write Protect is off
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.920081] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.920100] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.951560] usb 2-1: new high speed USB device number 2 using ehci_hcd
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.952607]  sda: sda1 sda2 < sda5 >
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    1.952902] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.079214] Refined TSC clocksource calibration: 2659.981 MHz.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.079222] Switching to clocksource tsc
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.083916] hub 2-1:1.0: USB hub found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.083959] hub 2-1:1.0: 8 ports detected
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.238826] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.255673] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633C, TM01, max UDMA/100
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.255678] ata2.00: applying bridge limits
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.272878] ata2.00: configured for UDMA/100
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.276897] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633C  TM01 PQ: 0 ANSI: 5
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.284025] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.284030] cdrom: Uniform CD-ROM driver Revision: 3.20
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.284184] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.284239] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.354728] usb 2-1.5: new full speed USB device number 3 using ehci_hcd
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.601909] ata5: SATA link down (SStatus 0 SControl 300)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.943103] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    2.943106] EXT4-fs (sda1): write access will be enabled during recovery
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    3.029537] EXT4-fs (sda1): recovery complete
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [    3.030014] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.576989] type=1400 audit(1333404188.666:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=403 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.577367] type=1400 audit(1333404188.666:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=403 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.577598] type=1400 audit(1333404188.666:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=403 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.602745] mei: module is from the staging directory, the quality is unknown, you have been warned.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.603018] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.603027] mei 0000:00:16.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.606598] lp: driver loaded but no devices found
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.618112] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.618117] Disabling lock debugging due to kernel taint
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.623334] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.626269] Adding 6148092k swap on /dev/sda5.  Priority:-1 extents:1 across:6148092k 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.627873] jmb38x_ms 0000:07:00.3: PCI INT C -> GSI 17 (level, low) -> IRQ 17
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.627882] jmb38x_ms 0000:07:00.3: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.639913] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.639916] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.640046] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.640056] iwlagn 0000:06:00.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.640168] iwlagn 0000:06:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.663529] iwlagn 0000:06:00.0: device EEPROM VER=0x11f, CALIB=0x4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.663533] iwlagn 0000:06:00.0: Device SKU: 0Xb
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.664666] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.664751] iwlagn 0000:06:00.0: irq 42 for MSI/MSI-X
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.669806] wmi: Mapper loaded
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.724366] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.733021] [fglrx] Maximum main memory to use for locked dma buffers: 5649 MBytes.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.735020] [fglrx]   vendor: 1002 device: 9553 count: 1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.735419] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.735436] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.735441] pci 0000:02:00.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.736252] [fglrx] Kernel PAT support is enabled
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.736273] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.737070] acpi device:02: registered as cooling_device4
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.737154] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.737198] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.750992] cfg80211: World regulatory domain updated:
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.750995] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.750997] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.750999] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.751002] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.751004] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.751006] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.759434] iwlagn 0000:06:00.0: loaded firmware version 8.83.5.1 build 33692
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.759439] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.759520] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.759562] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.759583] Registered led device: phy0-led
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.759613] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.761823] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.888124] hda_codec: ALC272: BIOS auto-probing.
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.978704] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.978771] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.978987] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.979051] HDA Intel 0000:02:00.1: irq 44 for MSI/MSI-X
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.979073] HDA Intel 0000:02:00.1: setting latency timer to 64
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.994646] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   17.994786] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:02:00.1/sound/card1/input8
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.454143] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.742173] init: udev-fallback-graphics main process (914) terminated with status 1
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.750541] type=1400 audit(1333404189.842:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=929 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.751904] type=1400 audit(1333404189.842:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=930 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.752538] type=1400 audit(1333404189.842:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=930 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.752827] type=1400 audit(1333404189.842:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=930 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.755021] type=1400 audit(1333404189.846:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=939 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.755303] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa42000/0xa0000
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.755881] type=1400 audit(1333404189.846:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=938 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.756021] type=1400 audit(1333404189.846:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=939 comm="apparmor_parser"
Apr  2 15:03:09 fatpie-Pangolin-Performance dbus[893]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.795742] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
Apr  2 15:03:09 fatpie-Pangolin-Performance kernel: [   18.816833] ppdev: user-space parallel port driver

```

---

### Post by MacDaddy1660B on 2012-04-03
Ah, nevermind. It logged this same message without the problem coming up. This is also a dead end. Sorry for all the posts. I am just trying really hard to figure out what this is. The intermittent behaviour makes it hard to diagnose.

---

### Post by MacDaddy1660B on 2012-04-05
Hey Isantop,

Here's one for you. I notice that something happens when things go wrong, and I try to reboot, but the BIOS splash screen doesn't come up and the computer doesn't boot. I see that the WLAN and HDD indicator lights on the font of the computer come on (power too, of course). All normal. However, the HDD light will turn off (as it should), yet the WLAN light will remain on and the system will "hang." In a normal boot, the WLAN light will turn off as soon as the BIOS splash screen comes up. Does this mean anything to you?

-Gordon

---

### Post by isantop on 2012-04-06
Not immediately. My initial thoughts are toward the hard drive. Could you try booting the system from a LiveCD with the hard drive removed, then attempt to reboot several times to reproduce the problem?

---

### Post by MacDaddy1660B on 2012-04-09
I did this on two separate occasions and everything worked just fine. I've booted ten separate times, got on LiveCD and surfed the net, did normal stuff, and couldn't get the screen to scramble and subsequent boot problems.

One difference I have noticed: the WLAN light lights up yellow on power-on, where it used to light up red. Strange... ???

Hardware problems are the worst.

-Gordon

---

### Post by isantop on 2012-04-10
> **MacDaddy1660B said:**
> I did this on two separate occasions and everything worked just fine. I've booted ten separate times, got on LiveCD and surfed the net, did normal stuff, and couldn't get the screen to scramble and subsequent boot problems.

One difference I have noticed: the WLAN light lights up yellow on power-on, where it used to light up red. Strange... ???

Hardware problems are the worst.

-Gordon

And booting from the LiveCD with the HDD *inserted* causes it not to boot, right?

If that's the case, it's definitely a bad hard drive. You'll want to log in to your account on our website and open a support ticket to get it replaced.

---

### Post by jadtech on 2012-04-10
here is a thought you said you tried to activate install the post ATI driver I have noticed when you do this and it fails as it always does the first ATI driver becomes inactivated and must be re-installed ..

though it does sound like  the hard drive is having a dramatic slow death , if your live CD has the right driver active that to could be solving the  issue

---

### Post by MacDaddy1660B on 2012-04-10
I am not able to reproduce the problem -- that's the issue. Its totally intermittent. Here's an outline again of what happens:

screen scrambles for no apparent reason (colors and lines all across screen) ---> computer hangs ---> power off ---> attempt to reboot...BIOS splash screen does not show up...screen remains black. WLAN and HDD light-up normally, then turn off and remain off ---> turn off, attempt to boot again several times and still get black screen --> could try inserting a LiveCD at this point, but the computer still does not boot as it doesn't make it past BIOS self-check ---> after N tries, the computer finally decides it wants to boot, BIOS splash shows up, Ubuntu starts.

Most of the time, the machine works fine, and then it gets into the funky mood as described above. Booting from a LiveCD or not makes no difference in getting it to boot back up and out of the funk. Sometimes the problem comes up, and it will reboot on the first try. Sometimes I have to try rebooting for hours before it finally want to work again.

It has not happened since removing the drive this past Saturday. Maybe it needed to be reseated? I'm waiting for it to happen again so that I can remove the drive right away and see if it will boot right away from the LiveCD with no HDD. If this happens, I will know for sure its a faulty drive.

I am also going to check the voltage of the wall power supply when this comes up again. But so far, everything has been running smoothly.

The original ATI driver was re-installed.

Story about the HDD: the original one crashed in this machine one year ago. Its a Seagate 7200 RPM 320GB drive. I got it replaced under the Seagate warranty. They sent me a rebuilt unit. It has performed well since then. Disk self-check says the drive is healthy. Still, I back-up regularly.

The machine is 2 years old and is no longer covered under the System76 warranty. If it turns out that there are any problems with this drive, I will contact Seagate, as my warranty with them is 3 years (I have 1 year left). Much appreciated, though, isantop.

Does the above explanation change anything? Again, thanks for the thoughts and consideration.

---

### Post by isantop on 2012-04-10
> **jadtech said:**
> here is a thought you said you tried to activate install the post ATI driver I have noticed when you do this and it fails as it always does the first ATI driver becomes inactivated and must be re-installed ..

though it does sound like  the hard drive is having a dramatic slow death , if your live CD has the right driver active that to could be solving the  issue

The LiveCD comes without the ATI driver. This is definitely a hard drive failure.

---

### Post by MacDaddy1660B on 2012-04-10
isantop: should I wait for the drive to die completely and send it in to Seagate under warranty? I may have a hard time convincing the guys at Seagate to replace it under warranty in its current state as it works most of the time.

Thanks for you expert advice!

---

### Post by MacDaddy1660B on 2012-04-11
I'm pretty sure that this is the problem. Started acting up again today. Powered down, quickly pulled the HDD and inserted a LiveCD and it booted right up. Did this twice. Let's call this solved. Thanks you guys!!!

---

