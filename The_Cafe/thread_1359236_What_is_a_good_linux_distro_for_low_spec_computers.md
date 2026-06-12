---
title: "What is a good linux distro for low spec computers?"
date: 2009-12-19
forum: The Cafe
---

### Post by marcher22 on 2009-12-19
Hi the computer im using has really low specs. I'm currently running Ubuntu 9.1 but it's kind of slow. I heard there was Xubuntu but before I go running into that I want to know if there is any OTHER Operating Systems for low spec computers like mine. That could run smoother.

Here are just some things I can say:

256MB of Ram
Hard drive is about 12GB
and If I'm not mistaken Pentium III

I also heard of " puppy linux"...not to sure about that either.

Alright thanks:)

---

### Post by snowpine on 2009-12-19
Puppy would be my suggestion, too... at least give it a try to see if you like it. :)

---

### Post by scorp123 on 2009-12-19
CrunchBang maybe?

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by kellemes on 2009-12-19
dsl

---

### Post by synapsys on 2009-12-19
PCLinuxOS

[http://pclinuxos.com/](http://pclinuxos.com/)

---

### Post by Marvin666 on 2009-12-19
I'd have to second [DSL]("http://damnsmalllinux.org/"). It can run completely from ram, and the os with all the bundled software is only 50mb. You can run it from a flash drive, cd, or install it to the hard drive.

---

### Post by ubudog on 2009-12-19
Crunchbang lite edition:[http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit]("http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit")  32bit would probably be better than 64.

---

### Post by Bachstelze on 2009-12-19
> **ubudog said:**
> Crunchbang lite edition:[http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit]("http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit")  32bit would probably be better than 64.

64 bit would not work at all. ;) Anyway, this is really not what I would consider small. Puppy and Cruchbang are designed for much smaller specs than that. What I would do is install a command-line Ubuntu and a light environment on top of it. XFCE could run reasonable well, otherwise you have LXDE.

---

### Post by Chesamo on 2009-12-19
I've gotten Ubuntu to run fluidly on lower specs if installed from the [Minimal CD](https://help.ubuntu.com/community/Installation/MinimalCD) then building up.

---

### Post by NoaHall on 2009-12-19
Debian, DSL, Puppy, Arch. Take your pick.

---

### Post by &#32 Greg on 2009-12-19
Slitaz or TinyCore for out of the box.

Things like Arch, Debian netinst, Crux, Gentoo, etc. will all work very well if you put the effort into them.

---

### Post by NoaHall on 2009-12-19
> **  Greg said:**
> Slitaz or TinyCore for out of the box.

Things like Arch, Debian netinst, Crux, Gentoo, etc. will all work very well if you put the effort into them.

You know, it has a bit more RAM than that. It can easily run DSL/Puppy.

---

### Post by cguy on 2009-12-19
Crunchbang - all the convenience of Ubuntu in a light package :)

---

### Post by HappyFeet on 2009-12-19
This must be the 8,000th thread on this subject.

---

### Post by mivo on 2009-12-19
As for DSL, hasn't the project been discontinued?

---

### Post by docus on 2009-12-19
I'm trying to install Crunchbang on an old P3 600mhz with 128 megs of ram ... it booted into the live cd but doesn't seem to install to the hard drive.

I couldn't get the Zenwalk live cd to load at all...

:(

---

### Post by docus on 2009-12-19
double post

---

### Post by thewooferbbk on 2009-12-19
Hey! puppy linux or fluxbox are my suggestions...
just go distrowatch.com, review and download them from there..
Peace!

---

### Post by nmaster on 2009-12-19
you should take a look at this: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
you can use ubuntu but just use something lighter than gnome.

---

### Post by earthpigg on 2009-12-19
if you are up to a command line only 9.10 install, [this may be of use.]("http://sites.google.com/site/masonux/home/notes-to-myself")

tldr version:
```
sudo apt-get install xorg lxde firefox synaptic empathy gdebi jockey-gtk wicd gdm
```

if you'd prefer a 9.04 LiveCD, [this]("http://sites.google.com/site/masonux/downloads") may be of use.

crunchbang lite is also great. only functionality-centric reason to use my stuff over theirs is that, out of the box, a) crunchbang has conky and looks prettier by default and b) masonux (lxpanel, more accurately) has menus that update automatically when you install new software. pick which matters more to you.

crunchbang lite + lxpanel is also nice, i've done it myself.

---

### Post by &#32 Greg on 2009-12-19
> **NoaHall said:**
> You know, it has a bit more RAM than that. It can easily run DSL/Puppy.

I find Slitaz to be nicer than both.

---

### Post by Stan_1936 on 2009-12-19
**[COLOR="Blue"][size="7"]MacPup Foxy 3[/size][/COLOR]**
- [http://macpup.org/foxy3.php](http://macpup.org/foxy3.php)
- [http://www.youtube.com/watch?v=QES2rqRhXgs](http://www.youtube.com/watch?v=QES2rqRhXgs)

It's as fast as a bullet!

---

### Post by ofb on 2009-12-19
It may be the 8,000th post, but it's a moving target as distros & the definition of "old" move forward. Also people tend to post what they've heard rather than what they've used for more than a day.

I've got PCLOS 2009.2 on a P3 450, 640mb, 14gig, NVidia MX440SE. It runs fine as a secondary computer.

=Comments=

- 256mb is not a lot of RAM. This is probably going to be your biggest bottleneck. If you can raid another old box to double that, it'll help.

- Old video card support is becoming an issue with various distros. Happily, PCLOS still likes the old NVidia.

- Use XFE for file management. Konqueror/Dolphin/Nautilus are noticeably heavier.


=Out-of-date Comments=

Until about a year ago I used to try a lot of the lightweight distros on my obsolete hardware. Things can change since then, so add a grain of salt here:

- I didn't like most of the truly lightweight distros like DSL and Puppy. While interesting, they were just too different from full-fledged distros like Ubuntu. I kept tripping over myself as I switched back and forth.

- Also they always seemed to lack a GUI configuration I needed. I get tired of dealing in terminal after a while. (I'm getting old - find I just don't remember well enough and have to keep re-learning what I once knew. I started with home computers in 78.)

- Can't remember why I didn't stay with Crunchbang. I remember being impressed but ultimately not keeping it. Possibly the same reasons.

- I didn't like Xubuntu. It's just not light enough, while losing the familiar Gnome or KDE desktop. I found I could make Gnome and KDE (3.5) run as well or better. And PCLOS is definitely better stock.


I'm looking forward to Lubuntu, but that project is probably a good year away from delivering an installable. Meanwhile PCLOS seems to be a very nice combination of light weight with good support and full-featured GUI.

---

### Post by docus on 2009-12-19
From the Crunchbang live cd I choose ***install crunchbang*** from the menu, but nothing happens!

---

### Post by snowpine on 2009-12-19
> **docus said:**
> I'm trying to install Crunchbang on an old P3 600mhz with 128 megs of ram ... it booted into the live cd but doesn't seem to install to the hard drive.

I couldn't get the Zenwalk live cd to load at all...

:(

128mb ram is not enough for CrunchBang in my experience, sorry. :(

Try Puppy, DSL, SliTaz "loram flavor", TinyCore, etc. ;)

(I'm typing this right now from an old pentium 3 running SliTaz and the Midori browser.)

---

### Post by ofb on 2009-12-19
docus, here's the CrunchBang forum.
[http://crunchbanglinux.org/forums/](http://crunchbanglinux.org/forums/)

---

### Post by docus on 2009-12-19
> **snowpine said:**
> 128mb ram is not enough for CrunchBang in my experience, sorry. :(

Try Puppy, DSL, SliTaz "loram flavor", TinyCore, etc. ;)

(I'm typing this right now from an old pentium 3 running SliTaz and the Midori browser.)

> **ofb said:**
> docus, here's the CrunchBang forum.
[http://crunchbanglinux.org/forums/](http://crunchbanglinux.org/forums/)

Thanks to both of you for the advice - I'm downloading Puppy and Slitaz, and I'll check out the #! forums.  

I'm a bit sad #! wont run with 128mb ram - I liked the dark and minimalist style of it a lot.

---

### Post by snowpine on 2009-12-19
> **docus said:**
> Thanks to both of you for the advice - I'm downloading Puppy and Slitaz, and I'll check out the #! forums.  

I'm a bit sad #! wont run with 128mb ram - I liked the dark and minimalist style of it a lot.

#! is really just Ubuntu with a different windows manager (openbox instead of gnome).

You can use a dark wallpaper and theme in any distribution. Linux is infinitely customizable like that. :)

---

### Post by earthpigg on 2009-12-19
> **docus said:**
> From the Crunchbang live cd I choose ***install crunchbang*** from the menu, but nothing happens!

if #! 9.10 is having the same problems that i am having with masonux 9.10, running 'ubiquity' from a terminal should do it for you. (both use remastersys, both use openbox, etc)

(same trick needs to be used in masonux 9.10 beta2... haven't decided if i want to declare something stable with such a silly and glaring issue)

---

### Post by darrelljon on 2009-12-19
AntiX.
What is the difference between Crunchbang and Crunchbang Lite and do Crunchbang have any plans to release 9.10?

---

### Post by earthpigg on 2009-12-19
> **darrelljon said:**
> What is the difference between Crunchbang and Crunchbang Lite?

Crunchbang has a zillion apps installed by default, like the official *buntu releases.

Crunchbang Lite is for folks that already know what games, media player, word processor, audio file editor, spreadsheet app, etc, they want - so it comes with none preinstalled and assumes you already know how a package manager works.

each has its use, of course.

---

### Post by Groucho Marxist on 2009-12-19
Xubuntu worked fantastically on my old Pentium III computer that had 10 GB of hard drive space :D

---

### Post by snowpine on 2009-12-19
> **darrelljon said:**
> AntiX.
What is the difference between Crunchbang and Crunchbang Lite and do Crunchbang have any plans to release 9.10?

CrunchBang has more applications installed by default; CB Lite only has the basics (browser, text editor, etc).

See here: [http://crunchbanglinux.org/wiki/applications](http://crunchbanglinux.org/wiki/applications)

There has been no official announcement yet about future CrunchBang releases.

---

### Post by XubuRoxMySox on 2009-12-19
> **Groucho Marxist said:**
> Xubuntu worked fantastically on my old Pentium III computer that had 10 GB of hard drive space :D

/\ This.

I was amazed to find that **[COLOR="Blue"]Karmic Xubuntu[/COLOR]** ran leaner and faster than even Crunchbang did on a low-resource laptop!!

I'm using it on the studio 'puter now. It replaces my old homemade minimal Ubuntu/LXDE mixture and it screams. Mind-bending speed on a 5-year-old Dell.

I'm still a LXDE fan though, and I expect that when the "Buntu Barrier" is broken (that's what I call whatever it is about even minimal Ubuntu that makes LXDE so buggy for me), soon I hope, that I'd jump right back on that bandwagon. On the studio 'puter anyway.

But I have fallen in love with Crunchbang's stark beauty and power. It's running on my laptop again in spite of it's slightly slower speed compared to Xubuntu just because it's so very COOL!

-Robin

---

### Post by marcher22 on 2009-12-20
Alirght guys thanks. I guess I'm going to experiment with all these different operating systems. I'm probably going to try out Puppy first , and maybe crunch bag because those were both brought up frequently.

I'm trying to revive an older computer in my basement so that our "main" computer won't be crowded with the amount of people staying in my house for the next while.

Also thanks to whoever mentioned distrowatch

---

