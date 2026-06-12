---
title: "Fastest and Minimalist OS?"
date: 2009-08-14
forum: The Cafe
---

### Post by nuseryame on 2009-08-14
HI,

I'm thinking about getting an old Acer netbook with 512 RAM and 8GB SSD.

I looked at Ubuntu Remix and Xubuntu to put on it, however with the recommended requirements, it'd take up more than half of RAM and 80% + storage.

But really, all I want is to go on the internet with it, through a wireless connection, that is all. If I want email I'll use google, if I want docs I'll use google. All I need is just a browser on it.

So what I want is a tiny o/s without things I don't need, so I can turn on the netbook and be online in seconds.

How much difference where there be in terms of memory available between a gnome desktop environment, and just using a window manager on its own, like Fluxbox?

I have seen Puppy Linux and others, but so they still have editors and image editing etc that I don't need.

---

### Post by ubudog on 2009-08-14
Have you seen Damn Small Linux?  [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by vallis on 2009-08-14
Hi,
I'm sure you could install something like xubuntu or maybe fluxbuntu then uninstall all the stuff you don't need.
You could then configure autologin and a startup script for a browser (in full screen) and you're sorted!

If you're feeling brave I'm sure you could do without a desktop environment and simply run X11 with a display manager. That'd probably need some configuring though.

V.

---

### Post by ubudog on 2009-08-14
> **vallis said:**
> Hi,
I'm sure you could install something like xubuntu or maybe fluxbuntu then uninstall all the stuff you don't need.
You could then configure autologin and a startup script for a browser (in full screen) and you're sorted!

If you're feeling brave I'm sure you could do without a desktop environment and simply run X11 with a display manager. That'd probably need some configuring though.

V.

Yeah, that would probably work.

---

### Post by Raffles10 on 2009-08-14
[#!CrunchBang]("http://crunchbanglinux.org/") Lite edition might suit your needs, it's Ubuntu based.

---

### Post by ubudog on 2009-08-14
> **Raffles10 said:**
> [#!CrunchBang]("http://crunchbanglinux.org/") Lite edition might suit your needs, it's Ubuntu based.

I would also like to try that.  Looks kinda cool.

---

### Post by celticbhoy on 2009-08-14
if you get a decent 8g ssd card you can use it as /home giving extra space

---

### Post by gjoellee on 2009-08-14
TinyCore is an interesting distribution which has an ISO image of 11MB at the moment. It has a nice repo, with applications as in example: gimp.

---

### Post by ubudog on 2009-08-14
> **gjoellee said:**
> TinyCore is an interesting distribution which has an ISO image of 11MB at the moment. It has a nice repo, with applications as in example: gimp.

Wow.  :guitar: :guitar: :guitar:

---

### Post by gjoellee on 2009-08-14
> **ubudog said:**
> Wow.  :guitar: :guitar: :guitar:

yeah, that is impressing...here is a little larger list with ISO sizes and links.

**TinyCore 1.2** -- _ISO=11mb_ -- [http://tinycorelinux.com/](http://tinycorelinux.com/)

[COLOR="Silver"]**SliTaz 2.0** -- _ISO=29mb or 1gb_ -- [http://www.slitaz.org/en/](http://www.slitaz.org/en/)[/COLOR]

**Puppy Linux 4.2.1** -- _ISO=100mb_ -- [http://www.puppylinux.org/](http://www.puppylinux.org/)

[COLOR="silver"]**TinyMe 2008.1** -- _ISO=149mb_ -- [http://www.tinymelinux.com/doku.php](http://www.tinymelinux.com/doku.php)[/COLOR]

**Damn Small Linux (DSL)** -- _ISO=50mb_ -- [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

[COLOR="silver"]**Arch Linux** -- _ISO=167mb-363mb (depends on which ISO you prefer)_ -- [http://www.archlinux.org/](http://www.archlinux.org/)[/COLOR]

---

### Post by ve4cib on 2009-08-14
> **nuseryame said:**
> HI,

I'm thinking about getting an old Acer netbook with 512 RAM and 8GB SSD.

I looked at Ubuntu Remix and Xubuntu to put on it, however with the recommended requirements, it'd take up more than half of RAM and 80% + storage.

But really, all I want is to go on the internet with it, through a wireless connection, that is all. If I want email I'll use google, if I want docs I'll use google. All I need is just a browser on it.

So what I want is a tiny o/s without things I don't need, so I can turn on the netbook and be online in seconds.

How much difference where there be in terms of memory available between a gnome desktop environment, and just using a window manager on its own, like Fluxbox?

I have seen Puppy Linux and others, but so they still have editors and image editing etc that I don't need.

A while back I installed Ubuntu 8.04 onto a 2GB thumb drive.  I managed to get it down to about 1.5GB and uses less than 128MB of RAM (somewhere in the area of 30-60MB if I recall correctly).  Purging a few other applications could probably drop that even lower.

Basically what you need is an Alternate Install CD, and install a command-line system on your machine.  This will install the absolute minimum Ubuntu can give you (and uses about 500MB).

Next install what you actually *need* using apt-get.  Usually this will include...

- Xorg
- a window manager (I like Fluxbox, though LXDE, OpenBox, EvilWM, or anything small will do -- basically no Gnome, no KDE, and debatably no XFCE)
- a file browser (Thunar, EmelFM, or PCManFM are all good options)
- extra drivers for your hardware (wifi, video cards, etc...)
- ALSA (so you have sound)


Next grab the stuff you don't technically need, but is really nice to have:

- web browser (I like Firefox, but there are lighter and smaller options like Epiphany and Dillo) (Optionally include plugins like Java and Flash)
- text editor (Geany, GEdit, Kate, Leafpad, etc...)
- media player (I suggest either VLC or MPlayer)
- GUI configuration tools (Synaptic, Update-Manager, etc...)
- graphical login manager (SLIM is nice for small installs)
- network manager (WICD is great)


This should bring you to somewhere around 1-1.3GB.  Then install whatever other apps you need/want, and move your personal files over.  Done.

You can do something similar with pretty much any distro (Debian, Fedora, etc...).  Start with a minimal command-line system and then build up from there.  It's kind of fun to do (if you're weird like me and consider installing and tweaking packages fun).

---

### Post by fela on 2009-08-14
If you don't mind a bit of configuring, Ubuntu can be configured to use very little resources. You can uninstall lots of unnecessary apps and stuff, a good reason to use Ubuntu is its user friendlyness and incredible OOTB hardware support. Like when you plug in a printer it will say (most of the time) 'printer found' and auto configure it. If not it's very easy to configure it anyway.

I've tried XFCE (xubuntu's desktop environment) - I hated it really TBH. It didn't seem to use much less resources than Gnome (on a EEE PC 700 netbook) and the file manager is nothing to show off about (that was really my worst gripe with it).

You could always install Gentoo on it to get the most customized configuration you could get (another good one for that I think is Linux From Scratch, where you compile absolutely everything from source. It would take ages on a not-so-fast netbook CPU though :P). You could also try Arch, where I don't think you compile everything from source but it's still extremely configurable, and doesn't care what desktop environment you install on it. I had a hard time configuring it once though, but it was probably due to virtualbox's restrictions.

In fact there are endless possibilities really, I recommend checking out google for other people's experiences.

EDIT: didn't see the person above me give that excellent advice.

---

### Post by hockeyfighter09 on 2009-08-14
I would suggest putting Arch linux on it with a Wm such as Openbox or Fluxbox. Then build it from the ground up.

---

### Post by ubudog on 2009-08-14
Like fela said, Ubuntu can be configured to run using very little resources.  I would suggest that because Ubuntu is a great OS. :)

---

### Post by rajcan on 2009-08-14
DSL is really nice and tiny, but because it runs on an older linux kernel it may not recongize your wireless card. There is a larger version of DSL called DSL-Not!, which uses a more up-to-date kernel, but it's still in development. 

Here's the site for DSL-N: [http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)

---

### Post by Ranax on 2009-08-14
> **nuseryame said:**
> HI,

I'm thinking about getting an old Acer netbook with 512 RAM and 8GB SSD.

I looked at Ubuntu Remix and Xubuntu to put on it, however with the recommended requirements, it'd take up more than half of RAM and 80% + storage.

But really, all I want is to go on the internet with it, through a wireless connection, that is all. If I want email I'll use google, if I want docs I'll use google. All I need is just a browser on it.

So what I want is a tiny o/s without things I don't need, so I can turn on the netbook and be online in seconds.

How much difference where there be in terms of memory available between a gnome desktop environment, and just using a window manager on its own, like Fluxbox?

I have seen Puppy Linux and others, but so they still have editors and image editing etc that I don't need.

If you have the knowledge to, build your install from scratch with the Ubuntu server disc.

---

### Post by Wiebelhaus on 2009-08-14
Look out for [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") But as mentioned Puppy Linux is the bomb.

---

### Post by Skripka on 2009-08-15
> **gjoellee said:**
> yeah, that is impressing...here is a little larger list with ISO sizes and links.

**TinyCore 1.2** -- _ISO=11mb_ -- [http://tinycorelinux.com/](http://tinycorelinux.com/)

[COLOR="Silver"]**SliTaz 2.0** -- _ISO=29mb or 1gb_ -- [http://www.slitaz.org/en/](http://www.slitaz.org/en/)[/COLOR]

**Puppy Linux 4.2.1** -- _ISO=100mb_ -- [http://www.puppylinux.org/](http://www.puppylinux.org/)

[COLOR="silver"]**TinyMe 2008.1** -- _ISO=149mb_ -- [http://www.tinymelinux.com/doku.php](http://www.tinymelinux.com/doku.php)[/COLOR]

**Damn Small Linux (DSL)** -- _ISO=50mb_ -- [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

[COLOR="silver"]**Arch Linux** -- _ISO=167mb-363mb (depends on which ISO you prefer)_ -- [http://www.archlinux.org/](http://www.archlinux.org/)[/COLOR]

Bingo.

IMHO, Any distro which has a name ending with "-buntu" is highly unlikely to be lightweight or at all minimal, in any sense of meaning.

PS-I *know* for Arch, there is a SPECIFIC (and big) entry in the Arch Wiki about getting Acer netbooks working to the best-est.

---

### Post by &#32 Greg on 2009-08-15
I'd probably start with a minimal distro- Arch, or Debian NetInst for instance, and install EvilWM or DWM or the like, and keep all my apps light.

---

### Post by Regenweald on 2009-08-15
> **Skripka said:**
> Bingo.

IMHO, Any distro which has a name ending with "-buntu" is highly unlikely to be lightweight or at all minimal, in any sense of meaning.

PS-I *know* for Arch, there is a SPECIFIC (and big) entry in the Arch Wiki about getting Acer netbooks working to the best-est.

That's kind of an unnecessary swipe at *buntu isn't it ? I mean, the minimal cd installer is all of 9-11 megs. Once that is complete you can install the widest variety of minimal software and still enjoy the hardware detection of *buntu.

Arch is amazing, true, but in Linux minimal depends on the user not so much the distro.

---

### Post by &#32 Greg on 2009-08-15
> **Regenweald said:**
> That's kind of an unnecessary swipe at *buntu isn't it ? I mean, the minimal cd installer is all of 9-11 megs. Once that is complete you can install the widest variety of minimal software and still enjoy the hardware detection of *buntu.

Arch is amazing, true, but in Linux minimal depends on the user not so much the distro.

Well, to be fair, with that exception (which is basically a Debian netinst) the *buntus are disproportionally heavy. Take Xubuntu- extremely heavy XFCE distro.

---

### Post by HappinessNow on 2009-08-15
Macpup Opera FTW!!!!! =P~#-o:lol:

---

### Post by daverich on 2009-08-15
I too have a fond spot for the puppy.

Fantastic tool.

I have an asus 2g, which is a very basic version of the EEE.

I use it to stream our backing tracks with the band using puppylinux - xubuntu cannot do this on this machine, it glitches and chokes up. Puppy is slick and does it no problem.

Kind regards

Dave Rich

---

### Post by sideaway on 2009-08-15
Considered SliTaz?

---

### Post by celticbhoy on 2009-08-15
As you are looking at the Aspire One, if you install the Linpus linux that comes with it the left hand SSD slot can be used to add to the system storage. It isnt the best linux out there but it can be configured to use a full XFCE desktop instead of the netbook launcher that is on by default. It also loads quick and the network manager works better with the netbook than any other I have tried (it is even quite simple to connect to JoikuSpot on my Nokia N95 - cant do it with Ubuntu). Whatever distro you go for just make sure that you update the BIOS when you get it, as it will stop some problems later on.

---

### Post by jaxxstorm on 2009-08-15
[Icebuntu]("http://icebuntu.com") Is currently being developed which should be lightning fast :)

---

