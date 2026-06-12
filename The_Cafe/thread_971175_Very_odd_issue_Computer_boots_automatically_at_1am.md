---
title: "Very odd issue: Computer boots automatically at 1am, every day"
date: 2008-11-04
forum: The Cafe
---

### Post by altonbr on 2008-11-04
I've been working with computers for almost 5 years and almost 2.5 with Linux. In my time, I have never seen a computer that can actually **turn itself on**.

Anyone see the Simpson's episode where Smithers has a boot screen that has a video of Mr. Burns - presumably naked - saying:
> *Computer/Mr. Burns:* "Hello, Smithers. You're... quite... good... at... turning... me... on.
*Smithers to Lisa:* "You probably should ignore that...

Its sort of like that, but less funny and more interesting.

For months now, my computer will turn itself on at 1am, every day. If the computer is already turned on at 1am, nothing happens. The only way to fix this is to pull the power cord out every night before bed.

I've tried checking my cron jobs (I have zero, as my user or root), checked the logs (no errors or warning or sign of unlawful entry), had the Internet and no Internet plugged in (can't be a hacker), etc., and it still, without fail, will boot every day at 1am.

I even completely wiped Hardy to upgrade to Intrepid, so this can't be an OS thing.

The only thing I can think of is a broken power supply (with some sort of internal clock (?)) or a broken BIOS.

Has anyone ever experienced a computer that can bootstrap itself?

---

### Post by OutOfReach on 2008-11-04
I know that a lot BIOSes have an option to turn the computer on at a certain time. So you may want to check your BIOS settings.

---

### Post by damis648 on 2008-11-04
That is very wierd... maybe a network card bug and the "wake on lan" option?

---

### Post by Grant A. on 2008-11-04
[IMG]http://tbn0.google.com/images?q=tbn:u_pbJmQ638laLM:http://www.pcghostdoctor.extra-net.co.uk/ghost-in-computer.jpg[/IMG]


Why not just turn off the surge protector or unplug the computer at night? A simple fix, but effective.

---

### Post by I-75 on 2008-11-04
Those darned ghosts.... :-)

---

### Post by kernelhaxor on 2008-11-04
a lot of BIOSes have that option! that wud be the first place to look into

---

### Post by init1 on 2008-11-04
Yeah your BIOS probably has that feature. Go into the CMOS setup utility can see if you can disable it.

---

### Post by lisati on 2008-11-04
The BIOS on my desktop also has an option to auto-start after power failures.

---

### Post by RATM_Owns on 2008-11-04
Weird.
But I know some guys who you can call.
Look them up in the phone book.
They're called "Ghostbusters."

---

### Post by divinequran on 2008-11-04
I think the better option will be to discard your power cables, you can fix it by changing the settings in your BIOS, It may not discard or remove the cables all the times.

---

### Post by Allison on 2008-11-04
I actually had the exact same thing happen to me in college, excpet it wasn't at the same time each day.  Mine had to do with a "turn on computer on network activity" option.  If I were still running XP, I'd try to find it in my settings.  But alas, I am now running Vista.  I know, I know.  Evil.  But I actually haven't had many problems with it.

I tried looking on my mom's computer, which is running XP, but unfortunately I couldn't find it.  I thought it was in internet options though.  And it was definitley something along the lines of "power on with network activity."  So while I doubt that will help you much, it might make you feel better to know that someone else in the world has had the same problem. :)

---

### Post by Icehuck on 2008-11-04
It's your BIOS. You probably have it set to wake up at 1:00 am without you realizing it(or you have wake on lan set and something is pinging your machine). I have a few machines that I have set to turn on and off throughout the day.

---

### Post by MaxIBoy on 2008-11-05
The guy said earlier that he's tried unplugging his LAN cable, so that wouldn't be causing it.

Guaranteed, your BIOS settings are off. You might not have done that on purpose or even done it on accident; cosmic radiation (solar wind from the sun and other stars) can scramble the CMOS sometimes.

---

### Post by pp. on 2008-11-05
AS others have said, possibly some BIOS settings:

- Powering on at a certain time of day
- waking on some kind of input (LAN, Keyboard, Mouse etc)
- Starting when power returns (would imply some kind of power outage)

Also, the computer could pick up some weird signals from the power line. Any factories, bakeries, train depots or other large scale power consumers near the location?

---

### Post by altonbr on 2008-11-05
> **MaxIBoy said:**
> The guy said earlier that he's tried unplugging his LAN cable, so that wouldn't be causing it.

Guaranteed, your BIOS settings are off. You might not have done that on purpose or even done it on accident; cosmic radiation (solar wind from the sun and other stars) can scramble the CMOS sometimes.

Exactly, it's not the LAN.

I'll try looking at the BIOS on the next reboot.

Thanks for the suggestions everyone...

> **pp. said:**
> AS others have said, possibly some BIOS settings:

- Powering on at a certain time of day
- waking on some kind of input (LAN, Keyboard, Mouse etc)
- Starting when power returns (would imply some kind of power outage)

Also, the computer could pick up some weird signals from the power line. Any factories, bakeries, train depots or other large scale power consumers near the location?

 * [yes] powering on at a certain time of day
 * [no] waking on some kind of input (LAN, Keyboard, Mouse etc)
 * [no] Starting when power returns (would imply some kind of power outage)
 * [no] wake on LAN
 * [no] power signals from external -- I've even had the computer turn on at 1am at three different locations and currently have a UPS /w power conditioner
 * [maybe] Ghosts.
 * [possible] solar radiation

I'll check the BIOS and report back!

---

### Post by pp. on 2008-11-05
> **altonbr said:**
> 
 * [no] Starting when power returns (would imply some kind of power outage)

Are you sure? The power outage could be very short (on the order of 1/60 of a second) or very shallow (a modest percentage of the required voltage).

Edit: not so likely; I've missed the UPS/conditioner in the preceding post.

---

