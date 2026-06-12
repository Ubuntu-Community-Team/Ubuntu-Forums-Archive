---
title: "Xubuntu, is it as feature complete as Ubuntu?"
date: 2007-10-20
forum: The Cafe
---

### Post by ddavid123 on 2007-10-20
I am a 2 year user of Linspire/Freespire, and am looking for a new distro.  I can not install Ubuntu because lack of memory.  256 minus 32 from video card is what I have, and Ubuntu will not install even in video safe mode.

Is Xubuntu just a feature full as Ubuntu and Kubuntu, or do I have to install a few packages?  I am looking for an easy to use Linux, with little or no CLI system configuration.  

If someone can tell me if any experience differences there are between Xubuntu and Ubuntu, I will appreciate it!

Thanks!

---

### Post by TidusBlade on 2007-10-20
I would say, the features are almost the same, just that programs are replaced abit. The best way to find out is for you to try it ;)

---

### Post by Tux Aubrey on 2007-10-20
You don't get OpenOffice.org.  Abiword is default WP.  Xfce is WM.  No games.  They're the main differences for me.  I install fluxbox and use that to further lighten the load.

---

### Post by tbroderick on 2007-10-20
I'd say try Zenwalk or even Puppy. Or wait until fluxbuntu is released. I don't think Xubuntu is as great for low memory computers as other distros.

---

### Post by Polygon on 2007-10-20
it uses around 60-70 mb of ram for me on a cold boot...which isnt bad. it goes up to like 90 when i start using other programs.

---

### Post by SlayerMan on 2007-10-20
Did you also try installation with the alternate cd? Using the alternate cd, you can probably install Ubuntu with less than 256 MB of RAM.

---

### Post by andrewabc on 2007-10-20
xubuntu for me only uses 62mb ram when I start it. I open every program possible from the menus and it was only using 120mb of ram.

---

### Post by Old Pink on 2007-10-20
I'm on a 256MB Ubuntu 7.10 GNOME system, with 500MB of swap.

To install on a low memory system, either:[LIST]
[*]Download the "alternate" CD, which is for text based installation, and requires little from your system.

[B]or

[/B]
[*]Format an old memory stick to linux-swap, boot the Live CD, insert your memory stick and swapon. This gives you more virtual memory, providing a smoother Live CD experience.[/LIST]

---

### Post by RedSquirrel on 2007-10-20
Xubuntu uses the Xfce desktop environment while Ubuntu uses the GNOME desktop environment. If you have never used Xfce before, it is a bit different and it will take you a little time to get used to it. It is, however, a desktop environment, so it has an easy-to-use point & click interface. 

With your RAM, you should be able to use the Xubuntu LiveCD to see what Xubuntu is like without actually installing it. Bear in mind of course that it will feel slower than it would if you install it to the hard disk.

You could install Ubuntu (with GNOME) using the alternate install CD, as mentioned above. I think that it will feel sluggish on your system since you don't have a lot of RAM. Xubuntu would be much faster.

Faster still is a minimal installation with a light window manager such as Fluxbox, Openbox, or IceWM, but they might require more "hands-on" tinkering than you want at this point. Up to you.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Polygon on 2007-10-20
oh, and btw....that one browser...i can never remember the name...kasakake or something is now in the ubuntu repos, so you can have a lightweight gecko browser without using firefox...and without having to install and run a bunch of gnome stuff with epiphany

---

### Post by RAV TUX on 2007-10-20
> **ddavid123 said:**
> I am a 2 year user of Linspire/Freespire, and am looking for a new distro.  I can not install Ubuntu because lack of memory.  256 minus 32 from video card is what I have, and Ubuntu will not install even in video safe mode.

Is Xubuntu just a feature full as Ubuntu and Kubuntu, or do I have to install a few packages?  I am looking for an easy to use Linux, with little or no CLI system configuration.  

If someone can tell me if any experience differences there are between Xubuntu and Ubuntu, I will appreciate it!

Thanks!I highly suggest [Wolvix]("http://wolvix.org/").

(I find Xubuntu more feature rich then Ubuntu or Kubuntu but that could be because I have GNOME, KDE & e17 installed also.)

---

### Post by RAV TUX on 2007-10-20
> **Polygon said:**
> oh, and btw....that one browser...i can never remember the name...kasakake or something is now in the ubuntu repos, so you can have a lightweight gecko browser without using firefox...and without having to install and run a bunch of gnome stuff with epiphany
[Kazehakase]("http://kazehakase.sourceforge.jp/")


Thanks for the 411 Polygon, installing [Kazehakase]("http://kazehakase.sourceforge.jp/") now!

---

### Post by LanDan on 2007-10-20
Xubuntu is great in my opinion 

i add openoffice and the needed codecs and thats all i need

offcourse you can add anything else you like, but as a normal desktop i can certainly call it complete.

p.s.
the story that it works well on slow machines is questionable...no matter how light your window manager is, if you use firefox, thunderbird, synaptic etc.... it will always be slow

---

### Post by RedSquirrel on 2007-10-20
> **LanDan said:**
> the story that it works well on slow machines is questionable...no matter how light your window manager is, if you use firefox, thunderbird, synaptic etc.... it will always be slow

Not always. It depends on the hardware. If the system is really old and/or has very little RAM, then I agree, those heavyweight programs will drag. It's one of those things where you have to try it out and see how it goes.

If you use a minimal installation with a light window manager, it leaves more resources for the heavier programs. They *may* perform better under those circumstances. Programs that were almost unusable in GNOME may work reasonably well on a light installation.

---

### Post by DjBones on 2007-10-20
If your looking into light distro's and are thinking about using fluxbox,
checkout the derivative of Mepis "AntiX" .. its a program rich but incredibly light on memory usage distro ((and the best looking out of the box flux distro around in my opinion lol))

Zenwalk is great too, but it can get annoying compiling things from source if you don't like doing that.. because it is slackware based haha

---

### Post by RAV TUX on 2007-10-20
> **LanDan said:**
> Xubuntu is great in my opinion 

i add openoffice and the needed codecs and thats all i need

offcourse you can add anything else you like, but as a normal desktop i can certainly call it complete.

p.s.
the story that it works well on slow machines is questionable...no matter how light your window manager is, if you use firefox, thunderbird, synaptic etc.... it will always be slowFunny OO.o is the first program I remove from any distro, I prefer Koffice.

---

### Post by RAV TUX on 2007-10-20
> **DjBones said:**
> If your looking into light distro's and are thinking about using fluxbox,
checkout the derivative of Mepis "AntiX" .. its a program rich but incredibly light on memory usage distro ((and the best looking out of the box flux distro around in my opinion lol))

Zenwalk is great too, but it can get annoying compiling things from source if you don't like doing that.. because it is slackware based haha

Zenwalk is nice but a bit too bloated, I prefer Wolvix which is also based on Slackware but much easier to use overall.

---

