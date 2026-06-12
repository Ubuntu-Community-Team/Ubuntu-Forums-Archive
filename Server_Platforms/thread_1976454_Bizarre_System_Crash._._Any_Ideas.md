---
title: "Bizarre System Crash. . Any Ideas?"
date: 2012-05-08
forum: Server Platforms
---

### Post by Bushflyr on 2012-05-08
I noticed my server (Ubuntu 11.10 Server) HDD light was on when nothing was accessing the server. I already had a SSH window open on my Mac. So I tried a few commands to try and see what was going on.

```

[/usr/local/sbin/hourly.active]: htop
-bash: /usr/bin/htop: Input/output error
[/usr/local/sbin/hourly.active]: sudo cat /proc/mdstat
-bash: /usr/bin/sudo: Input/output error
[/usr/local/sbin/hourly.active]: ls
/usr/local/sbin/ls: line 50: 19495 Bus error               /bin/ls $@ 1>&1
[/usr/local/sbin/hourly.active]: la
/usr/local/sbin/ls: line 50: 19500 Bus error               /bin/ls $@ 1>&1
[/usr/local/sbin/hourly.active]: cd
[~]: ls
/usr/local/sbin/ls: line 50: 19507 Bus error               /bin/ls $@ 1>&1
[~]: top
Segmentation fault

```

top, htop, cat, and ls gave errors, but cd worked fine.

I tried a reboot, but wound up with a "no operating system found" sort of error. I had to go to work, so I shut down and switched off the PSU. After coming home I rebooted into recovery, powered down the system normally (halt -p) and rebooted. It came up fine except for a failed sdb in in the raid. It rebuilt fine on the spare. I'm currently running a smart test (smartctl -t long /dev/sdb) but I don't expect any errors as the RAID has dropped disks before and they checked out fine. 

It seems odd thought that just failing a raid disk (the OS is on a separate drive) would take the whole system down.

Any thoughts?

---

### Post by LHammonds on 2012-05-08
Could it be possible that your PSU is failing or doesn't have enough juice to power all your equipment?  I had a PC that just barely have enough PSU to handle my system but I had a lot of drives and one day it just couldn't handle it anymore and had all kinds of problems that looked like HD issues...but checking individual disks seemed OK.  Once a put a new (and more powerful) PSU in the system, the HD problems went away.

LHammonds

---

### Post by Jonathan L on 2012-05-08
Hi Bushflyr

Bus error makes me suspicious of your memory or other basic hardware.  I'd try booting from the Live CD and running a memory test just to make sure.

Kind regards,
Jonathan.

---

### Post by Bushflyr on 2012-05-08
Thanks for the tips. 

The PSU ought not to be failing, it's brand new as of 2 months ago and is a 450w. The online calculators say I should be drawing less than 250w. Is there any way to check it besides swapping it out for another one?

Similarly, the memory is brand new also but has been running for the last month or two. I'll fire up memtest as soon as the smart test finishes and see if anything pops up just to make sure though.

---

