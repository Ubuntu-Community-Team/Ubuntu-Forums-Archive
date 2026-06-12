---
title: "Increasing CPU usage"
date: 2012-12-03
forum: Server Platforms
---

### Post by wishyou on 2012-12-03
Hi!

I have a vanilla Ubuntu LTS 12.04 Server installation with a weird problem.
Over time the cpu usage increases slowly and I cant figure out why.

Any pointers? See the RRD graph below, bars are load averages, line is instant cpu usage. The drops are reboots.

[ATTACH]228151[/ATTACH]

The server is pretty much idle, I have apache, mysql and postfix(local use only, with smarthost) running. In addition I've added some data gathering with RRDTools, smartmontools, lm-sensors and nut.

top og htop isnt showing anything out of the ordinary.

Any ideas?

(This is running on an Athlon 1700+ with 1 GB ram)

Regards,
Wish

---

### Post by thnewguy on 2012-12-03
I would suggest looking at your processes with "top" and seeing which one (or which ones) are using the most CPU. Once you know which processes are eating up your CPU then it will be much easier to figure out what is going wrong.

---

### Post by wishyou on 2012-12-04
Hi!

Thanks for replying.

The thing is I've already tried top and htop and nothing points out.
I've got a lot of processes running, all of them at 0.0 cpu at any point in time. Every now and then my RRD-stuff, or apache or mdraid shows up with a few processes at 1.0.

The load/idle numbers above the process list reflects the expected numbers better, but still i cant figure out exactly what is causing this.

At this point I'm inclined to let it run and simply wait until the usage reaches 100, and then figure out whats hanging... :|

Regards,
Wish

---

### Post by thnewguy on 2012-12-04
Without any further information my best guess is that the increased load times reflect disk IO and wait times rather than plain CPU usage. Perhaps when the server goes a long time without rebooting there are large log files being seeked through/scanned, or maybe swap space is getting used, causing more disk IO. My guess would be that memory and log fiels are getting cleaned at reboot, causing the load/IO wait to reduce. But it's just a shot in the dark until something shows up on top or iotop.

---

