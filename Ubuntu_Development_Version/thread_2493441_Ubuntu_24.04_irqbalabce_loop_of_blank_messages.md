---
title: "Ubuntu 24.04 irqbalabce loop of blank messages"
date: 2023-12-15
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-12-15
After recent updates I see a loop of  irqbalabce blank messages: [https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/2046470](https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/2046470) 
Tested on 2 different install on same PC

---

### Post by MAFoElffen on 2023-12-15
I commented and asked why we still have this package as installed by default. I thought is was removed from Debian as a default install a while ago. Many have told me that, though I can't find "the when" of that to document that in this bug report.

---

### Post by Doug S on 2023-12-17
I have not used my 24.04 server VM since early Novermber. I upgraded to today and get not the same but similar messages in /var/log/syslog:

```

doug@serv-nn:~$ [COLOR="#FF0000"]grep irqb /var/log/syslog[/COLOR]
...
2023-12-17T15:54:15.096422+00:00 serv-nn irqbalance[607]: Selecting irq 27 for rebalancing
2023-12-17T15:54:25.093560+00:00 serv-nn irqbalance[607]: #012#012#012-----------------------------------------------------------------------------
2023-12-17T15:54:35.096447+00:00 serv-nn irqbalance[607]: #012#012#012-----------------------------------------------------------------------------
2023-12-17T15:54:55.096612+00:00 serv-nn irqbalance[607]: message repeated 2 times: [ #012#012#012-----------------------------------------------------------------------------]
2023-12-17T15:55:05.096251+00:00 serv-nn irqbalance[607]: #012#012#012-----------------------------------------------------------------------------
2023-12-17T16:04:15.096904+00:00 serv-nn irqbalance[607]: message repeated 55 times: [ #012#012#012-----------------------------------------------------------------------------]
2023-12-17T16:04:25.095536+00:00 serv-nn irqbalance[607]: #012#012#012-----------------------------------------------------------------------------
2023-12-17T16:06:15.096174+00:00 serv-nn irqbalance[607]: message repeated 11 times: [ #012#012#012-----------------------------------------------------------------------------]
2023-12-17T16:06:25.097236+00:00 serv-nn irqbalance[607]: #012#012#012-----------------------------------------------------------------------------
2023-12-17T16:08:05.096865+00:00 serv-nn irqbalance[607]: message repeated 10 times: [ #012#012#012-----------------------------------------------------------------------------]
2023-12-17T16:08:05.097288+00:00 serv-nn irqbalance[607]: Selecting irq 27 for rebalancing
2023-12-17T16:08:15.096398+00:00 serv-nn irqbalance[607]: #012#012#012-----------------------------------------------------------------------------
```

I added "affects me to" to the bug report.

---

### Post by MAFoElffen on 2023-12-17
@Doug S -- 

Was pulled from being a default install in Debian 11 (as I reported there). None of RHEL or SUSE branch have it installed as default installed. Would you know why Ubuntu is still holding onto that as a default installed? It was found as not to really help. Or was it? Just trying to understand that perspective. Am I missing something there? Just curious.

I figure if someone here might know, it might be "you".

It is not maintained by kernel...
```

mafoelffen@noble-d05:~$ apt-cache show irqbalance
Package: irqbalance
Architecture: amd64
Version: 1.9.3-1
Priority: standard
Section: utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Paride Legovini <paride@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 145
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: libc6 (>= 2.38), libcap-ng0 (>= 0.7.9), libglib2.0-0 (>= 2.36.0), libncursesw6 (>= 6), libnuma1 (>= 2.0.11), libsystemd0, libtinfo6 (>= 6)
Filename: pool/main/i/irqbalance/irqbalance_1.9.3-1_amd64.deb
Size: 49238
MD5sum: 51aaf7d18ca9d715c59ba254dcb4f917
SHA1: 854d6e7227eb8608d53dfb09b2d6f115b71399bf
SHA256: 5a677125af1e801b1996a80925a71118d4b30084b52c0895791f7592bc6fb381
SHA512: a9b33f9a3e3eab1bcc9ece9b936cca9a528976831887f5ac2e6a1f7b3fd6284734871039a41e6dba37e03f941447b0b13c5fd77ba7a630c2989ae0a34fd4024f
Homepage: https://github.com/Irqbalance/irqbalance
Description-en: Daemon to balance interrupts for SMP systems
 Daemon to balance interrupts across multiple CPUs, which can lead to better
 performance and IO balance on SMP systems. This package is especially useful
 on systems with multi-core processors, as interrupts will typically only be
 serviced by the first core.
 .
 Note: irqbalance is not useful if you don't have more than one CPU core.
Description-md5: fa005f48c9a59b467ea65c0ddb10ffa9
Task: standard

```
I think the reasoning discussed back then was that kernel has this logic in-kernel now, right? I don't remember the specifics now. It was pulled from kernel (CONFIG_IRQBALANCE) back about 2.6.X... That's when it became an external daemon. But then something else happened about 2019...

That was after this:
[https://github.com/Irqbalance/irqbalance/issues/59](https://github.com/Irqbalance/irqbalance/issues/59)

---

### Post by #&amp;thj^% on 2023-12-17
I added me to it as well.

---

### Post by Doug S on 2023-12-17
> **MAFoElffen said:**
> @Doug S -- 

Was pulled from being a default install in Debian 11 (as I reported there). None of RHEL or SUSE branch have it installed as default installed. Would you know why Ubuntu is still holding onto that as a default installed? It was found as not to really help. Or was it? Just trying to understand that perspective. Am I missing something there? Just curious.I do not know anything about IRQ balancing, and can not provide knowledgeable input.

EDIT: Anyway, based on the input, it seems the service can just be disabled, so I have done so:
```
doug@serv-nn:~$ [COLOR="#FF0000"]systemctl status irqbalance[/COLOR]
&#9675; irqbalance.service - irqbalance daemon
     Loaded: loaded (/lib/systemd/system/irqbalance.service; disabled; preset: enabled)
     Active: inactive (dead)
       Docs: man:irqbalance(1)
             https://github.com/Irqbalance/irqbalance
```

---

### Post by #&amp;thj^% on 2023-12-17
I was curious as well but this helps me a bit: [https://www.baeldung.com/linux/irqbalance-modern-hardware](https://www.baeldung.com/linux/irqbalance-modern-hardware)

---

### Post by Doug S on 2023-12-19
I have been trying to test with and without the irqbalance service enabled on my physcial 20.04 test server and my 24.04 VM, with the objective of revealing any performance different between enabled/disabled. All tests chosen for a high rate of IRQs per second:

Test 1: 20.04 test server: Compile the kernel: Very similar times, with the irgbalance disabled a few seconds faster.
Test 2: 20.04 test server: 6 pairs of ping pong token passing rings. The irqbalance disabled case was a little faster.
Test 3: 24.04 VM server: 2 pairs of ping pong token passing rings: The irqbalance disabled case was a little faster. (4.46225 verses 4.65575 uSec per loop, 4.3%)
Test 4: iperf3 between the 2 servers: The irqbalance disabled case was a little faster. (60.8 verses 59.7 Gbits/sec, 1.8%)

For test 4: I did observe this:
```
2023-12-18T23:35:19.134221+00:00 serv-nn irqbalance[612]: Selecting irq 27 for rebalancing
2023-12-18T23:35:49.127125+00:00 serv-nn irqbalance[612]: Selecting irq 28 for rebalancing
2023-12-18T23:35:59.133802+00:00 serv-nn irqbalance[612]: Selecting irq 25 for rebalancing
2023-12-18T23:40:09.133663+00:00 serv-nn irqbalance[612]: Selecting irq 14 for rebalancing
```

Conclusion: I can not show any benefit for the irqbalance service, but admit I merely might not have figured out the proper way to reveal its abilities to improve performance.

---

### Post by #&amp;thj^% on 2023-12-19
I did not like the spam logs, so I removed it:
```
sudo apt remove irqbalance
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  irqbalance
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
After this operation, 148 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 262599 files and directories currently installed.)
Removing irqbalance (1.9.3-1) ...
Processing triggers for man-db (2.12.0-1) ...
```
If there is a difference I don't notice it.

2 days of testing it, so far my findings (Non Server install here)[list]
[*]irqbalance doesn't support fully all kernel features to an example a turning on/off core threads supported by the extension. If you do have irqbalance package and turn off some cores you can get freezes or not working devices like wi-fi, bluetooth, video cards, sound cards...
[*]irqbalance is not a part of the Linux kernel.
[*]It designed for special server configurations with many RAID/HDD/SDD controllers.
[*]Only Debian Flavors have the irqbalance installed because Debian is very Server oriented. Red Hat doesn't have installed irqbalance by default but it doesn't make Red Hat less server freindly.
[*]It keeps all Linux core threads working so its not good for power saving, especially for laptops.
[*]Any user-space application (like games, compilation...) can not get 100% of CPU resources on any thread because it's always sharing this resources with IO tasks.
[/list]
NOTE: I not suggesting to anyone to remove it, I just like mucking about in testing.

---

### Post by Doug S on 2024-01-05
Have you all seen the activity on the two bug reports? [first]("https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/2046470"), [second]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1833322"). I took the opportunity to add my 2 cents to the second one.

---

### Post by #&amp;thj^% on 2024-01-05
I liked your 2cents worth. This is the key wording " Admins on a larger scale can make the opt-in decision and evaluation better than
> expecting every user of Ubuntu to think about an opt-out. "
+1
BTW Debian dose not install it as default:
```
apt policy irqbalance
irqbalance:
  Installed: (none)
  Candidate: 1.9.2-1
  Version table:
     1.9.2-1 600
        600 https://deb.parrot.sh/parrot lory/main amd64 Packages

```

---

### Post by MAFoElffen on 2024-01-07
Dang. A whole lot of discussion and opinions on that second report. I think we started something...

Glad to see that the first, the looped messages, that they found a fix for that.

I had said my piece in the first bug report, that mentioned Debian and RHEL removing it as a default long ago, and mentioned how it was a dormant bug report from 2019... (The second)

Once that got revived and started activity again on that old Bug Report, I restated what I found, and added what seems to be current with that now. We do have the facility to change where that is installed as a default or not, based on our packaging systems for desktop and server. But I don't know that even then, that it should be "required", instead of optional. My choice would be for optional.

I did find two other good reads on irqbalance (links are there in my comment). Interesting on what SUSE said about it, even though they decided to keep it as default install, was that the first step to performance tuning was to disable it... That's how I read that quote. But at least they support that decision with "Here's how to do that manually to tune the load balancing better..." The blog from Oracle was informative on how it makes those decisions, but follows suit with Oracle doc's themselves, as boring, keep cup of coffee in-hand, and hard to stay awake.

It was curious to find out that Ubuntu Cloud images do not have it automatic/installed by-default...

---

### Post by Doug S on 2024-01-07
I have added some test results to the bug report. I guess it'll come down to two ways of thinking:

1.) "providing definitive data showing that a change (i.e. deleting irqbalance) would be beneficial"

verses

2.) "providing definitive data showing that including irqbalance would be beneficial"

The tests to do is the same in both cases, but with different ways of moving forward in the absence thereof.

I will continue to try to think of some good test.

---

