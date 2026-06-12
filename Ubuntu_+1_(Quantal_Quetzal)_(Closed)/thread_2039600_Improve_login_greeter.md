---
title: "Improve login greeter"
date: 2012-08-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by t1497f35 on 2012-08-09
Hi,
Currently the greeter first loads the system's default wallpaper then like "oh, this user has a wallpaper" and removes the system's default one with user's one. That wastes like 1-2 seconds on loading and showing up the system's default (needless in this case) wallpaper.

Wouldn't it be smarter to load user's wallpaper first (and hence also avoid the transition from one wallpaper to another), and, if needed, load the system's default one when needed?

---

### Post by dino99 on 2012-08-09
i've noted this non sense also; but i've not tried to find a dconf solution or using gnome-tweak nor reported it :(

but if you report it, i'll check the "affect me too" magic button :P

---

### Post by philinux on 2012-08-09
> **t1497f35 said:**
> Hi,
Currently the greeter first loads the system's default wallpaper then like "oh, this user has a wallpaper" and removes the system's default one with user's one. That wastes like 1-2 seconds on loading and showing up the system's default (needless in this case) wallpaper.

Wouldn't it be smarter to load user's wallpaper first (and hence also avoid the transition from one wallpaper to another), and, if needed, load the system's default one when needed?

The transition for me is almost instant. Also what about a multi user system?

---

### Post by vasa1 on 2012-08-09
> **philinux said:**
> The transition for me is almost instant. Also what about a multi user system?
The two loadings happens in 12.04 as well.
The transition time maybe be dependent on the computer's specs?

---

### Post by EgoGratis on 2012-08-09
> Also what about a multi user system?

There always is default user selected when system boots and just grab wallpaper from that user.

---

### Post by t1497f35 on 2012-08-09
> **philinux said:**
> The transition for me is almost instant. Also what about a multi user system?
It's not really about being instant or not, it's mostly about being silly (and annoying).
Imagine each time your **desktop wallpaper** first shows up the system's wallpaper than switches back to yours. Wouldn't you call that silly? If so, why should we put up with this in the login greeter?

The fact that this silly behavior consumes more CPU/hdd cycles & time is a lesser issue.

---

### Post by philinux on 2012-08-09
> **t1497f35 said:**
> It's not really about being instant or not, it's mostly about being silly (and annoying).
Imagine each time your **desktop wallpaper** first shows up the system's wallpaper than switches back to yours. Wouldn't you call that silly? If so, why should we put up with this in the login greeter?

The fact that this silly behavior consumes more CPU/hdd cycles & time is a lesser issue.

If you feel strongly about this I suggest raising a bug report.

Here I get default wallpaper then my custom wallpaper. Blink and I miss the transition.

(acer 1410 Intel® Celeron(R) CPU 743 @ 1.30GHz)

---

### Post by t1497f35 on 2012-08-09
> **philinux said:**
> If you feel strongly about this I suggest raising a bug report.
Not strongly, just slightly annoying. Also, on average, non-critical bugs from unknown users typically get taken care of in a few months (if at all), so I'm looking into the source code, send a patch and hopefully get them to apply it. But, often getting a patch from a newcomer to get applied usually takes more effort than creating it, i.e. last month I sent  a few lines of code to the transmission bittorrent and it's still dead in the water.

---

### Post by cecilpierce on 2012-08-09
What if you  don't blink ?      :P

---

### Post by vasa1 on 2012-08-09
> **cecilpierce said:**
> What if you  don't blink ?      :P

Dry eye!

---

### Post by wyliecoyoteuk on 2012-08-09
> **EgoGratis said:**
> There always is default user selected when system boots and just grab wallpaper from that user.

What about multi-seat?
I have had to set autologin on both seats to stop lightdm randomly failing to show the second login on my 2 seat system.

---

### Post by EgoGratis on 2012-08-09
I tested this again and now that this is mentioned i agree this should work better. Default users wallpaper should probably be garbed from the beginning.

P.S. And System Compositor in the future might do this a bit better? 


> What about multi-seat?
I have had to set autologin on both seats to stop lightdm randomly failing to show the second login on my 2 seat system.

Report bug?

---

### Post by t1497f35 on 2012-08-09
> **EgoGratis said:**
> I tested this again and now that this is mentioned i agree this should work better. Default users wallpaper should probably be garbed from the beginning.

P.S. And System Compositor in the future might do this a bit better? 

Report bug?
A quick note to the testers, when you log out to see how fast is the transition - it works (slightly)** faster **in this case because the system's and user's wallpapers have already been loaded during first login right after booting the OS.

Accordingly, the transition is (slightly) **slower** during the first login.

---

### Post by EgoGratis on 2012-08-09
Yes i always see the transition for one second or two and i did noticed this from the beginning i started using Ubuntu 12.04 when feature to display user wallpaper was introduced and basically always thought why not just grab default user wallpaper if it exist and if not then load default login image.

---

