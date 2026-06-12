---
title: "Why is X so tempermental?"
date: 2006-11-30
forum: The Cafe
---

### Post by an.echte.trilingue on 2006-11-30
I have a question that maybe somebody more tech-saavy than me can answer.  If, in windows, you have a problem with your video set up, it automatically drops you down to 600x800 8 bit resolution until you fix it.  This allows people who don't know much about their computers to bugger things up and still be able to fix them.  This is really nice if you are putting a new graphics card in and have to download the driver, for example.

In GNU/Linux, if X gets buggered up, you are lucky to be able to switch to a virtual terminal, usually you just get the black screen of death, or sometimes X loads and you can use it for a few minutes before it hard-freezes your box.  For some graphics cards, you cannot even boot at all from the *default* install (without the user having done anything to bugger X up!) without the black screen of death.

What is so hard about this?  Why doesn't X have a safe-graphics mode?

---

### Post by The Grum on 2006-11-30
Have a read of:

[https://blueprints.launchpad.net/distros/ubuntu/+spec/bullet-proof-x]("https://blueprints.launchpad.net/distros/ubuntu/+spec/bullet-proof-x")

Hopefully this will appear in Feisty.

---

### Post by bastiegast on 2006-11-30
> **an.echte.trilingue said:**
> 
What is so hard about this?  Why doesn't X have a safe-graphics mode?

I wonder that too, is anyone able to answer this?

---

### Post by Brunellus on 2006-11-30
because Windows is next to impossible to administer without a GUI, and *nix GUIs are 'extra.'  

Since one can have a minimally functional system without an xserver, the "startx at ANY cost" mentality doesn't get much traction.

---

### Post by an.echte.trilingue on 2006-11-30
> **bastiegast said:**
> I wonder that too, is anyone able to answer this?

It appears to be in the works, according to the answer that the grum posted, but I have to wonder why they are going with vesa instead of VGA...  You still run into about a person a day here who can't get things working with vesa even on modern hardware, which means there are probably many many more who just give up and don't use linux.  

I also wonder why it is impossible to do any meaningful graphics configuration from the GUI?  You tell a new user to dpkg-reconfigure xserver-xorg and sometimes they just give up...

---

### Post by Brunellus on 2006-11-30
> **an.echte.trilingue said:**
> It appears to be in the works, according to the answer that the grum posted, but I have to wonder why they are going with vesa instead of VGA...  You still run into about a person a day here who can't get things working with vesa even on modern hardware, which means there are probably many many more who just give up and don't use linux.  

I also wonder why it is impossible to do any meaningful graphics configuration from the GUI?  You tell a new user to dpkg-reconfigure xserver-xorg and sometimes they just give up...
or you could point them to SuSE, whose SaX (graphical X configuration program) is excellent.

---

### Post by an.echte.trilingue on 2006-11-30
> **Brunellus said:**
> because Windows is next to impossible to administer without a GUI, and *nix GUIs are 'extra.'  

Since one can have a minimally functional system without an xserver, the "startx at ANY cost" mentality doesn't get much traction.

If that were true, then instead of driver problems causing a hard crash, it would drop you into a terminal, no?

---

### Post by Brunellus on 2006-11-30
> **an.echte.trilingue said:**
> If that were true, then instead of driver problems causing a hard crash, it would drop you into a terminal, no?
if you're having problems with a binary driver, well, you're out of luck.  

If it's simply a misconfigured xorg.conf, then it *does* drop you to a terminal.

---

### Post by an.echte.trilingue on 2006-11-30
> **Brunellus said:**
> if you're having problems with a binary driver, well, you're out of luck.  

If it's simply a misconfigured xorg.conf, then it *does* drop you to a terminal.

Just to clarify, I am not having problems with anything, I am just wondering why this is the way it is.  Seriously, you're a mod, how many people do you read every day who cannot boot the liveCD at all because of problems with X?  This is a serious issue, methinks.

Also, if SuSE's tool works, why hasn't it been adopted in other *nixes?

Just curious...

---

### Post by Brunellus on 2006-11-30
> **an.echte.trilingue said:**
> Just to clarify, I am not having problems with anything, I am just wondering why this is the way it is.  Seriously, you're a mod, how many people do you read every day who cannot boot the liveCD at all because of problems with X?  This is a serious issue, methinks.

Also, if SuSE's tool works, why hasn't it been adopted in other *nixes?

Just curious...
SaX and SaX2 were not originally licensed as Free Software, so the community left them alone, as I recall.

---

