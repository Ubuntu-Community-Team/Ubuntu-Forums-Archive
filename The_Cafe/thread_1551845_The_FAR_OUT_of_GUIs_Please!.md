---
title: "The FAR OUT of GUIs Please!"
date: 2010-08-12
forum: The Cafe
---

### Post by clgy15 on 2010-08-12
Hey guys,
I love linux to death and work with it all the time. My personal PC is getting alittle boring with Ubuntu KDE, GNOME, XFCE, LXDE..... So I want a new GUI thats totally cool. The coolest graphical display you have seen. I dont care if its really user friendly or not cause I have all the user friendly ones already.
PLEASE someone know of a really cool one!!

---

### Post by drawkcab on 2010-08-12
enlightment

[http://www.enlightenment.org/](http://www.enlightenment.org/)

---

### Post by clgy15 on 2010-08-12
I tried Enlightenment but I can never get it to configure... Is there like a guide or something to it?

---

### Post by drawkcab on 2010-08-12
I think there are versions of Ubuntu that feature enlightenment.  Oh, wait, here's one that has enlightment with Debian:

[http://www.elivecd.org/](http://www.elivecd.org/)

It's a start!

---

### Post by clgy15 on 2010-08-12
OOOOHHHHHHH!!!!!!!! Im trying that now!!!!!

---

### Post by ubunterooster on 2010-08-12
See: igelle's Esther DE: [http://news.softpedia.com/news/Igelle-DSV-1-0-0-Introduces-the-Esther-Desktop-135761.shtml](http://news.softpedia.com/news/Igelle-DSV-1-0-0-Introduces-the-Esther-Desktop-135761.shtml)

---

### Post by drawkcab on 2010-08-13
^^  looks like gnome

---

### Post by Nick_Jinn on 2010-08-13
You have to pay for Elive.

Try OpenGEU. Its a combination of Gnome and Enlightenment. MoonOS is another good one, but the default artwork is a little girly. That is easily changed. There are some awesome themes for E17,

---

### Post by ubunterooster on 2010-08-13
@drawkcab: It certainly doesn't *feel* like gnome.

---

### Post by Madspyman on 2010-08-13
I like Openbox recently, but it's probably to minimal for your tastes. I used Gnome Shell in Karmic up until I upgraded to Lucid and it stopped working, also Gnome Shell needs to lose the panel.

Openbox an Gnome Shell should combine to form Open Shell.

---

### Post by drawkcab on 2010-08-13
Yeah, openbox is fun to play around with.

---

### Post by kerry_s on 2010-08-13
just pick something & start working on it to make it unique to you.
you can google, see if it's been done.

i been playing with netbook remix + tint2, currently i just figured out how to add launchers & things to tint2, so i been messing with that. made me some volume icons with sub menus & a show desktop toggle. now i'm just listening to some music taking a break, thinking about what i want to mess with next. :D

---

### Post by rotwang888 on 2010-08-13
[Fluffy Linux.](http://apachelog.wordpress.com/2010/06/04/fluffy/)

---

### Post by Helkaluin on 2010-08-13
> **rotwang888 said:**
> [Fluffy Linux.]("http://apachelog.wordpress.com/2010/06/04/fluffy/")
My eyes.

---

### Post by Spice Weasel on 2010-08-13
[Awesome]("http://awesome.naquadah.org/"), it's a tiling window manager. Very different from the common desktop, and fun to mess with. :D

---

### Post by murderslastcrow on 2010-08-13
KDE 4 and E17 are about as far out as you can ask for. Also, Gnome is endlessly customizable- you can see how, with screenlets, docks, applets, and all kinds of themes, they've found plenty of new ways to interact with your desktop. Gnome-DO, even.

But yeah, E17 is beautifully concisely coded, and beautifully optimized for what it can do (WITHOUT COMPOSITING!!). So really, I think e17 is a jewel in desktop computing. The fact that you can get it to work with compiz now is just incredible.

When it's stable, I might have no choice but to use it fulltime. XD I mean, it's just so easy to play around with, and so interesting, and well... Bling bling, seriously.

---

### Post by aeiah on 2010-08-13
> **Spice Weasel said:**
> [Awesome]("http://awesome.naquadah.org/"), it's a tiling window manager. Very different from the common desktop, and fun to mess with. :D

yeh, awesome is pretty good. a lot of people say xmonad is better but awesome gives you a whole desktop environment (well, it gives you a panel, menu, taskbar, widgets) wheras xmonad just gives you tiling functionality.

ive been craving awesome on my work pc in the office due to the speed of setting up multiple windows etc. its also very lightweight, moreso than openbox etc

---

### Post by slackthumbz on 2010-08-13
define 'far out', I <3 my custom gnome desktop and I find it pretty far out.

---

### Post by Zorgoth on 2010-08-13
I customize GNOME by

a) setting up awesome compiz animations.  I use vacuum for open normal, curved fold for close normal, burn for menus (open and close), horizontal folds for open tooltip, leaf spread for close tooltip, and for a few special windows like GnoMenu, guake, and gnome-do I use zoom from center for both open and close).

I also use shift switcher for Alt-Tab, a moderately customized rotate cube, and a pretty cool emerald theme (I think I use glassbuntu basically).  Ring switcher is also cool, but I don't like how it looks when you have just two or three windows, and of course Window Previews and Wobbly Windows.

Compiz also has a lot of very good productivity features that integrate well with cairo-dock.  I just love expo, scale, and grid.  I also actually find cube a pretty intuitive way to handle workspaces.  Window Previews and Grid are very improved with compiz 0.9 (which is still quite unstable), with options in Workarounds for minimized previews and the ability to restore window size in Grid.

You can also use opacity, brightness, and saturation to make windows partially transparent (warning, not too transparent, because it makes text transparent too!); e.g. I make my GnoMenu 14% transparent.

b) disabling the gnome-panel (you can do that with gconf-editor)

c) getting cairo-dock and configuring it to be superflashy, with on dock on the bottom and essential desklets like clock, systray, GnoMenu in the upper left - also  you need gnome-do to replace Alt-F2 (Alt-F2 is part gnome-panel)

d) (and this is the best part), you can make a transparent terminator (a cool terminal emulator) essentially part of your desktop background because it has a command line switch that allows you to set its window role, so you just have a startup application 
"terminator --role=Background --layout=mylayout"
and in ccsm you set role=Background to:

Skip Taskbar, Skip Pager, Below, Sticky, Non Movable, Non Resizable, Non Minimizable, Non Maximizable, and Non Closable in Window Rules, as well as a fixed size

In Window Decorations turn off Window Decoration for role=Background

In Place Windows set it to appear where you want it.

On my 1920x1080 laptop screen I have a 500x1080 terminal at 1420x1080.

Sometime when I have everything working perfectly I'm going to post a script to install my full theme somewhere.

---

### Post by drawkcab on 2010-08-13
> **kerry_s said:**
> just pick something & start working on it to make it unique to you.
you can google, see if it's been done.

i been playing with netbook remix + tint2, currently i just figured out how to add launchers & things to tint2, so i been messing with that. made me some volume icons with sub menus & a show desktop toggle. now i'm just listening to some music taking a break, thinking about what i want to mess with next. :D

I kind of like this idea.  My HTPC is ubuntu-powered and I've been tossing around the idea of replacing the gnome menus with UNE launcher somehow.  I have to think I can install the UNE packages and then somehow get UNE launcher working on start up.

---

### Post by RATM_Owns on 2010-08-14
Dwm.  That is all.

---

### Post by mips on 2010-08-14
Window Maker

---

### Post by Spice Weasel on 2010-08-14
> **mips said:**
> Window Maker

Now that's far out. :)

And oldschool.

---

