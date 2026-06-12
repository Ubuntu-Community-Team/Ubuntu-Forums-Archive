---
title: "(preliminary)SUCCESS:  Fluxbox in Gnome"
date: 2005-09-08
forum: The Cafe
---

### Post by Brunellus on 2005-09-08
Earlier, I asked whether it would be possible to run [Fluxbox]("http://www.fluxbox.org") as Gnome's default windowmanager instead of metacity. 

I am pleased to report that this is possible.  Consider this a draft howto, as I am busy trying to tweak things.

I am indebted to poofyhairguy's "enlightened gnome" howto, as well as Stormy Eyes' excellent advice on running Openbox within Gnome

**STEP ONE: Installing Fluxbox**

This is the easy part.  Fluxbox is in universe;  enable universe, fire up your terminal, and ```
$ sudo apt-get install fluxbox
``` that sucker.

You can restart the Xsession here, if you like.  When GDM comes up, you'll see Fluxbox added to your "Sessions" menu.

However, I would NOT restart the Xsession at this point.  Fire up your terminal and ```
$ sudo /usr/share/xsessions/fluxbox.desktop
```

where you see ```
exec=fluxbox
``` replace that line with ```
exec=startfluxbox
```

If you do this, Fluxbox will, on its first execution, generate a configuration file:

~/.fluxbox/startup

For a more complete discussion of what the startup file does in Fluxbox, please see [This page in the Gentoo Wiki]("http://gentoo-wiki.com/HOWTO_Fluxbox#Startup_Applications")

Log into fluxbox, and confirm that it does, indeed work.  We are now ready for 

**STEP TWO:  Cramming Fluxbox into Gnome**

This next section is essentially ripped off of poofyhairguy's excellent, and recently slashdotted, Enlightened Gnome Howto.

First,  execute the following in a regular terminal: ```
$ sudo cp /usr/share/gnome/default.session ~/.gnome2/session
```

Then, edit that session file: ```
 sudo gedit ~/.gnome2/session
```

Find this line: ```
 1,RestartCommand=gnome-wm --sm-client-id default1
``` and change it to this: ```
 1,RestartCommand=gnome-wm --default-wm fluxbox --sm-client-id default1
```

Save the file, restart your Xsession (CTRL+ALT+BKSPACE), and log back into gnome. 

This will take a while.  You will see fluxbox first, then the gnome-panel, and finally the desktop will appear and draw over all the fluxbox desktop.

**Fluxbox in Gnome: First impressions**

Fluxbox is a very lightweight windowmanager.  Not for nothing is it the wm of choice of  [DamnSmallLinux]("http://www.damnsmalllinux.org") From what I can tell, it takes up VERY little RAM.

It also draws and redraws faster than metacity, at least on my equipment--AMD k7, 512 MB RAM, nvidia geforce 5200 128mb VRAM-- and much neater as well.

Here's a neat trick that Fluxbox does:  open two windows.  Now middle-click drag one onto another.  The two windows are now docked together:  clicking on the titlebar will switch between windows.  In this way, you can tab through any number of windows.  This is particularly nice if you run stuff from terminals--that way, you can have the app in one window, then click the window itself and get the debug output.

Things I've got to figure out:

The nautilus desktop draws over fluxbox.  Thus, no flux taskbar and no slit (the flux name for the dock).

Also, I can't get flux's right-click menu.  Middle-click works.

Comments are ALWAYS welcome.  A huge shout and thanks to the whole Ubuntu community--y'all rock, hard.

And of course, a [screenshot]("http://static.flickr.com/27/41568346_aa996d0e15_o.png") of my desktop.  The wm is fluxbox, and an assload of gdesklets running.

---

### Post by weekend warrior on 2005-09-09
What are the differences between this and using Openbox? Not a flippant question btw; just genuinely curious as Openbox is much easier to integrate and would seem to accomplish the same. Is there any advantage to Flux?

---

### Post by az on 2005-09-09
Is fluxbox fixed in breezy?  If not, report this to the MOTU (Masters of the Universe) so that they fix the package before relase.

---

### Post by Brunellus on 2005-09-09
[QUOTE=weekend warrior]What are the differences between this and using Openbox? Not a flippant question btw; just genuinely curious as Openbox is much easier to integrate and would seem to accomplish the same. Is there any advantage to Flux?[/QUOTE]
 My main reason for wanting Fluxbox over Openbox is Fluxbox's neat window-tabbing trick.  It also seems lighter, memorywise, than Openbox, but I have not tested this rigorously.

Also, I have more experience with Fluxbox, having used it under DSL and on my old ubuntu box (a coppermine celeron and 256mb RAM--you run out of RAM fast if you're doing photo-editing work with that setup!)

I compared the two last night.   Openbox plays more nicely with gnome, but Fluxbox is better by itself.  It's a very sleek, somewhat stark environment...but it can be made to look pretty stylish. 

Azz, I'm still running hoary.  If someone running Breezy would please apt-get fluxbox and then post the contents of /usr/share/xsessions/fluxbox.desktop I would be interested.  It's a simple fix...

Come to think of it, I think I'm going to write a more general Fluxbox howto.

---

### Post by bigzak on 2005-09-09
[QUOTE=Brunellus]My main reason for wanting Fluxbox over Openbox is Fluxbox's neat window-tabbing trick.  It also seems lighter, memorywise, than Openbox, but I have not tested this rigorously.[/QUOTE]

I have generally found fluxbox lighter, quicker and much, much more stable than openbox. Also, the menu format is completely horrible, and takes a whole bunch of typing where fluxbox would need perhaps 4 words...

A quick correction to the article (excellent as it is); the slit is not the fluxbox word for the dock. Fluxbox has a dock that is normally hidden until you dock something to it. The slit contains the desktop switcher, systray, taskbar and clock.

---

### Post by Knome_fan on 2005-09-09
Hm, I'm currently usin xfwm4 with gnome and getting it to run was very easy, so I don't see why getting fluxbox to run should be any harder:
1. Open a terminal
2. gnome-session-remove metacity -> metacity is gone for good
3. Start your wm (in my case: nohup xfwm4 &)
4. gnome-session-save
5. Profit! :-D

---

