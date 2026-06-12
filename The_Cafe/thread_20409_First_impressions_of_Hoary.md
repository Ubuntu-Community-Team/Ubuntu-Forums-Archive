---
title: "First impressions of Hoary"
date: 2005-03-16
forum: The Cafe
---

### Post by ubuntu-geek on 2005-03-16
I just installed the Hoary preview release and here are my findings and thoughts.

1. The installation processes has definatly been streamlined which I found more user friendly.

2. Xorg setup my Radeon 9550 card automatically very impressive however the screen is off centered a little (no big deal, monitor auto focus fixed that).

3. Did not detect my Audigy 2 Value card this is a major issue IMO since alot of people are using these cards. I had to download the unstable debain package to get my sound working. Apparently Hoary is using Alsa 1.0.6 kernel drivers I hope they fix this.

4. Overall performance is good, much speedier then Warty.

5. The new default theme is nice and clean I like it.

6. The update tool is very nice.

Those are my first impressions of the Hoary preview release.

---

### Post by oddabe19 on 2005-03-16
I've been running hoary since the servers came online.

No serious problems (knock on wood)
everything has been great.

Not thrilled with the direction Gnome and Freedesktop is going with the no editing menus.

Ubuntugeek: Hoary actually uses 1.0.8 alsa.

---

### Post by Knome_fan on 2005-03-16
[QUOTE=oddabe19]
Not thrilled with the direction Gnome and Freedesktop is going with the no editing menus.
[/QUOTE]
Freedesktop is not going in any direction regarding menu editing. Their standard of course allows for menu editing, Gnome just didn't implement it for this release. (Which is a royal PITA imho) But some Gnome dev is working on a menu editor for the next release, so one might argue that the direction in this sence is good.  ;-)

---

### Post by ubuntu-geek on 2005-03-16
[QUOTE=oddabe19]

Ubuntugeek: Hoary actually uses 1.0.8 alsa.[/QUOTE]

Thats what I thought too..

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6892](https://bugzilla.ubuntu.com/show_bug.cgi?id=6892)

---

### Post by jdodson on 2005-03-16
ubuntu-geek and i installed it around the same time of day, strage.... anyways, these are my thoughts.

*ditto on the speed increase, it is very noticable even on my AMD 64 3000+ with a gig-o-ram.

*xorg supports WAY more screen resolutions and refresh rates than xfree did out of the box for my nvidida card.  if i didn't require 3D video i would leave it as is.  the proprietary driver did not afford me any more resolution or refresh than the opensource nv driver.  this is a REALLY cool thing in my book.

*way cool new clearlooks human theme.

* ndiswrapper on main install cd, awesome.

* i would have liked firefox 1.0.1, but i know they had feature freeze so it did not get put in.

* i would like the default gnome backgrounds avialable in the default install.  i know you can get them in universe, not a huge deal though.

* i think a few more themes to choose from would be nice.  not a huge deal, but would be nice.

* i like the new update manager and the way you add respositories in synaptic is pretty cool.

* i am glad they did not make openoffice 2 the default word processor.  from what i have seen from the beta it is junk imo.  did they strip out the gnome widgets?  it looks like it is less integrated to the gtk2 interface.....

---

### Post by jdong on 2005-03-16
I've been using Hoary for a month or so now, so:

1. Faster bootup is definitely noticeable. I also moved over to 5x40GB IDE RAID0 + reiser4 at the same time, so I honestly don't know what to attribute the speedup to!!

2. Firefox 1.0.1 did make it through, because it fixed a few security issues. 6 hours before it became official, I did package a Backport for Hoary and Warty coming from Debian Sid, so I got you guys covered anyway ;)

3.Openoffice.org2 is buggy and unstable. With GTK widgets, it regularly freezes or crashes. Kind of disappointing.

4. GNOME has been bumped down from "tolerable" to "unbearable" for me. I'm a full-time KDE user now.

5. KDE 3.4.0 is very nice. The Switch User functionality is much improved and newbie-friendly.

6. Big thanks to the KUbuntu team!

7. Backports are easier to do now, since all the libraries are now freshened. No more guessing dependencies (for a while)

8. GDM is finicky if zapped -- I filed a bug report on that : [http://bugzilla.ubuntu.com/show_bug.cgi?id=7753](http://bugzilla.ubuntu.com/show_bug.cgi?id=7753)



Overall, an excellent, much more polished release. Way to go, Ubuntu!!

---

### Post by lincr on 2005-03-16
I've been using Ubuntu for a week or so.  Some good things:

Runs great on a Dell GX280, which is newish hardware.
Evolution Exchange support kicked me in the !@#$% for about an hour, but it works with the Exchange server in my office now.  Not sure which thing I did fixed it...
Gnome is beautiful.
Default apps are not annoying (xpdf was a good choice).
Install was real easy.
Printing was easy to set up.

Bad things:
Had to configure X partially with the xf86config console tool, and then add wheel mouse support by hand with vi.  Had lots of initial frustration, only to find that a bios setting allowed normal resolutons and color depths (video ram was set to 1MB, but Windows didn't care;  XP ran at 1024x768x32bpp; set ram to 8MB in bios, and all is well).
Not sure how I got Evolution Exchange working, maybe this is an issue?
Terminal Server Client did not make the impression that it was a front end to vncviewer until I played with it.  Maybe a better name?
wxPython is uninstallable, so btdownloadcurses is the only way to work with BitTorrent files, like the Fedora 4 PPC release...

I like Ubuntu, other than missing a few Debian packages that I like, it's a very well put-together desktop, on one CD!  Hooray.

Don't think I'll use it for a server yet though...

Linc

---

### Post by jdodson on 2005-03-16
[QUOTE=jdong]
2. Firefox 1.0.1 did make it through, because it fixed a few security issues. 6 hours before it became official, I did package a Backport for Hoary and Warty coming from Debian Sid, so I got you guys covered anyway ;)
[/QUOTE]

it just made it into my latest round of updates.  thanks anyways jdong! :D

---

### Post by kleeman on 2005-03-16
Crap I'm getting envious. I still run Warty as the 2.6.11 kernel they use at present will not support my onboard Yukon Gigabit network card (the sk98lin driver sucks). GRRRRR!  :-(  :-(  :-(  One good thing: the developers have promised to fix this issue. Ubuntu developer support is really quite surprisingly good I find....

---

### Post by dusu on 2005-03-17
Hi,

I've installed Hoary yesterday (by an upgrade from Warty).

In the beginning I thought things worked pretty well, but :
- I could not listen to an audio CD, because there was no symbolic link of /dev/cdrom to my actual device /dev/hdc. I do not think this is normal, is it ? I created the link, but anyway, this morning it had disappeared.
- The gnome CD player worked, but the CD kept on jumping
- The same happened with a DVD played by vlc
- The above two points make me think that for me Hoary was not as fast as Warty :( (I'm using a 3 years old laptop, with 900Mhz Celeron proc, but if Hoary is to be faster than Warty, shouldn't it be the case for any computer ??)
- All the above points are written using the past, since I've done a dist-upgrade this morning, and that now, the X-server won't start any more  :-(  Is it to be expected to get into troubles every time one makes a dist-upgrade ? This was just a temporary failure since one hour afterwards a dist-upgrade made things work again :)

Sorry if all these questions are newbies questions... I'me a newbie !
And thanks for your help.

---

### Post by jsgotangco on 2005-03-17
X died on me too after the update today. I will try to update later and check what happened.

---

### Post by jsgotangco on 2005-03-17
Well ok they kinda updated the repository (that was a fast one) and another 40MB+ update (mostly X related) fixed it and I have x.org running again.

I still can't run ratpoison though..any hints?

---

