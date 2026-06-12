---
title: "Mouse freezes for no reason on Lenovo z570"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by samuraiCat on 2012-04-22
Hi everyone! I have a head-scratcher for ya!

I'm running a fresh install of Ubuntu Studio 12.04 Beta 2 on a brand new Lenovo z570. About once per day, when using my touchpad, my mouse randomly freezes. Only rebooting brings it back.

I can plug in a USB mouse to use the mouse. I can also use hotkeys. 

Running updates and upgrades on everything hasn't had any effect.

Does anyone have a suggestion on troubleshooting? I haven't found anything online that has fixed it.

Thanks!

By the way, other than this problem, UbuntuStudio has been fantastic.

---

### Post by ubuntu27 on 2012-04-22
Hi SamuraiCat, we all are experiencing the same thing. See [this forum thread]("http://ubuntuforums.org/showthread.php?t=1960391")


And here is the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/983910"). You can add yourself to "this bug affects me too"

---

### Post by jim_24601 on 2012-04-23
That thread and bug seem to be talking about failure of touch scrolling rather than the pointer not moving at all, although it might be another symptom of the same underlying problem.

I had a pointer freeze with the touchpad on my W520 yesterday, on a fully up-to-date Precise beta install. Sending it to sleep briefly by shutting the lid and opening it again sorted it out, though.

---

### Post by ubuntu27 on 2012-04-23
Oh. Sorry, I mis-interpreted it.

I personally did not experienced it, but I have seen it happen in my friend's laptop.

His laptop is of brand Sony, and it is around 2 years old. His mouse pointer freezes or is unable to control with the touchpad, but it can be controlled with an mouse.

It is quite en embarrassing bug, thankfully he likes to use the mouse, so he doesn't use the touchpad that often. Or perhaps it is a hardware problem?

He has Ubuntu 11.10 installed.




I hope someone could weigh in and perhaps shed some light on the subject.

---

### Post by mc4man on 2012-04-23
One of the major causes (but not only) of a frozen cursor was introduced in 11.10 (fix commited) & fix released in 12.04

The cause of the freeze was due to a 2nd instance of syndaemon running, this was caused in 2 separate ways.

One by lightdm but that was mainly confined to a live session & the 1st. session after an install

The more prevalent was from gnome-settings-daemon starting a 2nd instance
If during a freeze running this frees up the cursor that's a decent sign 2 were running
```
synclient TouchpadOff=0
```

More conclusive would be to run this first during a freeze, 
```
ps aux |grep syndaemon |grep -v grep
```

The 11.10 > 12.04 bug 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/868400)

This shouldn't be an issue anymore in 12.04, but still could be  in 11.10

---

### Post by neu5eeCh on 2012-04-23
Logitech's MX Anywhere mice have been weirdly failing (in a bad, fried hardware way) when used with 12.04. I could be coincidence, but more than one user has noticed their mouse going bad while using 12.04. Logitech just replaced my mouse and, brand new, it already failed, recently, to be recognized at boot up. Had to unplug it and plug it back in. This is how my last one failed. I'm getting... just a little... paranoid.

---

### Post by jim_24601 on 2012-04-25
Still having mouse problems on my Thinkpad. This morning it has been acting exactly as if I had one finger permanently down on the pad--a single touch acts as a scroll, but the pointer doesn't move.

There's only one instance of syndaemon running, so it doesn't look like that problem. Which should have been fixed by now anyway: I tried another update last night but all it pulled down was a Mono upgrade.

This is quite annoying. I've been running 12.04 since early alpha and it's been rock solid, now a few days before the release this comes down. Feh.

---

### Post by mc4man on 2012-04-25
> **jim_24601 said:**
> Still having mouse problems on my Thinkpad. This morning it has been acting exactly as if I had one finger permanently down on the pad--a single touch acts as a scroll, but the pointer doesn't move.

There's only one instance of syndaemon running, so it doesn't look like that problem. Which should have been fixed by now anyway: I tried another update last night but all it pulled down was a Mono upgrade.

This is quite annoying. I've been running 12.04 since early alpha and it's been rock solid, now a few days before the release this comes down. Feh.

If this is a recent break & you had proposed enabled there was a recent upgrade of xorg-server-core to 2:1.11.4-0ubuntu10.1, maybe involved, maybe not

(xserver-xorg-input-synaptics just went to 1.5.99.902-0ubuntu5.1 in proposed to fix the scroll issue but that's not your apparent problem

If you can't pinpoint when & what broke then maybe try a new install & certainly search for a  current bug & file  if one isn't already

---

### Post by jim_24601 on 2012-04-26
Thanks mc4man. A reboot seems to have fixed it for now; it's possible that there was a fix in the pipeline that needed a reboot to "take". There are a few touchpad bugs in the tracker but none that look like this exact problem. If it happens again I will investigate further.

---

### Post by ray field on 2012-04-26
I get this occasionally with Lenovo S100.

---

