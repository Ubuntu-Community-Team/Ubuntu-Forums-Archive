---
title: "server randomly shuts down"
date: 2009-03-23
forum: Server Platforms
---

### Post by flyvin on 2009-03-23
I made my own server about a few weeks ago. Everything was going fine for a while but just today it randomly stoped working:( I plugged in a keyboard and monitor(I usualy just let it run) and saw a black screen. I pressed some keys and nothing happened and the num-lock light didn't come on when I pressed num-lock but the fan and the power light where on. I restarted it and it worked fine. I ignored it but then later on it stoped working again. I did the same thing and it worked again. This is really annoying me and I don't want to have to just restart it all the time

---

### Post by BkkBonanza on 2009-03-23
Sounds like hardware issues. Power down and remove and re-insert any ram modules. Re-seat them firmly. Check connections for other items too. If you do this and it still acts up then at least you'll know it isn't just components working loose due to heat. 

Also check your logs (/var/log/messages) to see if any issues seem to be showing up. At least you can see when it stopped logging stuff - may tell you how long it's working. If you see messages that indicate errors then post them here and maybe people can help with diagnosis. For hardware faults you'll most likely need to figure that out yourself, maybe by trial and error. More often then not loose connections are culprits.

---

### Post by mrsteveman1 on 2009-03-24
I had this problem once with a desktop machine, i figured out that the kernel would load and stop the CPU fan causing it to overheat. It was Suse i think, but i figured out that i had to keep the system from controlling the fan speed because it wanted to turn it off :roll:

That's probably not the problem here, but hardware issues do turn up like this, when stuff just quits working you don't get much indication of why. Check your ram, make sure the CPU isn't too hot, remove any PCI cards you don't actually NEED to have inserted. I have seen PCI cards cause problems depending on which slot they are in.

---

### Post by wkulecz on 2009-03-24
When I get this kind of weirdness, first thing I do, assuming all the fans are running, is replace the power supply.  If its not the problem at least you now have a spare :)

Buy the next larger wattage above the one that's in there now.

--wally.

---

### Post by HermanAB on 2009-03-24
I 2nd the PSU replacement trick.  Also, always, always run a server from a UPS - it will last many years longer if you do.

Check the mother board for distended capacitors.  Even though this is an old manufacturing problem that was supposedly fixed, I still see machines with low quality capacitors that pop their tops.  Once two or three have popped, the machine will become unreliable.  Then you either need to get a powerful temperature controlled soldering iron and replace all electrolitics, or buy a new mother board.

Cheers,

Herman

---

### Post by flyvin on 2009-03-24
It happened again today, so I looked through the system logs. I found this
```
...
Mar 24 05:37:48 Frankenserver kernel: [25277.941938] type=1503 audit(1237887468.477:13): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/3577/net/if_inet6" pid=3578 profile="/usr/sbin/named"
Mar 24 05:57:04 Frankenserver -- MARK --
Mar 24 06:17:04 Frankenserver -- MARK --
Mar 24 06:37:04 Frankenserver -- MARK --
Mar 24 06:37:48 Frankenserver kernel: [28877.946232] type=1503 audit(1237891068.481:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/3577/net/if_inet6" pid=3578 profile="/usr/sbin/named"
Mar 24 06:51:06 Frankenserver syslogd 1.5.0#2ubuntu6: restart.
Mar 24 07:17:04 Frankenserver -- MARK --
Mar 24 15:05:27 Frankenserver syslogd 1.5.0#2ubuntu6: restart.
Mar 24 15:05:27 Frankenserver kernel: Inspecting /boot/System.map-2.6.27-11-server
Mar 24 15:05:27 Frankenserver kernel: Cannot find map file.
Mar 24 15:05:27 Frankenserver kernel: Loaded 45599 symbols from 54 modules.
Mar 24 15:05:27 Frankenserver kernel: [    0.000000] Initializing cgroup subsys cpuset
...

```
On line 7 I noticed there is a big gap in the time. also 15:05:27 (3:00 PM) is about when I restarted it. It said it restarted at 6:51 AM, but I didn't do that.

P.S.
I was checking the hardware inside the computer but I accidentally unpluged it and I had to restart. I'll check it again next time it breaks

---

### Post by BkkBonanza on 2009-03-25
It doesn't seem to show anything to indicate between 07:17 and 15:05 when it went down, except one surmises it was before 07:37 since it never made the 20 minute MARK it's doing after that one.

Does it always happen when your'e not there? Are you sure you don't have power failures or that someone isn't messing with it and unplugging it? 

The restart at 06:51 is perhaps due to software issues or even a failure that was brief enough to trigger a restart but not power off.

---

### Post by flyvin on 2009-03-25
It has never happened when I was there and I doubt anyone is messing around with it. I'm not sure about getting a power outage, because it didn't actually turn all the way off and It's happened three times.

---

### Post by BkkBonanza on 2009-03-25
I think you'll have to solve this by trial and error. I'd try to find a power supply to swap for a test and see if it continues to act up.

---

### Post by flyvin on 2009-03-25
yeah, I'll keep trying. I really don't want to get a new power supply because when I got this computer for free, but it was broken and I got a used power supply to fix it and I don't want to spend to much money. Oh well, hopefully I'll figure it out. If anyone has an idea post it.:)

---

### Post by flyvin on 2009-03-25
oh I just remembered it did happen when I was using it once, so that means it wasn't a power outage.

---

### Post by bryan7878 on 2010-02-16
I have the same problem.  I have a brand new machine and I am running 9.10.  At times it can run for days.  But most of the time it shuts of randomly.  The power is still on, but I loose all controls and have to reboot.  All hardware is perfect.

Any help would be appreciated!

Bryan

---

### Post by flyvin on 2010-02-19
This happened awhile ago so I can't remember exactly what I did. I think I just sort of ignored it for awhile and it went away, but then it started happening again. I figured out that if I hold in the power cord it will stay on, but if I move it just a little bit, the server will shut down, so I had I bad power supply. I replaced the power supply and everything worked fine. I have a really old, used computer though, and you said yours is new, so I don't think it would have a bad power supply. Good luck!

---

### Post by CoolHand on 2010-12-21
If anyone solved this I would like to know the answer.  I have this same issue.  I had the issue on my old home built server and thought it was just getting old.  I thought maybe a power issue.  Hardware...  Well I built a new machine entirely.  Put the LTS server version on it.  New case, power supply, even added a UPS.  It ran for a little more than a month solid then just started shutting down.  It will run for a day or two then just go down.  The box is still up with power but it's like the OS went to a safe shutdown state.  Driving me nuts.

---

### Post by flyvin on 2010-12-21
It ended up being a hardware problem for me. Sorry.

---

