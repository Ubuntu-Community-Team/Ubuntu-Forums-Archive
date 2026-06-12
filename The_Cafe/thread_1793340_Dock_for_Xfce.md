---
title: "Dock for Xfce?"
date: 2011-06-29
forum: The Cafe
---

### Post by BrokenKingpin on 2011-06-29
I would like to use a dock in XFCE 4.8 (Xubuntu 11.04) and was wondering which dock out there would work the best?

I have tried DockBarX on the normal Xfce panel (through xfapplet), but it seems really buggy and fails to load half the time. So I am looking for an alternative.

What I am looking for in a dock that works somewhat like the Win7 Superbar as well as has applets that the standard panel has (applications menu, notification area, sys tray, clock, etc.).

---

### Post by 3Miro on 2011-06-29
Avant-Window-Navigator (AWN) should work fine.

---

### Post by ScionicSpectre on 2011-06-29
AWN is the only dock that has any ability to hold those kinds of applets, it seems. Since a lot is changing in the desktop landscape these days, relying on GNOME 2 applets is probably not a wise decision. It's best to look for a completely separate project like AWN, which also supports a notification area and a lot of interesting dock-specific applets. Your options for alternatives here are fairly limited.

---

### Post by Perfect Storm on 2011-06-29
If it's a simple lightweight dock, that also can simple things like weather etc. go for docky.

---

### Post by M7S on 2011-06-29
DockbarX still crashes freaquently with xfapplet? I hoped some changes in 0.44 would fix that. Also, DockbarX can run as a stand-alone dock now, command: dockx.

---

### Post by BrokenKingpin on 2011-06-29
Has anyone tried Cairo-Dock (glx-dock) lately? It seems to have a large applet selection and appears to be very configurable. It also doesn't require compositing, which is a plus. Would this be lighter than AWN?

---

### Post by NightwishFan on 2011-06-29
I vote for Docky. It is very easy to use.

---

### Post by beew on 2011-06-29
> **BrokenKingpin said:**
> Has anyone tried Cairo-Dock (glx-dock) lately? It seems to have a large applet selection and appears to be very configurable. It also doesn't require compositing, which is a plus. Would this be lighter than AWN?

Yes, I have a 10G test partition running Xubuntu 11.04 with Ubuntu themes,  but for some reason every time on reboot I am seeing two or three instances of the Cairo-dock instead of just one. 

I have checked that all save session options are turned off and I even removed the current session folder but it still doesn't kill the extra Cairo docks on start up. This appears to be a very old bug in Xfce and never got fixed.

I wonder if people have the same problem with AWN. If not the simple thing is just to uninstall the Cairo-dock and switch to AWN.

---

### Post by zer010 on 2011-06-29
The last time I installed AWN on Xubutnu, it brought in all kinds menus options from GNOME.  It was a massive jumble of Xfce and GNOME.  Now I just go with Xfce's stock panel.  I'd be interested to know if others had the same thing happen or if any other dock does that in Xfce.

---

### Post by Copper Bezel on 2011-06-29
It's somewhat Gnome-centric. The menus are all based on the Gnome menu, for instance, and the indicator applet includes the Gnome sound menu by default. With that said, I use XFCE's volume control and power manager and no main menu with AWN, personally, so I don't technically have any Gnome parts involved.

DockBarX is the best dock there is, and it'll run in AWN or as a standalone dock. The standalone can't be themed or set to auto-hide yet, however, and it doesn't include any other applets, so you still need something like AWN to hold indicators.

---

### Post by koleoptero on 2011-06-29
What happened to adeskbar anyway?

---

### Post by Bandit on 2011-06-29
> **Artificial Intelligence said:**
> If it's a simple lightweight dock, that also can simple things like weather etc. go for docky.

Yea Docky seems to be super stable at least for me.

---

### Post by nzjethro on 2011-06-29
> **BrokenKingpin said:**
> 
What I am looking for in a dock that works somewhat like the Win7 Superbar as well as has applets that the standard panel has (applications menu, notification area, sys tray, clock, etc.).

OP, you could check out using Talika through xfce4-xfapplet. Talika, I've found, is very similar to the Win7 bar, as it has icons of open windows, plus you can pin any commonly used applications to it. You can even group multiple windows, and show previews like in Aero. Plus, if you use Talika, as it is a gnome panel applet (hence why you need to use xfce4-xfapplet), you can add any other system monitors to the panel as well. Then, set the transparency and autohide as you like, and you've got a sexy-looking, and functional "dock".

[Talika]("http://gnome-look.org/content/show.php?content=118267")
[xfapplet]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin")

---

### Post by BrokenKingpin on 2011-06-30
nzjethro, Talika looks very cool. I really do like how it is just a standard applet. I will give this a try tonight.

---

### Post by M7S on 2011-06-30
BrokenKingpin, you never answered me (perhaps my question sounded rethoric?), was it DockBarX 0.44 you found buggy or an older version?

---

### Post by hhh on 2011-06-30
> **nzjethro said:**
> OP, you could check out using Talika through xfce4-xfapplet.
Seconded, I've been using it for about a year now...

[[img]http://s2.postimage.org/2ae5391gk/Screenshot_06302011_04_03_38_PM.jpg[/img]](http://s2.postimage.org/5u02t24cz/Screenshot_06302011_04_03_38_PM.png)

---

### Post by nzjethro on 2011-06-30
> nzjethro, Talika looks very cool. I really do like how it is just a standard applet. I will give this a try tonight.

> **hhh said:**
> Seconded, I've been using it for about a year now...


It is indeed very attractive. And hhh, it was seeing this (or a similar) screenshot in the June 2011 Screenshots forum that made me get Talika (and Xfce4 for that matter) in the first place, so perhaps I should have been seconding Talika as your idea! ;)

---

### Post by danbuter on 2011-06-30
I just messed around with the standard XFCE panel. It now works just like a regular dock. AWN, Docky, Cairo are all nice, but make you pull in almost all of gnome to use.

---

### Post by Copper Bezel on 2011-06-30
Again, this is simply not true. AWN requires gconf to be installed, but it's only individual applets that require Gnome daemons. DockBarX requires a couple of Gnome Python dependencies. I don't know Docky, but I imagine it's a similar situation.

---

### Post by Ctrl-Alt-F1 on 2011-06-30
I use docky with XFCE.  I've used AWN in the past.  They're both great so I won't advocate one over the other.

---

### Post by BrokenKingpin on 2011-07-01
> **M7S said:**
> BrokenKingpin, you never answered me (perhaps my question sounded rethoric?), was it DockBarX 0.44 you found buggy or an older version?
Yes, version 0.44. When it actually started it was fine, but 9 times out of 10 it would fail to start when first logging in... very annoying.

---

### Post by speedwell68 on 2011-07-01
I have just tailored the XFCE panel to work like a dock.  It works beautifully and is very ligt indeed.

---

### Post by danbuter on 2011-07-01
> **Copper Bezel said:**
> Again, this is simply not true. AWN requires gconf to be installed, but it's only individual applets that require Gnome daemons. DockBarX requires a couple of Gnome Python dependencies. I don't know Docky, but I imagine it's a similar situation.

Then why does it have have almost all of gnome marked as a dependency?

---

### Post by Bandit on 2011-07-01
> **danbuter said:**
> Then why does it have have almost all of gnome marked as a dependency?

Remember dependency's can be chain linked. 1 program may only need 3 deps, but those deps can require multiple deps as well. Unless its absolutely necessary, this over-linking can be annoying. Its for this reason packagers should pay really close attention on what they declare as required or optional in building packages.

---

### Post by 3Miro on 2011-07-01
> **danbuter said:**
> Then why does it have have almost all of gnome marked as a dependency?

I think it is because of the menu applet. You can have Gnome-menu as an applet on AWN, so it needs a lot of Gnome stuff. If you don't use that applet, you will only need to install the Gnome libraries, you will not have to load them in memory.

I may be wrong, the cause may be some other applet.

---

### Post by zer010 on 2011-07-01
It's because of all those dependencies and the double menus that I stopped using AWN in Xfce. It's good looking and has some nice applets, but on Xfce it's just too much redundancy.

---

### Post by BrokenKingpin on 2011-07-01
I have installed Talika and I am loving it. The only thing that is not working for me is the preview doesn't show the actual Window... is this because it needs compiz for the window preview and is maybe not compatible with the Xfce compositor?

---

### Post by hhh on 2011-07-01
It's looking the same for me using either Compiz or Xfce compositing (it's not a feature I use though, Xfce compositing shown)...

[[img]http://s2.postimage.org/2rz8ceqw4/Screenshot_07012011_07_37_57_PM.jpg[/img]](http://s2.postimage.org/6bl627tsj/Screenshot_07012011_07_37_57_PM.png)

---

### Post by BrokenKingpin on 2011-07-02
I am marking this as solved, Talika is awesome. Pretty much does what dockbarx does, only it is lighter and more stable.

---

### Post by Copper Bezel on 2011-07-03
Just as a note, the instability you were experiencing is DBX's interaction with xfapplet, not DBX itself. DBX standalone shouldn't have the same problems. But Talika's cool, too. = )

---

### Post by BrokenKingpin on 2011-07-03
> **Copper Bezel said:**
> Just as a note, the instability you were experiencing is DBX's interaction with xfapplet, not DBX itself. DBX standalone shouldn't have the same problems. But Talika's cool, too. = )
I have been using DBX for years in Gnome and has always loved it, so it is for sure the incompatibility with xfapplet. Oh well, Talika will fill the void for now lol.

---

### Post by 7Seas on 2011-07-08
> **BrokenKingpin said:**
> Has anyone tried Cairo-Dock (glx-dock) lately? It seems to have a large applet selection and appears to be very configurable. It also doesn't require compositing, which is a plus. Would this be lighter than AWN?

Hi BrokenKingpin - I've been using Cairo-Dock for about 2 months now and only had problems with the recent update.  It's been well behaved and actually very nice dock to work with.  I had some configuration issues at first but that turned out to be me, not Cairo.

My only issue right now is when I go into KDE instead of Gnome it's still there and cluttering up the KDE desktop.  Completely different problem.

All in all,  I plan to keep it, on the Gnome side anyway.  It saves many mouse clicks and is, for me, a clean and easy visual.

I recommend it.

---

### Post by yurx cherio on 2012-05-08
I know this is an old thread so this is an update one year later on the situation with 12.04. AWN still brings a ton of gnome libraries. I've read somewhere that adding debian test repository allows to install AWN without gnome dependencies.

Tried Docky but it was crashing quite often.

I have been using Cairo since. It seems to be stable enough (non-OpenGL version), it depends only on itself, has a lot of applets. The experience is slightly different from AWN but I guess I need to get used to it.

If I happen to use Unity/Gnome I would definitely go with AWN. I wish somebody recompiles it for XFCE without those crazy dependencies.

---

### Post by Version Dependency on 2012-05-08
> **yurx cherio said:**
> I know this is an old thread so this is an update one year later on the situation with 12.04. AWN still brings a ton of gnome libraries....

...I wish somebody recompiles it for XFCE without those crazy dependencies.


AWN is a dead project.  It hasn't been updated in ages so don't expect any bug fixes or new features in the immediate future.  GLX Dock (Cairo Dock) and Docky are both actively maintained for those looking for a replacement for AWN.

---

### Post by neu5eeCh on 2012-05-08
> **Version Dependency said:**
> AWN is a dead project.  It hasn't been updated in ages so don't expect any bug fixes or new features in the immediate future.  GLX Dock (Cairo Dock) and Docky are both actively maintained for those looking for a replacement for AWN.

I'm not so sure that AWN is dead. I notice that members of this forum were announcing the death of AWN in 2008. Two new versions of AWN were released in 2009 and one in 2010. Also, the [PPA for the AWN testing team]("https://launchpad.net/%7Eawn-testing/+archive/ppa") was just updated with packages this past month.

My read is that the AWN community is dead, dead, dead. (The devs probably lost interest in "the community" -- can't imagine how time consuming that must be.) They're not responding to bug reports or probably even being notified of them. However, the core developers/coders/hobbyists seem to be slowly contributing to 4.1, probably in their spare time.

---

### Post by cmcanulty on 2012-09-21
I know this is an old thread but can someone explain how to make the xfce panel act like a dock as mentioned above?

---

