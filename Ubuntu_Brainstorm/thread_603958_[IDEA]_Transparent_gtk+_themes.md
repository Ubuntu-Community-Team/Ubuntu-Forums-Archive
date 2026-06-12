---
title: "[IDEA] Transparent gtk+ themes"
date: 2007-11-05
forum: Ubuntu Brainstorm
---

### Post by ntfs on 2007-11-05
Now as we have compiz, we also have transparent windows decorations and support for transparent windows(gnome-terminal for example), so it would be nice to let themes make some parts of windows transparent(for example have semi-transparent window, but buttons,lists etc would be opaque). Similar effect can be seen in Windows Vista Aero.

Implementation hints:
It should not be so hard we probably only have to make all gtk windows use ARGB visual by default, that could be made by change to gdk/x11/gdkvisual.c, there is a stuff that detects ARGB visuals, so when it detects one it sets it like a system default visual.
Than a separete gtk-engine would be created.
Is it possoble?

---

### Post by smartboyathome on 2007-11-05
> **ntfs said:**
> Now as we have compiz, we also have transparent windows decorations and support for transparent windows(gnome-terminal for example), so it would be nice to let themes make some parts of windows transparent(for example have semi-transparent window, but buttons,lists etc would be opaque). Similar effect can be seen in Windows Vista Aero.

Implementation hints:
It should not be so hard we probably only have to make all gtk windows use ARGB visual by default, that could be made by change to gdk/x11/gdkvisual.c, there is a stuff that detects ARGB visuals, so when it detects one it sets it like a system default visual.
Than a separete gtk-engine would be created.
Is it possoble?

It is possible, but would be VERY hard to make, and would have to have the ability to also use psuedo transparency. If this gets accomplished, maybe someone should work on transparencies for Metacity.
:lolflag:

---

### Post by 23meg on 2007-11-06
[GtkGLExt]("http://www.k-3d.org/gtkglext/Main_Page") has made some progress but is unmaintained now. Theme level changes will perhaps be possible once upstream GTK+ decides on how to go ahead with integrating OpenGL and compositing.

Related Ars Technica article from the recent FOSSCamp: [Making Linux application user interfaces richer with OpenGL]("http://origin.arstechnica.com/news.ars/post/20071028-making-linux-application-user-interfaces-richer-with-opengl.html")

---

### Post by ntfs on 2007-11-06
It only seems to be extension which allows to use Opengl, but to not to have themes with transparency...

---

### Post by 23meg on 2007-11-06
As I said, themes can start to have transparency once this kind of thing gets included in GTK+.

---

### Post by ntfs on 2007-11-06
No, IMHO the app does not need to use Opengl to take advantag of true transparency (only the composition manager does). Take look for example at gnome-terminal.

---

### Post by 23meg on 2007-11-06
I'm not saying it has to. On a per-application basis, you can do anything. Themes, however, typically apply to all GTK+ widgets in all applications, so to have themes that utilize support for compositing in those widgets, that support needs to have been decided on and implemented in the first place.

---

### Post by RAOF on 2007-11-07
This is actually already possible, and there has been at least one gtk engine produced by people in the Compiz-fusion community with translucent widgets.

Sadly, it's not quite as simple as ensuring every app has an ARGB base pixmap - when you do that, you expose all sorts of unwanted behaviour in other apps (firefox springs to mind).

In short, it's really not very hard to do (and a simple gdk.is_composited() can send you down the non-ARGB codepath).  The problem is that some apps don't render correctly when you give them an ARGB pixmap to draw on.

---

### Post by santiagoward2000 on 2007-11-07
I've been playing around with the fake ARGB plugin sometime ago, but I could never get it to look the way I wanted...
I saw a picture a Mac-using friend sent me of his desktop with a transparent Adium on it, and I wanted to do that with pidgin, but I couldn't find out how... :(

---

### Post by ntfs on 2007-11-07
Oh, so it would break apps? But I believe it still could be solveable, and Ubuntu could be the first distro to have it... What about modifiing GDK's functions to provide non-ARGB behaviour on ARGB visual's so that legacy apps renders correctly, and provide a few new functions for ARGB drawing.
Unfortunately I have no clue about GDK complexity and it's relations to Pango and Cairo, so do you think it would be possible to do such a modification, or is it to complex? Would there be a need to modify Pango and Cairo too?

---

### Post by coolen on 2007-11-08
From the link given above, it looks like this is already in the works (or at least, a goal). I'd say it'd be a while until we see this sort of technology on your average Linux desktop, and a while longer until it makes its way into the default setup, but if it does, I think the FOSS fellows have already proven they'll take full advantage. Sure, transparent menus would be nice, but how about menus that pop out at you, then spin off into the distance when you make a selection, all the while smoking a cigar and insulting your mother?

---

### Post by ntfs on 2007-11-09
I do not need to insult my mother to do the menus trick, I think it could be done using properly configured Beryl :)

---

### Post by delfick on 2007-11-12
> **RAOF said:**
> This is actually already possible, and there has been at least one gtk engine produced by people in the Compiz-fusion community with translucent widgets.

actually, it was back much further than that...
starting back in compiz.net days :D

wasn't it RYX that started doing that ?
(or was it someone else, I forget)
I remember it was fairly cool, but it made some programs screw up, like bittorrent (the program) wouldn't even start, and things like that...

personally though, I can't wait till gtk implements some sort of compositing goodness that makes this possible....

---

### Post by RAOF on 2007-11-12
> **delfick said:**
> actually, it was back much further than that...
starting back in compiz.net days :D
...

Yeah, I know.  I just lump everyone who is/was involved in compiz or beryl and isn't a core compiz hacker into the compiz-fusion community :).

> **delfick said:**
> 
personally though, I can't wait till gtk implements some sort of compositing goodness that makes this possible....

It's already possible.  As I say, you can ask gdk whether there's a composite manager running on the display, and if so ask for pixmaps with an alpha channel.  The trick is programs that fail to work properly with an ARGB pixmap, and I don't think that's fixable in GTK+.

---

### Post by delfick on 2007-11-12
> **RAOF said:**
> Yeah, I know.  I just lump everyone who is/was involved in compiz or beryl and isn't a core compiz hacker into the compiz-fusion community :).

lol, fair enough :D
beryl needs to be forgotten anyways, so that's a good idea :p

> It's already possible.  As I say, you can ask gdk whether there's a composite manager running on the display, and if so ask for pixmaps with an alpha channel.  

is that how like awn, kiba-dock, affinity, etc do their nice composited transparency ?

> The trick is programs that fail to work properly with an ARGB pixmap, and I don't think that's fixable in GTK+.

k then......
that's dissapointing.................

maybe if composited aware widgets were made that had to be specifically enabled by the application, so that it doesn't get enabled on older applications that would otherwise break because of them....
(excuse me if that is already how it is with gdk)

*starts imagining buttons that wobble when they're clicked :D*

---

### Post by coolen on 2007-11-12
It'd take some work, but this is something people want. Look at all the work being done on Compiz. All over the place, people are working together to make it as stable and enjoyable an experience as possible.
Eye candy has become a big part of the Linux desktop. I'm sure the devs won't rest until this is extended to the toolkits, too.

---

### Post by 23meg on 2007-11-28
Mirco Müller demonstrates off-screen widget rendering in GTK+:

[http://macslow.thepimp.net/?p=147](http://macslow.thepimp.net/?p=147)

---

### Post by coolen on 2007-11-28
That is the coolest thing I've seen this side of Sunday.

---

### Post by tjagoda on 2007-11-28
That is abso-freaking-awsome.

---

### Post by smartboyathome on 2007-11-28
Thats very cool, it can't be very usable though, just more eye candy ;)

---

### Post by RAOF on 2007-11-29
> **smartboyathome said:**
> Thats very cool, it can't be very usable though, just more eye candy ;)

Fortunately, the same technology can be used to do useful, as well as cool, things.  Animations become much easier when you don't have to care how bad the half-rendered result looks.  This can also be used for transparent or pulsing widgets.  You can do good things for usability with (subtle) use of these features.

---

### Post by tjagoda on 2007-11-29
"Just" eye candy is a bad way to phrase it, I believe.  Eye candy is significant/important to a good amount of people.

---

### Post by coolen on 2007-12-01
That's the whole point :D

---

### Post by 23meg on 2007-12-13
* [cough]("http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine") *

---

### Post by smartboyathome on 2007-12-13
> **23meg said:**
> * [cough]("http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine") *

That's awesome! I can't wait to see how this project turns out! :D

---

### Post by tehkain on 2007-12-13
This is something I have been hoping to see for a long time. I recently became discouraged with all the negativity but regained some hope with embedded Cairo. Now this just tops it off!

Thanks Cimi!

---

### Post by ntfs on 2007-12-14
It's already there(if it is not fake), See [http://arstechnica.com/journals/linux.ars/2007/12/12/gnome-theme-engine-designer-adds-transparency-to-gtk]("http://arstechnica.com/journals/linux.ars/2007/12/12/gnome-theme-engine-designer-adds-transparency-to-gtk")

Still there is a problem mentioned above: "The application must set an rgba colormap (for example for the main window).
This will take 2 lines of code per widget (depending on the programming language)."
And few applications does.

---

### Post by foerdi on 2007-12-15
Murrine + transparency hack:

[IMG]http://www.cimitan.com/blog/wp-content/murrine_rgba.png[/IMG]

OK, the hack stuff is alpha... But it looks tons better then clearlooks

[http://murrine.netsons.org/](http://murrine.netsons.org/)
[http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine)

---

### Post by Cimi86 on 2008-01-03
> **foerdi said:**
> Murrine + transparency hack:

OK, the hack stuff is alpha... But it looks tons better then clearlooks

[http://murrine.netsons.org/](http://murrine.netsons.org/)
[http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine)
...and it works ;)
:popcorn:

---

### Post by durand on 2008-05-30
It's in intrepid now! How exactly do you blur the transparency? It's kinda hard to read normal text when using it.

---

### Post by smartboyathome on 2008-05-30
It is? I didn't see it when I looked on packages.ubuntu.com, it uses the same version as Hardy. Also, I would think you would use the blur windows plugin when using Compiz. I think that made the transparent window borders blur. Be wary, though, as it can spike some CPUs to make it fairly unusable.

---

### Post by durand on 2008-05-30
Maybe it was updated in murrine? I don't have any extra repos related to this so it must have been updated in intrepid somehow...

I tried the blur plugin in compiz but its not changing the transparent gtk bits. Maybe that's separate?

---

### Post by smartboyathome on 2008-05-30
Did murrine update recently? Also, does everything become transparent, or just certain parts of the window? I am using the exact same engine now on hardy, and it doesn't do transparency as far as I can tell. What theme are you using, also?

---

### Post by durand on 2008-05-30
Yup, it did update murrine today.
> 2008-05-30 14:24:52 status installed gtk2-engines-murrine 0.53.1+svn20080529-0ubuntu1

And no, only patched apps become transparent. See [here]("http://www.cimitan.com/murrine/rgba-support/list")

The transparency is per gtk widget, not per window.

---

### Post by durand on 2008-05-30
Oh and I'm using The MurrinaOranche Theme: [http://www.cimitan.com/murrine/node/106](http://www.cimitan.com/murrine/node/106)
but it will work with all the official murrine themes, I think.

---

### Post by smartboyathome on 2008-05-30
Ok then, what server are you using in your repos list? Because it seems like a third party package to me (not even showing up on intrepid package search usually means that it isn't available in the official ubuntu.com repos). I think there may be a delay or something.

---

### Post by durand on 2008-05-30
Weird. Here's my repo list but I can't find anything related.

> durand@Carbon-14:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse

## Canonical Repostiory ##
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

# Screenlets
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) intrepid main universe


## Gnome Do
deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) hardy main

deb [http://erlug.linux.it/~da/deb/](http://erlug.linux.it/~da/deb/) ./
deb-src [http://erlug.linux.it/~da/deb/](http://erlug.linux.it/~da/deb/) ./

# Last.FM
deb [http://apt.last.fm/](http://apt.last.fm/) debian testing

# Inkscape

deb [http://ppa.launchpad.net/inkscape.testers/ubuntu](http://ppa.launchpad.net/inkscape.testers/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/inkscape.testers/ubuntu](http://ppa.launchpad.net/inkscape.testers/ubuntu) hardy main


# NM Applet
deb [http://ppa.launchpad.net/asac/ubuntu](http://ppa.launchpad.net/asac/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/asac/ubuntu](http://ppa.launchpad.net/asac/ubuntu) hardy main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse

# Teeworlds
deb [http://ppa.launchpad.net/jscinoz/ubuntu](http://ppa.launchpad.net/jscinoz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/jscinoz/ubuntu](http://ppa.launchpad.net/jscinoz/ubuntu) hardy main


---

### Post by Cimi86 on 2008-05-30
it's not time to test transparency, it is here just to help kenneth doing the intrepid theme.
Transparency will be disabled in intrepid

---

### Post by durand on 2008-05-30
Oh right, I don't usually use compositing but I noticed that the gtk theme changed. Thats the only reason why I saw this.

Cimi, do you know how to blur the transparency? I'm just curious now.
Thanks for your awesome engine!

---

### Post by smartboyathome on 2008-05-30
You are right, I just backported it for hardy and it seems there is a new version which is not yet showing up on packages.ubuntu.com.

---

### Post by durand on 2008-05-30
Possibly because Cimi doesn't want it to be noticed yet.

---

### Post by Cimi86 on 2008-05-30
please do not backport it or I will be forced to close the subversion repository

---

### Post by smartboyathome on 2008-05-30
It was only for my use (wasn't going to be distributed), and I am not currently using it anyway. I know it is still in development, and that it isn't stable at all. I was just seeing if it really was there.

---

### Post by Cimi86 on 2008-05-30
I have no time to support feedback of thousands of users that will come with: "why it is not working? how I can make it works?" etc etc etc.
I will work on this engine in july/august, and if it will be ready you'll see in intrepid, otherwise in ubuntu 9.04

---

### Post by smartboyathome on 2008-05-30
That is fine. I can wait until it is released. :)

---

