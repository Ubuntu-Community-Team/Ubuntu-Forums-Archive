---
title: "Hello! Beginner at ubuntu. Moved to this OS due to security concerns"
date: 2017-04-21
forum: Security
---

### Post by buttschecks on 2017-04-21
I have been troubled lately by continually being forced to reinstall my original OS, Win10 home... Came with the computer, and I hated it due to all the restrictions, and win7 does not support my chipset.. Lol talk about fail.

Anyways, I've been noticing weird stuff happening, and I don't really know what is wrong, but I know something is definately wrong.

Sitting atm behind a poor firewall, an old d-link, lol again, but it's better than nothing I guess. I had my TP cable connected to the router for just a sec, and all my other devices connected to the wifi stopped, and I got reports in the router logs (i disconnected the cable almost immediately). This is what I got:

> Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:46 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:47 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:47 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:47 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:47 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:49 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:49 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:49 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:49 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:50 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:50 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:50 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:50 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:51 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:51 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:54 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:54 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:54 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:54 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:54 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:54 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:55 2017 Dos Attack type : fragment flooding!! 
Fri Apr 21 14:55:55 2017 Dos Attack type : fragment flooding!!
...+17 lines or so more of this stuff

That was like 10 seconds. With wifi I guess they can't flood due to it being restricted to 10mbit i think... I'm so lost and confused in all of this. On the checklist is getting a good router I guess with DD-wrt firmware, heard it's good? Tomato and some other alt firmware was there too.

I also get a LOT of these in my (poor) routers log:
> Fri Apr 21 14:56:16 2017 Unrecognized attempt blocked from 101.85.*.*:56884 to 46.59.21.22 TCP:1433 
Fri Apr 21 14:56:31 2017 Unrecognized attempt blocked from 176.35.*.*:22359 to 46.59.21.22 TCP:23 
Fri Apr 21 14:57:06 2017 Unrecognized attempt blocked from 109.73.*.*:9191 to 46.59.21.22 TCP:23 
Fri Apr 21 14:57:26 2017 Unrecognized attempt blocked from 163.172.*.*:5153 to 46.59.21.22 UDP:5060

As I'm uncertain whether it's that I'm included in a botnets (again, I'm not really sure what I'm talking about here) list or something, if that's possible, I've decided for now to not reveal any ips. But I can say it's like 37 pages of these logged. Some seem to get through.

I am in need of guidance. Can someone show me the original setparams for 'Ubuntu' in the grubloader? I am beginning to question if mine are legit. Or if I am even sitting on a clean install of Ubuntu, or if it's been compromized already from the start.

This ubuntu version is fresh, but did run it before, and took a while but apparmor got disabled after I did some updates from deb packages to go back to gnome shell, with no keys or whatever it's called. Was dumb I guess. After a while the system went out of control. Did run lg to test whatever that came up, didn't make no sense of my results. But the shell started flipping out on me, maybe I accidently did something by inserting something by mistake, who knows.

What I've been keeping check on is ps -ef, and watch netstat -tonp.

Heres some logs I've saved:
[http://textuploader.com/drqkz](http://textuploader.com/drqkz) <-- this was using tails OS.
[http://textuploader.com/drqk2](http://textuploader.com/drqk2) <-- also tails

This is from this fresh ubuntu install only did apt-update and upgrade, checked the config of deb packages, seemed legit: [http://textuploader.com/drc09](http://textuploader.com/drc09)

I got a lot of more info stored. But I think I'll keep it short. One more thing, this all started when I was living at my moms, now I got my own place, but her computer was never compromized, so it feels like I'm a target for personal reasons? Maybe I'm just overly paranoid but I feel unsafe.

---

### Post by Bucky Ball on 2017-04-22
> **buttschecks said:**
> This ubuntu version is fresh ...

... but which Ubuntu is it??? :-k 

Welcome. Would help greatly if you provided us with release number and flavour.

---

### Post by deadflowr on 2017-04-22
Moved to the *Security* sub-forum

---

### Post by linuxyogi on 2017-04-24
I too was behind an old Dlink. The security is pathetic. [Read this]("https://www.cvedetails.com/vulnerability-list/vendor_id-899/product_id-31624/version_id-182671/D-link-Dir-600l-Firmware-2.05.html") 10 is the worst score. Now I am planning to setup a pfSense box.

---

