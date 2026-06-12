---
title: "How often to reboot?"
date: 2016-09-14
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2016-09-14
I've always known and understood that linux of nearly any kind is capable of amazing uptimes. I've had nothing but success with my server since I switched to Ubuntu 16.04 on it. However twice now after 7 or 8 days of uptime a few little irritations start happening. The Minecraft server gets very laggy and stuttery. We are on a wired network so I've ruled that out. The server itself just runs funny and glitchy. Worked fine after reboot. Second my apt-cacher-ng on the server wouldn't connect when I did a test install on another partition on my laptop, again worked fine after rebooting the server. In addition the server is also direct booting to Kodi for media center purposes. Kodi gets very sluggish after the time and again, rebooting clears it up just fine.

I currently have set a cronjob to run at 4 am every morning to reboot the server. It's just a home server so no big loss, everyone is asleep anyway and the total downtime is under 5 minutes. However it leads me to wonder why am I needing to reboot it at all? As said I've always understood linux servers to have uptimes in the months, years even. This one is doing 7-8 days before it starts glitching out.

Hardware if needed to help understand.

AMD Kabini Quad Core AM1 2.2ghz
8gb ram
120gb samsung evo ssd
1tb wd green spinner hard drive

---

### Post by ian-weisser on 2016-09-14
Applications should not become 'very sluggish' or unreliable due merely to uptime. If you can reproduce the problem reliably, check the Kodi forums to see if you should report it as a bug.

Running 'funny and glitchy' is a bit too vague for us to help you with. Like with Kodi, try to find reliable, reproducible symptoms that a Triager can use on their test system to poke around and discover a cause.

---

### Post by TheFu on 2016-09-14
Can't help without FACTS and DATA.

I can say that my kodi box is routinely up for a month without issues. That box is mainly a media storage device and plex server, but provides NFS for the entire network as well.  It runs a few other things.  Kodi is the main GUI app on it.  It is G3258-based.

My other Linux systems are usually up about a month. I reboot when a new kernel gets installed.  Sometimes that is weekly and sometimes it is quarterly. Just depends. I only patch weekly, Saturday mornings.  

None of my systems feel slow. If they do, it is usually an application problem. Killing/restarting the app fixes it.  I specifically avoid all Java programs/servers to avoid sluggish servers.

For fun, here are some current uptimes:
```
$ ansible -i hosts -a "uptime" powered
 lubuntu | success | rc=0 >>
 14:12:53 up 10 days, 19:21,  7 users,  load average: 0.13, 0.16, 0.18

hadar | success | rc=0 >>
 14:12:54 up 4 days,  5:25,  3 users,  load average: 0.02, 0.05, 0.05

spam2 | success | rc=0 >>
 14:12:54 up 11 days,  4:05,  1 user,  load average: 0.03, 0.04, 0.05

romulus | success | rc=0 >>
 14:12:55 up 11 days,  4:12,  3 users,  load average: 0.70, 0.93, 0.84

vpn | success | rc=0 >>
 14:12:55 up 4 days,  5:25,  1 user,  load average: 0.08, 0.03, 0.05

istar | success | rc=0 >>
 14:12:55 up 8 days,  5:24,  6 users,  load average: 0.07, 0.09, 0.11

xen41 | success | rc=0 >>
 14:12:55 up 11 days,  4:04,  1 user,  load average: 0.00, 0.01, 0.05

zcs43 | success | rc=0 >>
 14:12:54 up 11 days,  4:03,  1 user,  load average: 0.20, 0.29, 0.27

osmc | success | rc=0 >>
 14:12:55 up 15 days, 18:17,  1 user,  load average: 0.64, 0.56, 0.49
...

```

As a server OS gets older, the uptimes go up.  My 12.04 server was seeing uptimes over 90 days before being replaced with a 14.04 server.  Newer kernels tend to need more patching. Just sayin'.  If you want longer uptimes, load up 12.04 until support ends in March.  Then move to 14.04.x

If you want really long uptimes, avoid GUI code.

---

### Post by aromo2 on 2016-09-14
> **Tadaen_Sylvermane said:**
> I've always known and understood that linux of nearly any kind is capable of amazing uptimes. I've had nothing but success with my server since I switched to Ubuntu 16.04 on it. However twice now after 7 or 8 days of uptime a few little irritations start happening. The Minecraft server gets very laggy and stuttery. We are on a wired network so I've ruled that out. The server itself just runs funny and glitchy. Worked fine after reboot. Second my apt-cacher-ng on the server wouldn't connect when I did a test install on another partition on my laptop, again worked fine after rebooting the server. In addition the server is also direct booting to Kodi for media center purposes. Kodi gets very sluggish after the time and again, rebooting clears it up just fine.

I currently have set a cronjob to run at 4 am every morning to reboot the server. It's just a home server so no big loss, everyone is asleep anyway and the total downtime is under 5 minutes. However it leads me to wonder why am I needing to reboot it at all? As said I've always understood linux servers to have uptimes in the months, years even. This one is doing 7-8 days before it starts glitching out.

Hardware if needed to help understand.

AMD Kabini Quad Core AM1 2.2ghz
8gb ram
120gb samsung evo ssd
1tb wd green spinner hard drive


Post the output of top when the server is sluggish.  It could be a memory leak from one or more applications, long processor wait, need to clean up cache, etc.  Top should give you an idea of what could be happening.

---

### Post by TheFu on 2016-09-14
> **aromo2 said:**
> Post the output of top when the server is sluggish.  It could be a memory leak from one or more applications, long processor wait, need to clean up cache, etc.  Top should give you an idea of what could be happening.

Good place to start.  Could be other things.  Basically, check:
a) CPU
b) RAM use / Swap
c) I/O
c1) Disk
c2) Network

Those things should lead back to a process and a parent process and a parent process, so you can determine what the slowdown is.  All sorts of different tools for this. My preferred method is to install something like **Munin** and capture stats for a few days before making any decisions. [https://www.howtoforge.com/tutorial/server-monitoring-with-munin-and-monit-on-ubuntu-16-04-lts/](https://www.howtoforge.com/tutorial/server-monitoring-with-munin-and-monit-on-ubuntu-16-04-lts/)  For example, I found that USB3 storage, via an addon USB3 card, sucked all the I/O capacity on one of my systems (not any of the others). Determined this when backups that should have been faster actually got slower with the change to USB3 for the backup disk. Moved the backups to a different system and times dropped back down even though the other system has much slower CPU, with less RAM.  OTOH, the USB3 performance was great.

Anyway, hope all this is helpful.

---

### Post by Tadaen_Sylvermane on 2016-09-14
All replies are helpful. I rebooted the other day, ill check in in a few days with stats when it's sluggish. I can't help but think that the Java thing may be the culprit though. Seems to be a common theme with minecraft servers people run at home on the few places I've searched for that specifically. Some suggest using Oracles java instead of the openjdk. At any rate I'll trace it down when it starts lagging out again, shouldl be a few days. Thanks for suggestions.

---

### Post by mastablasta on 2016-09-15
as mentioned above check with top command to see what is makign it slugish and for possible memorry leaks.

also Kodi starts acting weird on my RaspberryPi as well but usually only after a few days. slugish, slow menues, not displaying the video or subtitles etc. a reboot will usually solve it.

also - 5 minute to reboot on that setup?! :o

---

### Post by TheFu on 2016-09-15
The only time I see kodi get sluggish is when it has been playing weird video formats ... wma, flv, stuff like that. With mpeg2/h.264/aac/ac3/mp3, no issues in R-pi v2.  Also, no need to reboot the box, just restart kodi.  The base OS is fine. Quick OSMC restart - just kill the kodi process and systemd brings it back up.

---

### Post by Tadaen_Sylvermane on 2016-09-25
Update. I discovered I was swapping pretty bad. With 2gb of ram dedicated to the Minecraft server alone, rest of system and I was hitting the swappiness threshold pretty quick. Changing the swappiness setting to 10 and it is running like a dream a week down the road. Running noticeable better all around to be honest. I don't know if its placebo but it feels better to me, wife also commented on it. Marking as solved.

---

