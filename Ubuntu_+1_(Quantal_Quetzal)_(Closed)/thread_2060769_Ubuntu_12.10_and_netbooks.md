---
title: "Ubuntu 12.10 and netbooks"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by toomanymatts on 2012-09-20
hi all

So was reading about 12.10 yesterday.  I run Ubuntu on three machines, my laptop, a desktop, and my gf's netbook.  Little Atom powered Dell thing, not sure what model off hand...can tell you later if it matters.

Anyhow, on the Atom thing, 11.10 ran OK, 12.04 was really sluggish, so we switched it to 2D mode and it was basically happy.  12.10 ditches 2D and replaces it with some kind of system that uses CPU to drive graphics or somesuch (I'm no techy, but that was my read anyhow).  

This lil Atom thing doesnt really have a lot of processing power to spare, so was wondering whether you guys thought that upgrading would be a bad idea for that machine.

Any other workarounds I can consider to ease the burden of Unity.  I am not a Unity hater btw (actually I really like it), but for this machine, if there are no better choices, I am pondering either leaving her at 12.04 or switching her to Lubuntu instead.

Matt

---

### Post by carl4926 on 2012-09-21
My ASUS 1015PEM run 12.04 just fine, that's with Unity.
Currently also it has Mint 13 KDE, which is good

I booted 12.10 on it recently (as I am running 12.10 dev on another machine) and it seemed fine. I will be installing 12.10 on it.
I could do that sooner rather than later if you like

---

### Post by rafalcieslak on 2012-09-23
This is true. I have installed 12.10 on Asus 1225c (In some countries it ships with Ubuntu pre-installed), but due to the fact that Unity2D is no longer available, and that CPU computes graphics for all effects, Unity works too slow for normal desktop usage - and compiz uses lots of CPU, which affects battery usage a lot.

I am a great fan of Unity and would prefer to disable some pretty effects then to be forced to switch to Lubuntu - any tips on how can I get it to run a bit faster?

---

### Post by oldfred on 2012-09-23
Moved to  [Ubuntu +1 (Quantal Quetzal)]("http://ubuntuforums.org/forumdisplay.php?f=416")

---

### Post by jerrylamos on 2012-09-23
Acer Aspire 1 netbook.  12.10 Ubuntu running O.K. I install, check Unity for bugs, then do 
sudo apt-get install lxde
From 42 years in engineering development on large main frame computers I prefer efficiency and performance.  Ubuntu (meaning unity and compiz) has other goals.

Your choice.

BTW using a spare TV at 1366x768 resolution takes some antics after every 12.10 install then works fine.  

Current Ubuntu 12.10 bug is disconnecting from hidden wireless network, launchpad bug reported, no fix, so I use a workaround.  12.04's network manager works fine with Precise.  I don't know if that nm would work with 12.10.

---

### Post by toomanymatts on 2012-09-24
Sticking LXDE on to Ubuntu basically = Lubuntu, right?

---

### Post by Stinger on 2012-09-24
I have a Lenovo IdeaPad s10 myself
[LIST]
[*]Intel Atom N270 single-core (1.6 GHz, 533 MHz FSB, 512 KB cache)
[*]Graphics: Intel Graphics Media Accelerator 950
[*]RAM: 1024 MB PC2-5300 DDR2 SDRAM 667MHz
[*]Hard drive: 160 GB 5400 RPM
[/LIST]
It works very well with [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") (based on Ubuntu 12.04)
Unity has always been painfully slow (Unity 2D is somewhat better)
There is currently a Gnome version of 12.10 under development, but still in the early alpha stages, [Ubuntu GNOME Remix 12.10]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/") It could be a possibility when released :D

---

### Post by philinux on 2012-09-24
I have an Acer 1410.

It gets a lockup when a large update is running but that's all.

Otherwise it runs 12.10 just fine.

---

### Post by jerrylamos on 2012-09-24
> **toomanymatts said:**
> Sticking LXDE on to Ubuntu basically = Lubuntu, right?

On one notebook I've got Lubuntu of course I replace Chromium with Firefox and Abiword with Libre Office and add Files (Nautilus) and gedit and there's a bunch missing from system settings and .... easier to just install Ubuntu then sudo apt-get install lxde.  Besides, Ubuntu isn't interested in Lubuntu so I expect it to disappear.  It's not LTS??

On rare occasions I fire up unity to check for some bug or to see what people arae talking about, then I lose interest in unity and go back to lxde for whatever it is I'm doing.

I've tried some gnome classic or gnome remix or whatever.  Not my cup of tea.  As an aside, there have been some "discussions" between Linus and the gnome people.

---

### Post by Stinger on 2012-09-24
> **philinux said:**
> I have an Acer 1410.

I don't think you can compare the [Acer 1410]("http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtml")to an Atom powered netbook like the one from toomanymatts girlfriend, the Acer 1410 has a lot more juice.

---

### Post by philinux on 2012-09-24
> **Stinger said:**
> I don't think you can compare the [Acer 1410]("http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtml")to an Atom powered netbook like the one from toomanymatts girlfriend, the Acer 1410 has a lot more juice.

I guess that depends on which Atom it is. The OP did not say.

Mine has an Intel® Celeron(R) CPU 743 @ 1.30GHz which does run out of steam as it just did doing an update.

I could not type this reply for a about a 20 second period.

---

### Post by Stinger on 2012-09-24
@philinux
guess you are right, but if you compare the Atom N270 to your Intel® Celeron(R) CPU 743, as done [here]("http://gadgetmix.com/netbook/intel-to-launch-su2300-celeron-743-processors-in-september/"), you get, and I quote:
> Intel is very sure that the 743 is 1.7 to 2.1 times faster than an Atom N270 in audio transcoding and image processing.

toomanymatts, can you post the specs from the Atom powered netbook in question please ?

---

