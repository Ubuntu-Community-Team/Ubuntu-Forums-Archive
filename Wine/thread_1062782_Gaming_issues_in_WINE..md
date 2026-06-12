---
title: "Gaming issues in WINE."
date: 2009-02-07
forum: Wine
---

### Post by SketchyLlama on 2009-02-07
Hi,

I've been playing games on WINE for around 6 months now (WoW in particular). 

I've noticed a problem that is really annoying, and I've searched everywhere in an attempt to solve it, but to no avail. 

When I'm running a game, I cannot alt-tab out of it at all. Furthermore, when I have the cube effects enabled a copy of WINE takes up every single desktop. This is what annoys me the most, because I can't quickly switch screens to respond to a message, read an email, or check a site. 

I feel like I've tried everything to solve this, I'm by no means an expert with Linux but I've been using it for a while. Is there anything that you can recommend I try to fix it, so it takes up one desktop as intended, or at least allows me to alt-tab freely?

Thanks in advance, it's driving me batty. I've scoured google for hours.

WINE: 1.1.14
GPU: 8800GT


-Paul.

---

### Post by skorea2131 on 2009-02-07
Are you using a computer that is supposed to have windows on it or was originally installed with linux

---

### Post by SketchyLlama on 2009-02-07
> **skorea2131 said:**
> Are you using a computer that is supposed to have windows on it or was originally installed with linux

It's a computer I built myself around May last year. I originally had Windows installed on it, but switched to Linux around October or so. 

At the moment it's dual boot, but I very rarely need to switch back to Windows to do something.

---

### Post by Dizzle7677 on 2009-02-07
> **SketchyLlama said:**
>  
When I'm running a game, I cannot alt-tab out of it at all. Furthermore, when I have the cube effects enabled a copy of WINE takes up every single desktop.

  Best practice is to turn off Compiz when running games. Install Fusion-Icon for easy switching(Compiz<->Metacity) or set visual effects to none from the desktop. It applies to native Linux games and through Wine also.

---

### Post by hikaricore on 2009-02-07
For best results run the game in Windowed Mode at your native desktop resolution and check the box that says fullscreen.

I have no trouble running WoW like this even with desktop effects.

---

### Post by SketchyLlama on 2009-02-07
> **Dizzle7677 said:**
> Best practice is to turn off Compiz when running games. Install Fusion-Icon for easy switching(Compiz<->Metacity) or set visual effects to none from the desktop. It applies to native Linux games and through Wine also.

I tried this just now, unfortunately I still get the same problems when trying to alt-tab. 

> **hikaricore said:**
> For best results run the game in Windowed Mode at your native desktop resolution and check the box that says fullscreen.

I have no trouble running WoW like this even with desktop effects.

This is something google turned up, running max windowed did solve some graphical and keyboard/mouse capturing issues, but no matter which way I run it (fullscreen/max windowed), the problem still exists.

---

### Post by RedSingularity on 2009-02-07
I have never been able to alt tab it either.  Would be nice if i could.

---

### Post by Bios Element on 2009-02-07
Ok, I'm in a hurry but here's what you need to do. Set the Wine desktop the size of your screen. Go into compiz and bind a key combo to fullscreen windows. Then just tap that when you want to go full/windowed. It's not ideal but it'll get you between WoW and your desktop.

---

### Post by SketchyLlama on 2009-02-07
> **Bios Element said:**
> Ok, I'm in a hurry but here's what you need to do. Set the Wine desktop the size of your screen. Go into compiz and bind a key combo to fullscreen windows. Then just tap that when you want to go full/windowed. It's not ideal but it'll get you between WoW and your desktop.

This would have been a good temporary fix, but it seems compiz is ignoring those commands with WoW. It's affecting Firefox behind it when I try.

--

Edit: 

I've managed to fix it, was incredibly simple and makes me feel a bit stupid. Here's what was done;

* winecfg in terminal.
* graphics tab.
* allow the window manager to control and decorate the windows.

Works perfectly now for me, hope it solved your problem too Shadow121. :)

---

### Post by RedSingularity on 2009-02-08
Ahh that did it for me as well.  Thanks guys.  :)

---

