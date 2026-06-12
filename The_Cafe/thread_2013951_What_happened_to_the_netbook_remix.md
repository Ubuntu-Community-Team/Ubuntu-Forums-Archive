---
title: "What happened to the netbook remix?"
date: 2012-07-01
forum: The Cafe
---

### Post by mechanic on 2012-07-01
I am just running through various possibilities for a light fast system on my Dell Mini-10v (1GB RAM, 1GHx Atom processor); after some time using Fuduntu I'm looking for a change. My partner here suggested trying U 10.04 Netbook Remix as it's a Long Term Support distro rather different from Gnome3 or Unity. 
What surprised me was how difficult it was to find the ISO file for this distro. Not on the main Ubuntu site, the search doesn't throw up anything useful and the lists under 'alternative downloads' don't show the Netbook Remix although the Ubuntu Gnome file is there. Similarly on most mirror sites and third party software sites. Eventually I did find a copy but it was hard work!

Why is this version so hard to find? I think the remix interface (or UNE I think it's also called) is really good looking and easy to use on a small screen device (1024x600). Anything based on GNOME3 is hopeless on such a small screen. I can see that Ubuntu might not have wanted to progress this variant as well as the Unity line, but surely it's worth keeping as a possible alternative? And why make a LTS hard to find?

Any thoughts?

---

### Post by rai4shu2 on 2012-07-01
I don't think Netbook Remix was part of the LTS. Just the normal "Desktop" group of packages.

That said, Unity is really just Ubuntu + UNR (or that was its stated intention).

---

### Post by ajgreeny on 2012-07-01
10.04 did originally have a netbook version with a desktop rather like unity, with icons on the left hand side of the screen, etc etc, but now that unity has arrived the netbook version is not available any more even for 10.04.4 which is the current point version of 10.04.

If you really want a fast desktop environment on that netbook have a look at Lubuntu 12.04 which runs well and is much faster than gnome or unity.  You can also choose to run the netbook desktop of LXDE which is the DE of Lubuntu.  I have been using Lubuntu on my old laptop and my netbook for a long time now and would suggest there is nothing better if you want to stay in the *ubuntu family.

However, if you want to really try things that are a little different, also have a look at Bodhi, which uses the ubuntu repos but also adds its own, and uses the E17 desktop.  It might take a bit of getting used to but is worth investigating.

---

### Post by forrestcupp on 2012-07-01
Yeah, after Unity came out, it mysteriously disappeared because they want Unity to be their Netbook version, too. But like you said, if you search deep into the mirrors, you can still find copies of it out there.

---

### Post by fuduntu on 2012-07-01
> **mechanic said:**
> I am just running through various possibilities for a light fast system on my Dell Mini-10v (1GB RAM, 1GHx Atom processor); after some time using Fuduntu I'm looking for a change. My partner here suggested trying U 10.04 Netbook Remix as it's a Long Term Support distro rather different from Gnome3 or Unity.

What's causing you to want to look for something else?

---

### Post by mechanic on 2012-07-01
> **ajgreeny said:**
> 10.04 did originally have a netbook version with a desktop rather like unity, with icons on the left hand side of the screen, etc etc, but now that unity has arrived the netbook version is not available any more even for 10.04.4 which is the current point version of 10.04.

Yes I know this, but I wonder why all (most) copies of this on various systems seem to have been removed! Are they ashamed of it? They shouldn't be!

> If you really want a fast desktop environment on that netbook have a look at Lubuntu 12.04 which runs well and is much faster than gnome or unity.  You can also choose to run the netbook desktop of LXDE which is the DE of Lubuntu.  I have been using Lubuntu on my old laptop and my netbook for a long time now and would suggest there is nothing better if you want to stay in the *ubuntu family.
Yes I thought of installing Lubuntu - I could run the LXLauncher which has a nice interface!

> However, if you want to really try things that are a little different, also have a look at Bodhi, which uses the ubuntu repos but also adds its own, and uses the E17 desktop.  It might take a bit of getting used to but is worth investigating.
I've looked at Bodhi but it didn't seem polished. The setup was a bit flakey too.

Thanks for the suggestions!

---

### Post by mechanic on 2012-07-01
> **fuduntu said:**
> What's causing you to want to look for something else?
I was playing with the latest Consumer Preview of Win8 last week; it looks so smart and polished, it makes distros based on traditional Applications/Places/Desktop menus look old fashioned. Fuduntu seems stuck, it's only just got to grips with Grub2, and shows no sign of moving to Gnome3 (not that that would help with my netbook, Gnome3 demands more screen space). Even Win8 doesn't seem cramped, but there are performance issues that make it hard to use on my netbook.

OK I admit it, I'm a closet distro-hopper!

---

### Post by neu5eeCh on 2012-07-01
Shuttleworth wants Unity to "unite" all operating environments -- laptops, desktops, TVs, phones, microwaves, dishwashers, dryers, hair dryers, Stereos, Cereal Boxes, etc. --  hence "unity".  As far as Shuttleworth is concerned, he probably sees no need for Netbook Remix now that we have Unity. 

[CENTER]Mechanic.

_**Resistance is futile.**_
[/CENTER]

---

### Post by neu5eeCh on 2012-07-01
> **mechanic said:**
> I was playing with the latest Consumer Preview of Win8 last week; it looks so smart and polished, it makes distros based on traditional Applications/Places/Desktop menus look old fashioned. Fuduntu seems stuck, it's only just got to grips with Grub2, and shows no sign of moving to Gnome3 (not that that would help with my netbook, Gnome3 demands more screen space). Even Win8 doesn't seem cramped, but there are performance issues that make it hard to use on my netbook.

OK I admit it, I'm a closet distro-hopper!

That's interesting. So, do you find it better or easier to use than any given linux distro? Do you prefer it above and beyond Windows 7?

---

### Post by fuduntu on 2012-07-01
> **mechanic said:**
> I was playing with the latest Consumer Preview of Win8 last week; it looks so smart and polished, it makes distros based on traditional Applications/Places/Desktop menus look old fashioned.

I like 7, but install Office on Windows 8 and then come back and tell me more about polish. :P

It'll probably get there, but it's going to take a while.  Once you install non-8 optimized apps it looks like Windows 3.1 with a big border around the icon so it fits on the page.

> **mechanic said:**
> Fuduntu seems stuck, it's only just got to grips with Grub2, and shows no sign of moving to Gnome3 (not that that would help with my netbook, Gnome3 demands more screen space).

Ahh, fair enough about GRUB 2 but we have lots of things other distros don't yet - like kernel 3.4.4 and Chromium 20 (going to stable today) so it is a balancing act.  We don't have enough active contributors to be much bigger, but we manage to keep up with what's deemed important very well.

Concerning GNOME 3, I looked at Fedora 17 just today - GNOME 3 is still a big joke so we won't have that anytime soon.  Sticking with the traditional desktop has carried us far so far, no reason to change it quite yet.  I can understand that some people seem do like it though.

> **mechanic said:**
> Even Win8 doesn't seem cramped, but there are performance issues that make it hard to use on my netbook.

OK I admit it, I'm a closet distro-hopper!

Fair enough, I was just looking to see if there was anything specific we were doing wrong, but I'm not getting that vibe.  Good luck wherever you land! :D

---

### Post by Paqman on 2012-07-02
> **VTPoet said:**
> As far as Shuttleworth is concerned, he probably sees no need for Netbook Remix now that we have Unity. 

[CENTER]Mechanic.

_**Resistance is futile.**_
[/CENTER]

Considering Unity grew out of the netbook edition that's hardly an irrational idea. This was all announced officially some time ago.

There's no need for a seperate netbook remix any more, as the netbook remix is now used on all desktops. Makes sense. The old pre-Unity netbook interface was pretty nasty and isn't supported any more.

---

### Post by mechanic on 2012-07-02
> **Paqman said:**
> Considering Unity grew out of the netbook edition that's hardly an irrational idea. This was all announced officially some time ago.

There's no need for a seperate netbook remix any more, as the netbook remix is now used on all desktops. Makes sense. The old pre-Unity netbook interface was pretty nasty and isn't supported any more.

My point is that the remix interface in 10.04 is far from nasty, I rather like it, and anyway we should have choice, no? Why hide the option from us?

Thanks for your thoughts everyone!

---

### Post by mechanic on 2012-07-02
> **VTPoet said:**
> That's interesting. So, do you find it better or easier to use than any given linux distro? Do you prefer it above and beyond Windows 7?

On that specific point clearly win8 is not yet finished, there's a lot of polishing yet to do. Win7 is finished and I use that most of the time (shhhhh!). But some of the design effort that's gone into Win8 is just breathtaking! I only wish such effort went into Linux distros, Ubuntu isn't bad on that scale some are just ghastly.

For people who say Windows is expensive, note that Enterprise Editions of Win7 have been available for free evaluation for months, mine is a year old and has to be re-armed (!) every 90 days or so, you get 5 or 6 goes so that's a lot of free time! This Win8 preview is good till January with another Release Candidate available for review before then (AIUI).

---

### Post by Paqman on 2012-07-02
> **mechanic said:**
> My point is that the remix interface in 10.04 is far from nasty, I rather like it, and anyway we should have choice, no? Why hide the option from us?


Well, the packages are still in the repos, so you could just download the regular Ubuntu ISO then install [ubuntu-netbook-remix]("apt:ubuntu-netbook-remix") and switch to it from the login screen.

---

### Post by mechanic on 2012-07-02
> **Paqman said:**
> Well, the packages are still in the repos, so you could just download the regular Ubuntu ISO then install [ubuntu-netbook-remix]("apt:ubuntu-netbook-remix") and switch to it from the login screen.

The remix package seems to contain just:
/usr/share/doc/ubuntu-netbook-remix/changelog.gz
/usr/share/doc/ubuntu-netbook-remix/copyright
although there is a dependent package ubuntu-netbook that calls in the usual programs and a package of default settings (for gconf and so on). I suppose that's one way to do it although I haven't tried it but not so convenient as an ISO in the download list on a mirror!

---

### Post by Paqman on 2012-07-02
> **mechanic said:**
> The remix package seems to contain just:
/usr/share/doc/ubuntu-netbook-remix/changelog.gz
/usr/share/doc/ubuntu-netbook-remix/copyright
although there is a dependent package ubuntu-netbook that calls in the usual programs and a package of default settings (for gconf and so on). I suppose that's one way to do it although I haven't tried it but not so convenient as an ISO in the download list on a mirror!

Yep, it's a meta-package. Same as any of the other meta-package, all they really are is a set of dependencies. All the desktops have a meta-package to make installing or upgrading all the various components nice and simple.

---

### Post by ajgreeny on 2012-07-02
If you take a look at the image of the netbook remix for 10.04 in synaptic you will find that it now looks very much more like unity than it used to back in April 2010, with the same looking launcher bar as unity, but also some large desktop icons for, I think, groups of applications.

---

### Post by codingman on 2012-07-02
They mixed them both together, but puppy and bodhi are some good distros for a netbook to look into.

---

