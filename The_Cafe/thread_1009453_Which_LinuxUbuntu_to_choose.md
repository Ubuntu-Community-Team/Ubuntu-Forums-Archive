---
title: "Which Linux/Ubuntu to choose?"
date: 2008-12-12
forum: The Cafe
---

### Post by Deathray on 2008-12-12
Hi everyone! I'm visiting my parents for the weekend and I feel sorry for my littlesister using a compaq nx9005 with Windows XP installed. It is so incredibly slow that she rarely even bothers to use the laptop.
Now is there a Linux OS that would run on the specified specifications relatively quickly?

AMD Athlon XP2600+ 2.12 GHz
192 MB DDR1 RAM
Radeon IGP 320M

All she needs to use the laptop for is webbrowsing, and a client that can log onto MSN Messenger.
I've been thinking about Xubuntu? Any suggestions that are not to hard to get installed?

---

### Post by dannytatom on 2008-12-12
> **Deathray said:**
> Hi everyone! I'm visiting my parents for the weekend and I feel sorry for my littlesister using a compaq nx9005 with Windows XP installed. It is so incredibly slow that she rarely even bothers to use the laptop.
Now is there a Linux OS that would run on the specified specifications relatively quickly?

AMD Athlon XP2600+ 2.12 GHz
192 MB DDR1 RAM
Radeon IGP 320M

All she needs to use the laptop for is webbrowsing, and a client that can log onto MSN Messenger.
I've been thinking about Xubuntu? Any suggestions that are not to hard to get installed?

Xubuntu is pretty light, and runs good on my laptop (1.6GHz & 512MB RAM).  Also easy to install.

I'm confused as to how she has a 2.21GHz processor and only 192MB Ram, though. ;x

---

### Post by PriceChild on 2008-12-12
I'd go with plain old Ubuntu if you're going to install something...

However why? That laptop is more than capable of running xp. I don't think you're going to make her comfortable using Ubuntu in just a weekend and it would probably be better for her to just reinstall a fresh copy of her xp and install antivirus/firewall.

---

### Post by Therion on 2008-12-12
> **dannytatom said:**
> I'm confused as to how she has a 2.21GHz processor and only 192MB Ram, though.
Because the integrated graphics are "borrowing" 64 of the 256MB of installed system RAM.

---

### Post by dannytatom on 2008-12-12
> **Therion said:**
> Because the integrated graphics are "borrowing" 64 of the 256MB of installed system RAM.

Ah, gotcha.  Didn't think about that. :P

---

### Post by Deathray on 2008-12-12
> **PriceChild said:**
> I'd go with plain old Ubuntu if you're going to install something...

However why? That laptop is more than capable of running xp. I don't think you're going to make her comfortable using Ubuntu in just a weekend and it would probably be better for her to just reinstall a fresh copy of her xp and install antivirus/firewall.

The Windows XP installed is completely stripped and she is always logged in as guest so she can't do harm. I use the tool HijackThis and the day I installe I added everything to ignore list. Anything new gets deleted. But it still manages to be extreamly slow. Oh I'm sure she will be comfortable right away as she will only be browsing the web so everything else won't matter.

---

### Post by sirjoebob on 2008-12-12
> **Deathray said:**
> 
AMD Athlon XP2600+ 2.12 GHz
192 MB DDR1 RAM
Radeon IGP 320M


Based on the specs, I would recommend Xubuntu. It is a lot faster than regular Ubuntu and will perform much better on that hardware.

---

### Post by zmjjmz on 2008-12-12
If she's just doing web browsing, I would recommend you get Sidux Xfce. I've found it to be relatively easy to use (not so easy to set up) and very light.
Just make sure you install flash and mplayer and everything, k?

---

### Post by lykwydchykyn on 2008-12-12
> **Therion said:**
> Because the integrated graphics are "borrowing" 64 of the 256MB of installed system RAM.

I wonder if that could be turned down in the BIOS.  Surely she's doing nothing on a laptop of those specs which requires that much video RAM.  IME XP on a machine with < 256MB is horrendously slow, unless you strip it bare (e.g., no AV running).  Add to that the fact that it's probably swapping all the time to a slow little laptop HDD.

Anyway, other than checking the BIOS to see if the video RAM sharing can be lowered, here's my advice:

 - If you install Linux, set it up dual-boot; let her try it gradually
 - Make sure you know her computing needs thoroughly.  I don't think ANYONE uses ONLY web-browsing and IM.  Surely she's got some other uses for it.
 - Xubuntu probably won't be a significant speed boost over XP, at least not in my experience.  Fluxbuntu, AntiX, or (if you're adventurous) build a lightweight setup from the ground-up using Debian. I recommend these because they are all Debian-based like ubuntu, and you'll have an easier time working with them if you know Ubuntu.

---

### Post by sirjoebob on 2008-12-12
> **zmjjmz said:**
> 1 I would recommend you get Sidux Xfce. I've found it to be relatively easy to use (not so easy to set up)

Why would you recommend something admittedly hard to set up? 

> **Deathray said:**
> Any suggestions that are not to hard to get installed?

:lolflag:

---

### Post by zmjjmz on 2008-12-12
> **sirjoebob said:**
> Why would you recommend something admittedly hard to set up? 


Well apparently I missed that part :p
I would still recommend it though. It's not _that_ hard to set up. If she's going to use it more overtime though you might want to put her in the sudoers file, which isn't that easy (It's easy if you do it a lot, but you might want to ask someone for help).

---

### Post by sirjoebob on 2008-12-12
> **zmjjmz said:**
> If she's going to use it more overtime though you might want to put her in the sudoers file,

This is not a good idea for a beginner. It is a security risk and a forum admin will probably comment on this because of that recommendation. I recommend NOT adding a new Linux user to the sudoers file because they could inadvertently do something that would hose the system.

Note: I run with my user in the sudoers file and appreciate the usefullness but it is not recommended for those unaware of the potential security risks.

---

### Post by zmjjmz on 2008-12-12
> **sirjoebob said:**
> This is not a good idea for a beginner. It is a security risk and a forum admin will probably comment on this because of that recommendation. I recommend NOT adding a new Linux user to the sudoers file because they could inadvertently do something that would hose the system.

Note: I run with my user in the sudoers file and appreciate the usefullness but it is not recommended for those unaware of the potential security risks.

You do realize that when you get a default Ubuntu install that you are in the sudoers file, right?

---

### Post by sirjoebob on 2008-12-12
You are talking about /etc/sudoers, right?

---

### Post by zmjjmz on 2008-12-12
> **sirjoebob said:**
> You are talking about /etc/sudoers, right?

Yes I am.
The way it works in Ubuntu is that you are put in the admin group upon install. In /etc/sudoers, you see
```
%admin ALL=(ALL) ALL

```
This is to make it easier to add other admin users so you don't have to constantly edit the sudoers file, but for a single user machine just having your username in the sudoers files should be fine.

---

