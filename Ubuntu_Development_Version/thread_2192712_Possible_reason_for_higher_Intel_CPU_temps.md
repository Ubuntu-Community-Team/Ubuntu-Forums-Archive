---
title: "Possible reason for higher Intel CPU temps"
date: 2013-12-09
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-12-09
I happened to read this a couple hours ago:

[http://www.phoronix.com/scan.php?page=news_item&px=MTUzODc](http://www.phoronix.com/scan.php?page=news_item&px=MTUzODc)

> Intel Developer Finds 50 Watt Power Regression In Linux

I had noticed in both Trusty and Saucy that my Intel Atom 230 ran a full 20 degrees Fahrenheit warmer than in previous versions of Ubuntu (and flavors) but I never could find a process that was consuming more resources. So, after reading that, I busted out my P3 Kill-A-Watt and sure as heck - at idle I'm still consuming nearly 17 watts in Trusty @idle whereas in Precise I'm consuming less than 3 watts :D

---

### Post by zika on 2013-12-09
1. Put in kernel boot command-line ```
idle=mwait
```
2. After boot do ```
dmesg|grep idle
```
3. With ```
uname -srvmpio
```post Your result(s).
I'm trying to see what kernel do honor mwait since I'm using poll for least latency with```
intel_idle.max_cstate=0 processor.max_cstate=0
```
Thank You.

---

### Post by kansasnoob on 2013-12-09
> **zika said:**
> 1. Put in kernel boot command-line ```
idle=mwait
```
2. After boot do ```
dmesg|grep idle
```
3. With ```
uname -srvmpio
```post Your result(s).
I'm trying to see what kernel do honor mwait since I'm using poll for least latency with```
intel_idle.max_cstate=0 processor.max_cstate=0
```
Thank You.

It may be a day or two until I get around to that :(

Just lots of cold weather projects stacking up here.

---

### Post by pnarciso on 2013-12-09
Isn't this problem related to the new intel p_state cpu governor. When using it, my cpu never idles to 800mhz and idles at 3.5ghz instead. Ubuntu doesn't enable intel p_state by default.

---

### Post by kansasnoob on 2013-12-10
> **zika said:**
> 1. Put in kernel boot command-line ```
idle=mwait
```
2. After boot do ```
dmesg|grep idle
```
3. With ```
uname -srvmpio
```post Your result(s).
I'm trying to see what kernel do honor mwait since I'm using poll for least latency with```
intel_idle.max_cstate=0 processor.max_cstate=0
```
Thank You.

Sorry for the delay, hope I did this right:

```
lance@lance-desktop:~$ dmesg|grep idle
[    0.000000] Malformed early option 'idle'
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.12.0-7-generic root=UUID=f49bbc53-3369-47cf-89ae-c25795762898 idle=mwait
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.106297] cpuidle: using governor ladder
[    0.106340] cpuidle: using governor menu
[    1.129214] intel_idle: MWAIT substates: 0x10
[    1.129233] intel_idle: v0.4 model 0x1C
[    1.129239] intel_idle: lapic_timer_reliable_states 0x2
lance@lance-desktop:~$ uname -srvmpio
Linux 3.12.0-7-generic #15-Ubuntu SMP Sun Dec 8 23:42:09 UTC 2013 i686 i686 i686 GNU/Linux

```

---

### Post by PJs Ronin on 2013-12-11
..

---

### Post by kansasnoob on 2014-01-31
I'm not seeing this anymore since upgrading to 3.13.0-6-generic :D

---

### Post by pqwoerituytrueiwoq on 2014-01-31
> **pnarciso said:**
> Isn't this problem related to the new intel p_state cpu governor. When using it, my cpu never idles to 800mhz and idles at 3.5ghz instead. Ubuntu doesn't enable intel p_state by default.
that is not how intel_pstate works
the clock speed changes dynamically for every 1% from 800MHz to 3.5GHz
here is a chart generating script to show you the clock speeds over time using intel_pstate
[http://pastebin.com/PYj4wwCj](http://pastebin.com/PYj4wwCj)
requires [php5-cli](apt:php5-cli) be installed

---

