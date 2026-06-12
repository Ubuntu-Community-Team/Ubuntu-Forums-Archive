---
title: "sudden high load average but cpu idle"
date: 2017-03-31
forum: Server Platforms
---

### Post by Mad_Turnip on 2017-03-31
[COLOR=#1D2129][FONT=Helvetica]Hi,

I keep searching the issue but no luck. I have a VPS (SSD, 3G RAM, 1core) which was running perfect until about a week ago. The load average was around 02.-0.6, rarely over 1 - especially when doing backup of virtualservers. I am using Roundcube as webmail client. In the last week I saw more often alerts about load average over 1 and Roundcube is running like dead (even 500 errors with premature end script 31 sec timeout - apache is running in fcgi mode.

I added 1 core and 1G of RAM, now I have VPS (SSD, 4G RAM, 2core) but it is the same issue. Running top in console reveals a lot of CPU idle time with wa around 0.1-0.3 but load average is still high around 2-3 even 4/1min.

I scanned with rkhunter, maldetect, I have csf and lfd running, nothing strange in logs, I checked all the virtualhosts access logs for POST or any suspicious spike in traffic. Nothing. But the webmin, roundcube and some sites are running like crap.

The VPS details:

[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit]Operating system Ubuntu Linux 14.04
Webmin version 1.831 
Virtualmin version 5.07
Theme version Authentic Theme 18.40
Firewall version ConfigServer Security & Firewall 10.05 
 Time on system Friday, March 31, 2017 11:06 AM
Kernel and CPU Linux 2.6.32-042stab102.9 on x86_64
Processor information Intel(R) Xeon(R) CPU L5639 @ 2.13GHz, 2 cores[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2017-03-31
Flush the VPS and rebuild it.  You've probably been hacked.  Any time there are radical changes in workload, being hacked must be the first assumption.

After you rebuild using all currently supported AND patched versions of all software, if it happens again then figure out exactly which process it eat all the RAM and CPU and look for reported bugs in those. For example, Java has had a problem due to time changes a few times - so if any of these are java-based and the issue started around the DST change-over .... that could be it.

Gotta ask - why are you running an out of date kernel?  Currently patched and maintained 14.04 started with  3.13.0 kernels.

12.04.5 runs 3.2.0-124-generic kernels - and support for that ends in about 1 month.

Definitely time for a fresh install (not an upgrade) and I'd stop using webmin for more than a few reasons.

---

### Post by darkod on 2017-03-31
Because unfortunately on many VPS depending on how they do the virtualization, you don't actually control the kernel. :( It's shared... Which might be one additional suspect for high cpu, shared resources...

I have sen this in Digital Ocean VPS, the kernel is what it is, and any dist-upgrade you do installs a newer kernel but a reboot does not load it... :(

---

