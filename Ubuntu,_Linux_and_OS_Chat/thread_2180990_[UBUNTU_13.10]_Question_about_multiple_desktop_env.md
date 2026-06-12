---
title: "[UBUNTU 13.10] Question about multiple desktop environments"
date: 2013-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by fatcowxlive on 2013-10-15
Hello!

Ever since Ubuntu made the jump to Unity, I like a few other Ubuntu users decided to leave in search of a new distro to try and fill this void. I've jumped to GNOME2 forks like Mint (MATE), to Fedora and its use of the GNOME Shell, to some XFCE distros and even the new ElementaryOS distro. Ever since GNOME made the jump to GNOME3 it seemed that the number of desktop environments have jumped.

Now I am back to Ubuntu, wanting to give 13.10 a spin on the 17th. My question to you guys is if it would cause any issues if you download multiple desktop environment over Unity like Gnome Shell, xfce and others? Also a while back (like 2009) I had a Fedora Live DVD that came with Gnome, KDE and various codecs is there something similar for Ubuntu builds? 

Thanks you!

---

### Post by deadflowr on 2013-10-15
I've never had any issues installing and running multiple desktops, but that really doesn't mean you won't.
I guess it really comes down to what you, yourself, consider issues.

Gnome-shell and classic seem to work just as well on Ubuntu as they do on any other distro I've used them on.

---

### Post by fatcowxlive on 2013-10-15
> **deadflowr said:**
> I've never had any issues installing and running multiple desktops, but that really doesn't mean you won't.
I guess it really comes down to what you, yourself, consider issues.

Gnome-shell and classic seem to work just as well on Ubuntu as they do on any other distro I've used them on.

Thanks! Can I install the Gnome-Flashback session without installing Gnome-Shell like the old Gnome fallback?

---

### Post by llanitedave on 2013-10-15
The only issue I've ever had is organizational, not technical.  Each DE has its own suite of utilities and system tools, but in the past, at least, they've all ended up sharing the same menus on each DE.  So on KDE, I got the menu items for Unity and Xfce as well as KDE itself.  It can get a bit crowded.

---

### Post by deadflowr on 2013-10-15
> **fatcowxlive said:**
> Thanks! Can I install the Gnome-Flashback session without installing Gnome-Shell like the old Gnome fallback?

Yes
Here's a look at the flashback package and the stuff(depends) it needs.
[http://packages.ubuntu.com/saucy/gnome-session-flashback](http://packages.ubuntu.com/saucy/gnome-session-flashback)

Though, I am a bigger user of shell than classic/flashback, so I really don't know, nor do I care if they junkered beloved functions.
I do know that it is a useable desktop, and has as of yet, not imploded the universe.(at least my universe)

---

### Post by fatcowxlive on 2013-10-15
> **llanitedave said:**
> The only issue I've ever had is organizational, not technical.  Each DE has its own suite of utilities and system tools, but in the past, at least, they've all ended up sharing the same menus on each DE.  So on KDE, I got the menu items for Unity and Xfce as well as KDE itself.  It can get a bit crowded.

Ah, thanks for the tip. Now I'm rethinking the whole thing :P. Makes sense, I guess Unity and Gnome-Shell combo is as less messy as you can get.

> **deadflowr said:**
> Yes
Here's a look at the flashback package and the stuff(depends) it needs.
[http://packages.ubuntu.com/saucy/gnome-session-flashback](http://packages.ubuntu.com/saucy/gnome-session-flashback)

Though, I am a bigger user of shell than classic/flashback, so I really don't know, nor do I care if they junkered beloved functions.
I do know that it is a useable desktop, and has as of yet, not imploded the universe.(at least my universe)

Thanks for the link! Good to know Ubuntu/Unity supports Flashback without the need to install Gnome-Shell!

---

### Post by sammiev on 2013-10-15
> **llanitedave said:**
> the only issue i've ever had is organizational, not technical.  Each de has its own suite of utilities and system tools, but in the past, at least, they've all ended up sharing the same menus on each de.  So on kde, i got the menu items for unity and xfce as well as kde itself.  It can get a bit crowded.

dido

---

### Post by ubuforum3 on 2013-12-13
Once installed, how do you switch between the Desktops?

---

### Post by deadflowr on 2013-12-13
> **ubuforum3 said:**
> Once installed, how do you switch between the Desktops?

In normal Ubuntu?
You switch 'em at the login screen.
In the box where you're login name is is a ubuntu logo, click on it and the choices of desktops will come up.

---

### Post by monkeybrain20122 on 2013-12-13
I know LXDE and gnome-fall back witll work, and with the latter there are only a few dependencies. But I think gnome-shell is not going to work, at least that was what I read for 13.04, something about Unity losing the wall paper and icons if gnome-shell was installed on the same system. I suppose kde would be crazy even if you can do it, usually just installing one kde application would bring in a ton of dependencies

---

### Post by buzzingrobot on 2013-12-13
> **fatcowxlive said:**
> ...a while back (like 2009) I had a Fedora Live DVD that came with Gnome, KDE and various codecs is there something similar for Ubuntu builds? 


Fedora is pretty adamant about avoiding non-free codecs, so that Live DVD may have come from another source.

In any case,  stuff takes up more room than it used to.  It's getting difficult to fit multiple DE's on a single Live DVD.  OpenSuse 13.1, for example, offers separate live images of KDE and Gnome.  It does offer a non-live DVD with multiple DE's which tallies out at over 4 gigs, just about filling one DVD.

I'm not aware of any single Ubunti image combining multiple DE's. More or less the equivalent is available in a network install which offers a software selection menu.

---

### Post by Daletec on 2013-12-13
I use Ubuntu-Studio as my main distro, I love it.  I also like the customized XFCE desktop, but I always like to add LXDE and KDE-plasma, just just run:

>sudo apt-get install xubuntu-desktop
>sudo apt-get install kubuntu-desktop
>sudo apt-get install lubuntu-desktop

I also add wy60 as my Unix server at work uses WYSE60 terminals.  I had to build a .deb package, so Alien is a must-have.

---

