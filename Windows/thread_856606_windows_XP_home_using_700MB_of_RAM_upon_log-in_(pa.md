---
title: "windows XP home using 700MB of RAM upon log-in (painful slow)"
date: 2008-07-11
forum: Windows
---

### Post by Tuxoid on 2008-07-11
I have no idea why, but my dad's installation of Windows XP Home is taking 700MB out 1GB of memory upon log-in of any account. Whether it's on my account alone (which has very few icons on the desktop, only four system tray items) or my dad's (with several desktop shortcuts, several system tray items), it's using far too much RAM, and effectively, is slower than a monster truck without front wheels.

I have been running virus scans, spyware scans, registry scans, process scanners, you name it; I have run it. To list it all off:

I ran AVG 8.0 (Free Edition) 3 times on slow scan mode.
Every time, I updated the database before performing a scan, and all three times, it found no threats after running a scan with an updated database

I ran CCleaner. CCleaner found a whopping 423 issues with the registry. I saved a backup point, before fixing all those problems, and after fixing all of those registry problems, it was still eating my RAM like candy and was still just as slow. CCleaner was mostly picking issues with program sortcuts and found quite a few ActiveX/COM issues (kinda makes my skin crawl :( )

Rolled-back the registry to previous saves created by CCleaner. That just increased the amount of items in the system tray, the amount of RAM being eaten, and the lack of speed remained after a restart.

Ran Spybot Search and Destroy. After ran an update, I did a scan, it didn't find anything

Ran advanced windows care personal (v2.01 ?). found lots of problems, that remained after an attempt at the 'Repair' option.

Ran HiJackThis. The only issue I have, I know little about system processes on Windows XP. This is something that I could use some help with. I will post the log file that HiJackThis generated:

but my question is, does the stuff under HiJackThis seem dangerous. If it doesn't, what else can I try to get the RAM consumption and speed back to normal?

---

### Post by fiddledd on 2008-07-11
I have to go after posting this so I can't help until tomorrow, however someone will be able to help. To help them (or me if I'm wrong about someone else helping :)) right click the Taskbar and select Task Manager. Then Click the Processes tab and see how much memory is being used by which process. You should easily see which is using all the memory, and nothing should be using more than 40mb of ram on login. Well, maybe vsmon, which is Zonealarm. Anyway, that should help anyone who might be able to help you. Sorry, but I must go.

---

### Post by LittleLORDevil on 2008-07-11
In your "run" menu type msconfig, go to start-up and uncheck unnecessary programs and that should free up a lot of junk like iTunes or other stuff that doesn't need to be running on start-up. Then reboot and see what it is like then.

---

### Post by Tuxoid on 2008-07-11
I am getting that RAM usage figure from Advanced Windows Care's Memory Cleaner. It doubles as a memory monitor.

Anyway, as I forgot to attach the log file in my first post, I will attach it now.

I would check the memory being used by each process, but the task manager somehow lost its tabs, menus, and title bar. I'd give a screen shot of that, but I don't think windows is operating fast enough to take a screen shot of anything.

---

### Post by paul101 on 2008-07-11
why not do a fresh install of xp??



strong solutions are often the best solutions



have you tried AVAST??

---

### Post by Tuxoid on 2008-07-11
I'd do a fresh install, but I have no means of a back-up for everything, and sine this is a Dual-Boot (XP and Hardy), I would need to recover GRUB after re-installing windows (something that I don't have a clue on how to do).

---

### Post by paul101 on 2008-07-11
> **Tuxoid said:**
> I'd do a fresh install, but I have no means of a back-up for everything, and sine this is a Dual-Boot (XP and Hardy), I would need to recover GRUB after re-installing windows (something that I don't have a clue on how to do).


i'd opt for the option of wiping EVERYTHING, fresh start... fresh install of ubuntu


you dont have any cd's??? :confused:

---

### Post by Nessa on 2008-07-11
You can try turning off Advanced Windows Care's Memory Cleaner and use your task manager to check the RAM. Maybe it's your memory monitor eating up the memory.

---

### Post by Tuxoid on 2008-07-12
> **paul101 said:**
> i'd opt for the option of wiping EVERYTHING, fresh start... fresh install of ubuntu


you dont have any cd's??? :confused:

I don't see a need to wipe both OSes off the disk; Ubuntu is working fine. I don't have any hardy CDs at the moment. I upgraded both my laptop and my dad's computer, from Gutsy, via the internet.

> **Nessa said:**
> You can try turning off Advanced Windows Care's Memory Cleaner and use your task manager to check the RAM. Maybe it's your memory monitor eating up the memory.

I would check the RAM consumption via the Windows Task Manager, if it hadn't of stopped showing its tabs, menus, and title bar. I have no idea how to recover that. I have found that Windows runs noticeably as slow with or without the Windows Care Memory monitor.

---

### Post by fiddledd on 2008-07-12
Let's get Task Manager right first. It's running in Tiny Footprint mode, here's the fix:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;193050](http://support.microsoft.com/default.aspx?scid=kb;en-us;193050)

---

### Post by Tuxoid on 2008-07-16
I found out the reason it's slow. It's because the hard drive has some bad sectors. I ran badblocks and it found a sizable amount of messed blocks. After running badblocks, I ran diagnostic disk that came with the computer, and that comfirmed it; noting that actual sectors are bad. I will be getting it replaced ASAP.

And actually, I was reading my memory monitor wrong. There was actually 700MB free.

---

