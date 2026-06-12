---
title: "PROS &amp; CONS - Gnomebuntu vs Gnome PPA"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sml on 2012-09-28
what are the pros and cons of:

gnomebuntu   vs   ubuntu & gnome PPA?

---

### Post by kansasnoob on 2012-09-28
First of all I need to clarify that there is NO Gnomebuntu AFAIK. There is this:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta)

The official name has not yet been decided but the "meta-package" name in the Quantal repos is 'ubuntu-gnome-desktop'. The fact that it's in the repos is a positive sign that this will really happen sometime in the not too distant future :)

The most basic differences are that Ubuntu now uses Unity + Compiz (+ llvmpipe when required), but the 'ubuntu-gnome-desktop' does NOT even have Compiz installed but rather uses 'mutter' w/gnome-shell by default.

Second it's rather unfair to consider the differences as "pros & cons". It's really no different than comparing Xubuntu to Lubuntu.

I prefer Lubuntu over Xubuntu but I'm fairly sure that many, many users prefer Xubuntu out of those two options.

Third, but almost off-topic, I'm finding that it's much easier to set up a "classic-look" DE using Jeremy Bicha's respin than it is to start with Ubuntu.

But ultimately it just comes down to figuring out which desktop environment and window manager works best for you, so it's much more a matter of preference and hardware capability than it is "pros & cons" :D

Edit: I see that I left out a huge chunk of info :oops:

Regarding [this PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") you can see that it says:

> === Ubuntu 12.10 (Quantal) ===
Parts of GNOME 3.6 that won't make it into the normal Ubuntu 12.10 repositories.

So if you apply the Quantal filter you can see what packages will (or may) be upgraded by adding the PPA:

[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=quantal](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=quantal)

---

### Post by x-shaney-x on 2012-09-28
PROS & CONS really depend on the individual and what that person prefers.

Basically, using the PPA would only install or upgrade Gnome stuff that you choose to install.
Gnome remix or "Gnomebuntu" is more of a Gnome "as intended", with Gnome's choice of default applications etc, rather than ubuntu's.

---

### Post by Mr.JJ on 2012-09-29
> **kansasnoob said:**
> Second it's rather unfair to consider the differences as pros & cons. It's really no different than comparing Xubuntu to Lubuntu.

But ultimately it just comes down to figuring out which desktop environment and window manager works best for you, so it's much more a matter of preference and hardware capability than it is

 You got the question all wrong. He is not asking about the difference between ubuntu and gnome remix. He is asking about the diff between gnome within ubuntu and in gnome remix. 

The basic diff is that if you like to use gnome, and do not much care about unity, gnome remix is the best choice. It comes with only the gnome packages installed. No unity, no global menu, no libnotify etc., so a lot of space saved. 
Second, the application selection etc. are far more closer to what gnome developers intended and you get a better gnome experience in gnome remix (with web instead of firefox, softwares instead of ubuntu software centre, no ubuntuone etc.). You also get all the gnome artwork instead of the ubuntu ones (grub menu, plymouth, default wallpaper etc.). 
Third, you will have to replace lightdm with gdm to get a complete gnome experience. 

Basically it comes down to this, how much passionate you are for gnome. For some of us (who do not care about unity) gnome remix does the basic work for us. But if you just want to test gnome and prefer unity as main desktop (may be you should really give gnome another try?) you could try installing the gnome team ppa and install only those packages. 

The gnome expereince in ubuntu is still nowhere close to fedora implementation and needs lot of improvement. But gnome remix is now making some prgoress with a better gnome implementation. Some of these will be backported to gnome 3 ppa, others not (new control centre etc.). But in the future there might be more and more differences between the both.

---

### Post by Bazon on 2012-09-29
> **Mr.JJ said:**
> The gnome expereince in ubuntu is still nowhere close to fedora implementation and needs lot of improvement.

I have to disagree strongly. 
Because I also had the same idea before (and I prefer Gnome-Shell and don't use unity), I installed fedora 17. But in fact, the Gnome-Experience is much worse:
[LIST=1]
[*]The mouse-hover labels for dash were disappearing all the time. 
[*]Switching an Gnome-Shell-Extension on or off resulted in switching on or off a random other extension.
[*]And, worst of all, I had random Gnome-Shell freezes in fedora.
[/LIST]
I never had such problems with ubuntu or debian.
And additional to that, fedora as an awful font-rendering, especially in Firefox. Yes, there are dozens different tipps how to make it better, but the fonts never looked as good as in ubuntu by default for me.

So because of that Vanilla-Gnome opportunity, fedora nearly got me. But I was really disappointed very bad and have no problem staying with ubuntu.



To the question in #0:
Good question! I'm using a standard ubuntu installation with the meta-package "gnome" added. Yes, that resulted in some problems:
[LIST]
[*]In 12.04, that one: [https://bugs.launchpad.net/ubuntu/precise/+source/gnome-control-center/+bug/965921](https://bugs.launchpad.net/ubuntu/precise/+source/gnome-control-center/+bug/965921) But there was an easy workaround in dconf.
[*]In 12.10, selscting the Gnome-Session in LightDM with mouse doesn't work. You have to know the keyboard keys for that (tab, space and enter) and have to be able to recognize that very slight border for the selected item.
[/LIST]

Both aren't bad for me, but it would still be a problem for me recommending Ubuntu with that for someone else. So my hope is, the Gnome-Remix can be something I'm able to recommend to friends, who are not so deep into OS things... :-)

---

### Post by sml on 2012-09-29
> **Mr.JJ said:**
> You got the question all wrong. He is not asking about the difference between ubuntu and gnome remix. He is asking about the diff between gnome within ubuntu and in gnome remix. 

Actually ... after realising how complicated this can be, I think I might be asking about both! :)

---

