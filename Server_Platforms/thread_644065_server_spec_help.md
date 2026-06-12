---
title: "server spec help"
date: 2007-12-18
forum: Server Platforms
---

### Post by reckless2k2 on 2007-12-18
I'm currently running quite a few different services on one box. I know this isn't the ideal situation but electric bills and space are the major issues for consolidating to one machine. The machine specs are as follows:
[LIST]
[*]P4 HT 2.8GHz
[*]3GB RAM
[*]256MB nvidia
[*]250GB SATA I 7200RPM
[*]gigabit ethernet card
[/LIST]

The services are as follows:
[LIST]
[*]zimbra mail server
[*]vsftpd
[*]apache2 (serving several sites with little traffic)
[*]wordpress
[*]gallery2
[/LIST]

I have no GUI and admin the box via ssh. I've noticed lag on page rendering in general across the apache sites and gallery2. I'm concerned that I need a higher spec machine and was looking for advice if that was the case.  It may be possible that I need to make some apache or php tweaks to fix this though. zimbra, vsftpd, and wordpress seem to be fine. The pictures/content on the apache and gallery pages is painfully slow though. 

Any advice would be appreciated.

---

### Post by koenn on 2007-12-18
run  'top"

it will give you a first idea of system resources, what programs are using them, and how much. 
It's kinda pointless to invest in more RAM, if the CPU is the bottleneck. 
It's also pointless to invest in a new server, if the network is the bottleneck (& responsible for eg slow rendering of pictures).

---

### Post by mellowd on 2007-12-18
Install Munin. It's will show you exactly what is causing the slowdown. It monitors all kinds of things like apache, cpu, memory, hard disks, mysql and so on.

How many hits are you getting on that server? Is it just a home server? Commercial? What kind of internet connection does it have?

---

