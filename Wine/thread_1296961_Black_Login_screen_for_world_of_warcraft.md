---
title: "Black Login screen for world of warcraft"
date: 2009-10-21
forum: Wine
---

### Post by Arminius on 2009-10-21
I have followed all instructions at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and in previous occasions I have played wow fine under wine.
hardware is the same, but this time I have followed instructions and nothing I do will get rid of the black screen at login.

so guess wine is a little different, or something else.

anyone know how to fix this?

---

### Post by pedro_orange on 2009-10-22
> **Arminius said:**
> I have followed all instructions at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and in previous occasions I have played wow fine under wine.
hardware is the same, but this time I have followed instructions and nothing I do will get rid of the black screen at login.

so guess wine is a little different, or something else.

anyone know how to fix this?

1 - What version of Wine are you using? I would imagine this is different from the last time you played.

2 - Have you tried running in D3D or OpenGL mode? 

3 - What video card / drivers do you have?

---

### Post by Arminius on 2009-10-22
wine version is 1.1.31

no idea which mode I'm running in, or how to switch between D3D or OpenGL mode

video card is Nvidia Geforce 8600 GT

---

### Post by hikaricore on 2009-10-22
You may need to add:

> SET glxAPI "OpenGL"

To your Config.wtf file.
That card runs WoW quite well, what driver are you using?

---

### Post by beastrace91 on 2009-10-22
If the fix in the post above me does not work for you try reverting back to Wine version .28 or .29 - I know this has resolved many WoW issues of the late.

~Jeff

---

### Post by Arminius on 2009-10-22
> You may need to add:

Quote:
SET glxAPI "OpenGL"
To your Config.wtf file.
That card runs WoW quite well, what driver are you using?

I tried SET glxAPI "OpenGL" and that didn't help I'm afraid
I went to administration/hardware drivers
and it just reads Nvidia accelerated graphics driver version 180

---

### Post by beastrace91 on 2009-10-22
> **beastrace91 said:**
> try reverting back to Wine version .28 or .29 - I know this has resolved many WoW issues of the late.

Give that a go.

~Jeff

---

### Post by Arminius on 2009-10-22
hmmm, I completely removed wine, then compiled wine-0.9.28
but whenever I ran "winecfg" in terminal it said wine is not installed and offered to install the latest.

so are there complete instructions on rolling back somewhere?
I've already googled around.

---

### Post by 8Kuula on 2009-10-22
I think beastrace91 means wine versions 1.1.28 or 1.1.29.

---

### Post by Arminius on 2009-10-22
ok thanks, Wine 1.1.28 i386 is installed, and wow is installing now, but wasn't there a problem with the EULA on the wrath of the lich king install?
later versions of wow solved that I'm lead to belive.

---

### Post by 8Kuula on 2009-10-22
Grayed accept button? That was wine side bug, and yes it should be fixed, don't ask on what version (and up) thou :P, with 1.1.28 should be fine.

---

### Post by Arminius on 2009-10-22
yeah EULA was fine, I could have sworn I used a later wine version where it was greyed out.

does wine usually remove really necesarry stuff then put it back in later.

anyway it's downloading the game patches but seems to be working fine now.

so thanks everyone.

anyone who comes after don't use the latest wine if your only needing it to play wow.

---

### Post by hikaricore on 2009-10-23
> **Arminius said:**
> 
does wine usually remove really necesarry stuff then put it back in later.


This is what's known as a regression.
When managing a large base of code it is sometimes possible to mess up one thing by fixing another.

> **Arminius said:**
> 
anyone who comes after don't use the latest wine if your only needing it to play wow.

I've played WoW on every version of Wine for the last few years including the latest which is atm 1.1.31.
Aside from a few minor things I've not had a problem in a long time.
Hell I even installed Wow recently with a version back.

---

### Post by Sanity8080 on 2010-12-21
Im not currently in front of my laptop, but I am getting the same issue, the patches all downloaded for WoW, when I went to hit play, I got a black screen, and could hear the sound, and see the mouse pointer, but nothing else.

---

