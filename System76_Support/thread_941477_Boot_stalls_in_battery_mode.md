---
title: "Boot stalls in battery mode"
date: 2008-10-08
forum: System76 Support
---

### Post by ajlewis2 on 2008-10-08
I don't know when this began, because I usually run my Darter (white - DARU1, I think) plugged in to an outlet.  I have Gutsy on it with 2.6.24-21-generic kernel.

It does boot in recovery mode showing the stall here at 16.741531 (dmesg):

[   16.385501] ACPI: SSDT 3F7BEE30, 0B9F (r1    AMI   CPU2PM        1 INTL  2002026)
[   16.389423] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   16.389664] ACPI: Processor [CPU2] (supports 8 throttling states)
[   16.741531] ACPI: Thermal Zone [THRM] (46 C)
[   16.849513] Clocksource tsc unstable (delta = -49992252700 ns)
[   16.850489] Time: hpet clocksource has been installed.

This morning I walked away from it and I think it took a couple minutes before it went on to the next step.  It will go on faster than that if I plug it in at the point where it stalls.

It looks like something with power management.  I'm sorry that I can't say when it developed, because it has been months since I booted on battery only.  

Any thoughts on what might be the problem and correction?

Thanks,
Anita

---

### Post by thomasaaron on 2008-10-08
When it stalls, try to make it move forward by hitting the space bar a couple of times?

If that works, it may have something to do with your clocksource (as would seem to be indicated by the log you posted), and I might have some suggestions.

Does it do it every time you boot with a battery?

---

### Post by perce on 2008-10-08
I have a similar problem. It doesn't always happen to me. When it happens, it happens twice or three times in a row, and then it goes away for a while.

---

### Post by ajlewis2 on 2008-10-08
Thanks Thomas.

Pressing the space bar a few times does not cause it to continue.

It has happened every time I boot with the battery only.  After 3-4 minutes it continues and completes the boot.  

I noticed tonight when I reboot that there is a message as the system is going down that says that it is not able to access the Hardware Clock by any known method.  You mentioned the Clock; so I thought maybe that is connected.  

Anita

---

### Post by thomasaaron on 2008-10-08
Anita and Perce,

I did some googling on that error (the one Anita mentioned) and there are quite a few mentions of it. Here is what I'm seeing...

1. For some people, updating their computer fixed the problem -- so this might go away on its own.
2. I read a pretty good explanation of how Windows dual-booting might be a suspect. Do you two have Windows dual-booted?
3. Try resetting your cmos. Disconnect your ac and battery and stick a paper clip through the re-set hole on the bottom (it has an arrow on each side of it). Hold the cmos button for 15 seconds. Then hook up your battery and see if it still happens.

---

### Post by ajlewis2 on 2008-10-08
No Windows installed on here.

I turned off the machine, unplugged, pulled the battery, and depressed that button with a paper clip for 15-20 seconds.  This did not change the boot problem.  I tried a second time to make sure.

I am doing any upgrades that come along with the updater. I said I have Gutsy, but actually I upgraded to Hardy quite some time ago.  /etc/apt/sources.lst indicates 2008-07-04; so I imagine that is when I upgraded.

Anita

---

### Post by lwb1086y on 2008-10-11
[size=2]bump up then lurk[/size]----------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU30U016.jpg[/img]Welcome to our site:[wow power leveling](http://www.yoyo-power-leveling.com/),everyday [wow powerleveling](http://www.swow-power-leveling.com/),[world of warcraft power leveling](http://www.toppowerlevel.net/),[world of warcraft powerleveling](http://www.wow-power-leveling1.com/),cheap [wow gold](http://www.toppowerlevel.net/buy.php)

---

