---
title: "IGMP/pimp vuln. detected by Nessus"
date: 2009-01-21
forum: Security
---

### Post by ju2wheels on 2009-01-21
Hi everyone, I was recently doing a Nessus scan on my Ubuntu pc from a Windows machine running the Nessus scanner. I honestly didnt expect it to find anything beyond my open SSH/web servers, which for the most part it did aside from one security hole it found described here: [http://www.nessus.org/plugins/index.php?view=single&id=10179](http://www.nessus.org/plugins/index.php?view=single&id=10179) .

Essentially its a DOS vulnerability and Im not sure how to fix the problem or if its a false positive and I should ignore it. 

Based on my google searching, all I could find was that earlier versions of the Linux kernel were vulnerable to this, however Im using Intrepid with the latest updates so my kernel version is newer and should be patched against this.

My question is should I file this as a bug against the current kernel, is there a fix anyone knows of, or is there a way for me to determine if its a false positive?

The only reason im concerned is because some posts ive read suggest that this vulnerability could also be exploited to gain root privs on the machine as well.

Thanks.

---

### Post by Titan8990 on 2009-01-21
Personally, I would just follow the advice of what you posted:


"Solution : filter incoming IGMP traffic"


Add it your iptables rules.

---

### Post by ju2wheels on 2009-01-22
I use Firestarter, im not familiar with working with iptables directly yet.

Is there anyway I can use Firestarter to block this? Or what would be the command I would need to run. Ive google for how to block it but all I come up with are hits for ICMP.

---

