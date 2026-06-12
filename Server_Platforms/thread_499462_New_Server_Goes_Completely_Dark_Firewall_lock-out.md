---
title: "New Server Goes Completely Dark: Firewall lock-out?"
date: 2007-07-12
forum: Server Platforms
---

### Post by hawzor on 2007-07-12
New Dapper Drake server installation runs ssh (alt-port 222), postfix, courier, Apache, and MySQL. Ssh has be conf'd to send keepalive packets.

Here is the bizarre:

Intermittently, all port connections to my new server from my home base (Time Warner cable connection) simply go on hiatus for varying amounts of time, between ~3 and ~15 minutes. Cable connection is perfect, always up. But to me the box has gone dark, "blanked." And then as if by magic, it "just returns."

I have checked extensively with the ISP and there is no (none, zero, wide-open) filtering going on upstream of the box.

I have ran 72 hour ping logging on either side of the upstream router and got 100% throughput, no losses. So no bad patch cable, no bad port, no bad router.

I thought that maybe there was some default firewall rule or IPtables rules in Ubuntu that would lock out my home address by somehow inappropriately assuming my IP was malicious. I am not running **fail2ban**, **portsentry**, **snort**, or other software like this though, though I had **portsentry **installed and active for a moment, then did **apt-get remove **on it when I realized I didn't have the skill to conf the files. It is thus an essentially default installation, and anyway, I never touched those firewall confs or rules. I did try rootkitchecker also, but I don't see how that would have caused the issue, and just removed it after a while.

I worried that cron jobs may have been causing loads or something, but simply turning off cron was no help for the blanking, and anyway, when a blanking episode concludes, examination of syslogs and load averages reveal nothing remarkable just happened.

When I had an episode of "blanking" like this today, I immediately chatted my ISP guy and asked him to run some ping stats alongside me at home. His were perfect, mine were timed out for about 4 minutes. I tried telnet to all open ports and all were dark. I ssh'd to another box and then from there to my subject box and got in. And then the subject box was live again, as if the clouds had lifted. Sound like my home IP is poisoned, but I cannot find any reference to it on my server.

This phenomenon cannot be unique. Anybody have a diagnosis out there?

---

### Post by hawzor on 2007-07-15
Are you guys kidding me? *Nobody* has seen this behavior before? Nothing even a *little* like it?

---

