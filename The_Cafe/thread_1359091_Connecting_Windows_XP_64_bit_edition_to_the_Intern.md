---
title: "Connecting Windows XP 64 bit edition to the Internet fail"
date: 2009-12-19
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-19
I know this isn't a Windows support forum, but I've been posting here for almost a year and don't want to go out and find a Windows help forum to join since the support on this forum is usually pretty good.

Anyway, after the colossal pile of fail that Windows 7 64 bit edition turned out to be I've decided to revert back to Windows XP.

Windows XP 32 bit, Windows 7 64 bit, and Ubuntu 64 bit automatically detected my network configurations. But Windows XP 64 bit didn't. It was originally setup to automatically detect my network settings. When that didn't work I logged onto my upstairs Windows XP (32 bit) installation, ran ipconfig, wrote down all of my information, and entered it manually (changing the last segment of my IP address to something different, obviously). After doing that multiple times it still doesn't work, even entered several different ending segments to my IP address to make sure I wasn't using an address that was already in use by my something else in my house. I tried an alternate DNS (4.2.2.1) instead of the two Comcast DNS's. I also tried switching all of the network connection settings back to automatic and doing an ipconfig /release and ipconfig /renew, but to no avail.

When I run ipconfig I don't get any readouts except "Windows IP configuration" at all, it's as if it doesn't recognize my motherboard's built in networking card. I tried putting in my motherboard's driver CD but nothing happened when I clicked to install network connection drivers.

---

### Post by pwnst*r on 2009-12-19
64bit Win7 works fine here and is what i'm posting from.  so in essence, you failed.

---

### Post by bilalakhtar on 2009-12-19
Looks like your card is not supported in WinXP 64-bit. Well, WinXP 64-bit was only a testing release for WinVista 64bit. Therefore, it is expected to have such problems.

---

### Post by blueshiftoverwatch on 2009-12-19
> **pwnst*r said:**
> 64bit Win7 works fine here and is what i'm posting from.  so in essence, you failed.
64 bit Windows 7 works fine with my hardware configuration as well, automatically detected all of my settings. It's just really buggy for me as far as the software side of it. I'm constantly getting Explorer crashes and when trying to play some of my games that my friends are able to correctly play on Windows XP I'll instead get the BSOD. Which is why I'm downgrading to XP.

I wonder if it would be worth it to try and install Vista instead of XP? Did Vista get a lot of pad press because it was a bad OS or because there wasn't much of a reason to upgrade to it?
> **bilalakhtar said:**
> Looks like your card is not supported in WinXP 64-bit. Well, WinXP 64-bit was only a testing release for WinVista 64bit. Therefore, it is expected to have such problems.
The thing is, I was messing around with virtual machines about a month ago and could have sworn that I was able to connect to the Internet via 64 bit Windows XP running in Virtualbox on Ubuntu. At least I think, it might have been 32 bit.

---

### Post by Queue29 on 2009-12-19
> **blueshiftoverwatch said:**
> 64 bit Windows 7 works fine with my hardware configuration as well, automatically detected all of my settings. It's just really buggy for me as far as the software side of it. I'm constantly getting Explorer crashes and when trying to play some of my games that my friends are able to correctly play on Windows XP I'll instead get the BSOD. Which is why I'm downgrading to XP.
.



Drivers exist for your network card for Windows 7/ Vista. Drivers do not exist (or you just haven't downloaded and installed them) for XP 64bit.

If the games you and your friends are playing were designed to run on a decade old OS, maybe it's time to find some new games.

---

### Post by CharlesA on 2009-12-19
> **pwnst*r said:**
> 64bit Win7 works fine here and is what i'm posting from.  so in essence, you failed.

Running Win7 x64 Ultimate just fine here.

> **blueshiftoverwatch said:**
> 64 bit Windows 7 works fine with my hardware configuration as well, automatically detected all of my settings. It's just really buggy for me as far as the software side of it. I'm constantly getting Explorer crashes and when trying to play some of my games that my friends are able to correctly play on Windows XP I'll instead get the BSOD. Which is why I'm downgrading to XP.

What network card/mobo do you have? Also: What games are you playing that are causing a BSOD? What's the error message on said BSOD?

> The thing is, I was messing around with virtual machines about a month ago and could have sworn that I was able to connect to the Internet via 64 bit Windows XP running in Virtualbox on Ubuntu. At least I think, it might have been 32 bit.

Virtual machine works differently, it simulates a network card to the guest OS, which is not necessarily the same as the host's.

> **Queue29 said:**
> If the games you and your friends are playing were designed to run on a decade old OS, maybe it's time to find some new games.

I still play a few games from ages ago. Tomb Raider, Fallout 1 and 2.. both run fine on W7 natively. *shrugs* Unless the game is insanely ancient, you can run it in compatibility mode if you need to.

---

