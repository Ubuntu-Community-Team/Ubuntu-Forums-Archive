---
title: "Ubuntu + XFCE vs Windows on an old laptop"
date: 2006-04-29
forum: The Cafe
---

### Post by auberginepop on 2006-04-29
I am a convert to Linux and Ubuntu. I use Slackware boxes at work and Ubuntu on two desktops at home. Great on all fronts.

I also have an old laptop at home (Dell Latitude CP M233ST with 128 RAM). This was untill recently running Windows XP. Although on old machine it did run XP and Office reasonably well.

I an attempt to go Windows free and also because some forums will have you believe that Linux is more efficient on old hardware, I did a basic Ubuntu install on the laptop and added XFCE.

What I have found is that the machine now takes longer to boot and is much slower driving Firefox (the main application for the machine). Openoffice is too slow to be practical.

As a result I am grudgingly starting to think that it would be best to give up the idea of Linux for this machine and reload XP.

Am I wrong? Perhaps another distro?

The one thing I have learned from the experience is the power of the Opera browser where speed over features is important.

---

### Post by kaamos on 2006-04-29
Well, openoffice is way too heavy for that amount of memory. Abiword would be what you are looking for. And if the OS in general feels too sluggish, you could try damn small linux.

---

### Post by tseliot on 2006-04-29
[QUOTE=auberginepop]I an attempt to go Windows free and also because some forums will have you believe that Linux is more efficient on old hardware, I did a basic Ubuntu install on the laptop and added XFCE.
...
Am I wrong? Perhaps another distro?

The one thing I have learned from the experience is the power of the Opera browser where speed over features is important.[/QUOTE]
Either try a more lightweight WM such as IceWM or Openbox or try Arch Linux with Xfce, which really makes my laptop fly (something which never did with Winxp or Xubuntu).
Arch Linux is optimised for i686 processors and is very fast.

---

### Post by auberginepop on 2006-04-29
The problem with considering lighter weight apps like Abi word is that like most people I need compatiblilty with Word and Excel because of their predominance. I also have to consider the merits of chosing such apps when, although I would love to leave XP behind, Office does run well on the machine and does what I need it to.

Before taking a step backwards though, I think I will try a lighter weight distro. Thanks for the advice on Arch. I'd not heard of that one. Perhaps I'll give it a go or perhaps Damn Small Linux.

---

### Post by auberginepop on 2006-04-29
During this experiment, as well as discovering Opera, I have also been very impressed with XFCE.

---

### Post by tseliot on 2006-04-29
[QUOTE=auberginepop]Before taking a step backwards though, I think I will try a lighter weight distro. Thanks for the advice on Arch. I'd not heard of that one. Perhaps I'll give it a go or perhaps Damn Small Linux.[/QUOTE]
I forgot to tell you that on my laptop (158MB of RAM, because the graphic card uses  part of the system memory) with Arch Openoffice is fast. And that's a miracle, I have never seen such a thing.

---

### Post by auberginepop on 2006-04-29
Have you had sucess using Arch with ndiswrapper and getting older sound cards to work?

---

### Post by tseliot on 2006-04-29
[QUOTE=auberginepop]Have you had sucess using Arch with ndiswrapper and getting older sound cards to work?[/QUOTE]
I don't use a wireless card so I have never used ndiswrapper.

About the sound card: you can use ALSA (which worked great both on my desktop and laptop).

Here are the instructions to set up ALSA (it seems a long process but I assure you that it's not):
[http://wiki.archlinux.org/index.php/Alsa]("http://wiki.archlinux.org/index.php/Alsa")

---

