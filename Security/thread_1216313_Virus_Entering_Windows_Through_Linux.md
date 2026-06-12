---
title: "Virus Entering Windows Through Linux"
date: 2009-07-18
forum: Security
---

### Post by loweehahn on 2009-07-18
I'm using Ubuntu via dual boot and since I can access Windows files through Ubuntu so I'm wondering whether there is a chance that a Windows virus entered through Ubuntu can enter Windows too and infect it. Thanks.

---

### Post by hetx on 2009-07-18
From what you explained you'd pretty much have to download a virus in Ubuntu and manually place it on the Windows partition =)

---

### Post by loweehahn on 2009-07-18
Haha... It's not like this. What I mean is can virus 'move' into Windows partition by itself?

---

### Post by lisati on 2009-07-18
> **loweehahn said:**
> Haha... It's not like this. What I mean is can virus 'move' into Windows partition by itself?

Unlikely without help

---

### Post by loweehahn on 2009-07-18
What do you mean by unlikely without help?

---

### Post by Bucky Ball on 2009-07-18
Well, if you download a file with a virus designed for MS, Ubuntu will ignore it, no effect, different language. If you are attached to a network or then drop that file onto a shared drive and open a Windows machine and access that file, game on.

Effectively, Linux will ignore because written in a different language, immune kind of, but can act as a 'carrier' of the virus.

Hope that helps.

---

### Post by XCan on 2009-07-18
In addition, if you by means manage to run the Windows virus, for example, through Wine, it is still unlikely that it would cause any harm to your Windows partition as the paths are all different.

---

### Post by bodhi.zazen on 2009-07-18
See [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

There is a section on viruses.

---

### Post by The Cog on 2009-07-18
> **XCan said:**
> In addition, if you by means manage to run the Windows virus, for example, through Wine, it is still unlikely that it would cause any harm to your Windows partition as the paths are all different.

By default, wine maps / to Z:, so if an NTFS drive was mounted, a virus running in wine could infect files on it. But it is quite unlikely - I don't think any windows viruses are able to run properly in wine. You might have more luck running old DOS viruses in DOS box - they were less sophisticated and thereby more likely to be compatible with emulated environments.

---

### Post by doas777 on 2009-07-18
in the absolute worse case, a malware laden file could conceivably become written to a windows hdd, but unless you launch it, it wouldn't really do anything, unless the malware was specifically written to attack a dual boot system. extremely unlikely.

---

### Post by XCan on 2009-07-19
> **The Cog said:**
> By default, wine maps / to Z:, so if an NTFS drive was mounted, a virus running in wine could infect files on it. But it is quite unlikely - I don't think any windows viruses are able to run properly in wine. You might have more luck running old DOS viruses in DOS box - they were less sophisticated and thereby more likely to be compatible with emulated environments.

You're right, however, the normal virii would look for the windows partition which maps into the user's home dir by default. Of course, there are virii out there that just want to wipe all partitions... :p

---

### Post by Richbuntu on 2010-05-24
What happens if my Linux computer is connected to a network where some people has Windows or if I use my USB stick to transfer files from my Linux to windows, in that case can the virus infect other computers?

---

### Post by lykwydchykyn on 2010-05-24
> **Richbuntu said:**
> What happens if my Linux computer is connected to a network where some people has Windows or if I use my USB stick to transfer files from my Linux to windows, in that case can the virus infect other computers?

Viruses aren't magic.  They're just programs, like any other programs.  For a program to do anything, it has to be executed.  For it to execute, it must first be put on a system that can run it, and then some action must be taken for it to be put into memory and executed (i.e., referenced in an autoexec file or registry location, selected by the user, launched from a cron/scheduled tasks job, etc).

Your average virus is just not written to operate in a cross-platform way like this.  Is it theoretically possible?  I suppose so, but it would be so unlikely to find itself in such a situation that it hardly seems worth the trouble.

So the short answer is "no"; a typical windows virus sitting on the hard drive of an Ubuntu or any other non-Windows system is not a threat to anyone.  If it can't execute, it can't do anything.

---

### Post by Richbuntu on 2010-05-24
Thanks, I just wanted to make sure that I won't have any problems :)

---

### Post by aysiu on 2010-05-24
> **Richbuntu said:**
> What happens if my Linux computer is connected to a network where some people has Windows or if I use my USB stick to transfer files from my Linux to windows, in that case can the virus infect other computers?
Windows tends to autorun any autorun files on a USB stick, unless you turn autorun off (which most users *don't* do), so theoretically if you have an autorun file on a USB stick, it'll do nothing in Linux, but it'll execute in Windows right when you plug in the drive.

---

