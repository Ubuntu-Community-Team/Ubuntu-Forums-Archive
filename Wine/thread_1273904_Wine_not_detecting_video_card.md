---
title: "Wine not detecting video card?"
date: 2009-09-23
forum: Wine
---

### Post by the2ndgenesis on 2009-09-23
Hey everyone. Just coming off a fresh reinstall of 9.04 and have run into a few problems with my video card (NVIDIA GeForce 8600M) in Wine. Was hoping you guys could throw me a bone...

I was pleasantly surprised by how easily the drivers for the card installed at the outset of the installation, but for some reason, Wine (or specifically, Crossover Games) doesn't seem to recognize that my card is there at all. As such, nothing I want to run in Wine that uses it (e.g. Steam games) works. I've been trying to figure out what the problem is for a few hours but am basically stumped.

Could one of you help me find out what exactly is the issue? I feel like I'm forgetting something critically important here... I will post the content of any config files that you request. Anything to keep me from booting back into Vista to get my fix...

Please and thank you.

---

### Post by castlefox on 2009-09-24
Do any games play or do they refuse to play because no card is recognized.

Have you tried doing a fresh install of wine?

---

### Post by the2ndgenesis on 2009-09-24
> **castlefox said:**
> Do any games play or do they refuse to play because no card is recognized.

Have you tried doing a fresh install of wine?

When selecting which video card to use (the only example I've tried so far is Dawn of War), the only options I'm given are "Direct3d HAL" and "none." Choosing either one, the game refuses to load, unsurprisingly.

And the install of Wine is fairly new... I think I threw it on here yesterday or the day before that.

---

### Post by NightMKoder on 2009-09-24
Make sure you're using proprietary drivers (Hardware Drivers option somewhere in the system menu), and make sure you're using the latest wine (1.1.29).

---

### Post by the2ndgenesis on 2009-09-24
> **NightMKoder said:**
> Make sure you're using proprietary drivers (Hardware Drivers option somewhere in the system menu), and make sure you're using the latest wine (1.1.29).

Thanks for reminding me NightMKoder. I updated Wine and ran Crossover again... it didn't seem to help, though.

For the moment I've uninstalled Crossover and am wondering what would be the best way to proceed from here. Should I even bother re-installing it or should I just try to run Steam directly from Wine?

[EDIT]
I forgot to mention... ever since changing my source list to update Wine, I've started getting the following error while running Update Manager:
```
W: GPG error: http://wine.budgetdedicated.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
```
Does this ultimately matter, and if not, is there any way to get the message to go away?
[/EDIT]

---

### Post by beastrace91 on 2009-09-24
That error does not stop anything from working it simply means you do not have the gpg key for the repo.

~Jeff

---

