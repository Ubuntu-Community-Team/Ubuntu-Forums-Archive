---
title: "server shutsdown seemingly randomly"
date: 2009-12-18
forum: Server Platforms
---

### Post by gobbledigook on 2009-12-18
Hi!

i'm running Linux server 2.6.28-16-server .

my server seems to shut down randomly... after looking at /var/log/syslog this line is the last thing before i come along and turn it back on!! 

```
Dec 18 13:20:01 server /USR/SBIN/CRON[24195]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

```

can anyone shed any light on this please? if you need other log entries or more info just ask!

thanx!

---

### Post by renkinjutsu on 2009-12-18
That seems like a very normal cron job and shouldn't be causing problems unless some hacker replaced /usr/sbin/update-motd with his own file. But, you said that your server shuts down randomly, if there's no chronological pattern, then it's probably not cron doing it.

---

### Post by Despot on 2009-12-18
Some random ideas:

Are you hooked up to a UPS? It's a long shot, but I've had issues with random shutdowns caused by a Tripp Lite UPS that would shut itself off.

If you *aren't* using a UPS, you might have problems with the power dipping long enough for the system to lose power.

Maybe the power switch is shorting itself out, or possibly there's a BIOS setting that makes the computer shutdown if a certain temperature gets to high.

---

### Post by cdenley on 2009-12-18
I would first determine if it is a hardware or software issue. Perhaps you can try running the memory tester off an ubuntu disc, see if the system randomly shuts down. You can also try replacing the power supply if you have a spare one. Are all the fans spinning on the power supply, case, and CPU heatsink?

---

### Post by gobbledigook on 2009-12-21
thanx for your ideas guys!

i'm using a 500w power supply with 2 x 1tb drives a 300gb and a 40gb as well... the cpu is a 3.4ghz amd single core and i recently cleaned all the fans of dust. I'm not hooked up to UPS... but will investigate the bios temp settings, the box is basically open as it was a temporary measure which is still hanging about!!

:)

---

