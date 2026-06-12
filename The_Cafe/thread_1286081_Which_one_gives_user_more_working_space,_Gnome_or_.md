---
title: "Which one gives user more working space, Gnome or KDE?"
date: 2009-10-08
forum: The Cafe
---

### Post by legolas_w on 2009-10-08
Hi
I am wondering with a 14.1" laptop which one of Gnomeor KDE gives a more clear workspace with more space for users.

I never tried KDE 4.X to a degree that I could compare it with Gnome so, I can not come to a conclusion by myself and so I asked the question here.

Thanks.

---

### Post by Dougie187 on 2009-10-08
Personally I don't care for KDE, but I would not think that either of them would make your working space larger than the other one. I mean, with both of them you could get rid of your un-needed panels and auto-hide the needed ones to make your real estate larger, but they won't determine your resolution thus determining your overall desktop space.

---

### Post by NoaHall on 2009-10-08
I'd say gnome.

---

### Post by RiceMonster on 2009-10-08
You can drastically change the layout of both of them to give you more "working space" (though I'm not sure what that means). Try them both and use whichever you're more comfortable with.

---

### Post by Bachstelze on 2009-10-08
Changing DEs won't give you more working space. Changing monitors will.

Yes, I know you're on a laptop. The point is, DEs only make a marginal difference, the monitor size, thus the actual space available, will always be the same.

---

### Post by OpenGuard on 2009-10-08
Tiling WM's ( Awesome, Wmii, Xmonad, ... ) will always let you use more space, without thinking about how to align 3 terminal windows, file manager, music player and probably, even vim.

---

### Post by Grimhound on 2009-10-08
To be entirely honest I'd have to say Xfce would be the best bet for saving space. Gnome second. KDE third.

---

### Post by Skripka on 2009-10-08
> **Grimhound said:**
> To be entirely honest I'd have to say Xfce would be the best bet for saving space. Gnome second. KDE third.

Blah.  You're talking about things that can basically be customized however you want.  Have a premium on vertical space?  Put toolbars on the sides.

---

### Post by Tibuda on 2009-10-08
If you want space you should use a standalone WM instead of a DE. I don't know about KDE, but it is impossible to get rid of gnome-panel.

---

### Post by OpenGuard on 2009-10-08
> **danielrmt said:**
> If you want space you should use a standalone WM instead of a DE. I don't know about KDE, but it is impossible to get rid of gnome-panel.

Since when ? All you need to do is to remove it from required components list in gconf-editor.

---

### Post by RichardLinx on 2009-10-08
> **danielrmt said:**
> it is impossible to get rid of gnome-panel.
No it's not.

---

### Post by spupy on 2009-10-08
Run Fluxbox with Gnome stuff. Fluxbox, although not as good-looking as Metacity, saves space - for example, you can remove decorations on windows where you don't need it.

---

### Post by Xbehave on 2009-10-08
While both can be customised there are a few reasons why kde wins hands down:
[LIST]
[*]Hide any menubar
[*]the BII window decoration is pretty small
[*]toggling window decoration (edit: may be doable with gnome)
[/LIST]
I'm sure you can customise gnome too but I have an always visible panel (systemtray, system monitor, clock) yet still get 98% vertical screens (and 100% horizontal) dedicated to the active app (which itself gets more content space because I can hide the menubar)

---

### Post by mikewhatever on 2009-10-08
You can hide the panels in both Gnome and KDE, as well as customize window borders. I think what really matters, and does give more working space is the size of the screen.

---

### Post by spupy on 2009-10-08
> **Xbehave said:**
> While both can be customised there are a few reasons why kde wins hands down:
[LIST]
[*]Hide any menubar
[*]the BII window decoration is pretty small
[*]toggling window decoration (edit: may be doable with gnome)
[/LIST]
I'm sure you can customise gnome too but I have an always visible panel (systemtray, system monitor, clock) yet still get 98% vertical screens (and 100% horizontal) dedicated to the active app (which itself gets more content space **because I can hide the menubar**)

How can you do that? Please tell me.

---

### Post by Dimitriid on 2009-10-08
Its not about screen real-state since as mentioned, that is dependent entirely on screen resolution ( which in turn depends entirely on monitor size ).

You outta be looking for which DE is the more efficient to manage and organize your tasks within the screen real-state you are currently stuck with.. In which case I'd go for Gnome + Compiz right now.

---

### Post by Bodsda on 2009-10-08
> **danielrmt said:**
> If you want space you should use a standalone WM instead of a DE. I don't know about KDE, but it is impossible to get rid of gnome-panel.

Hmm, I best let apt know that it cant do a ```
sudo apt-get remove gnome-panel
``` then

---

### Post by Xbehave on 2009-10-08
> **spupy said:**
> How can you do that? Please tell me.
for any native kde program ctrl+m 

3 notes:
It doesn't work in amarok because they ruined it (to avoid confusing gnome users)
It doesn't work well in kontact (don't know why)
It is tricky to work in konsole (use menus instead as ctrl+m can be used by programs in the shell)

In the image I've used personalmenu2 for firefox.

---

### Post by Firestem4 on 2009-10-08
> **Bachstelze said:**
> Changing DEs won't give you more working space. Changing monitors will.

Yes, I know you're on a laptop. The point is, DEs only make a marginal difference, the monitor size, thus the actual space available, will always be the same.

While physical size does not change, KDE's new Plasma Netbook interface ads an extra bit of usable real-estate by acting as a scrollable desktop. Conceptually its neat, and I saw a good demo of it by Aseigo.

---

### Post by OpenGuard on 2009-10-08
> **Bodsda said:**
> Hmm, I best let apt know that it cant do a ```
sudo apt-get remove gnome-panel
``` then

Which will obviously remove a bunch of dependencies, leaving you on something I can't call Gnome.

---

### Post by Bodsda on 2009-10-08
> **OpenGuard said:**
> Which will obviously remove a bunch of dependencies, leaving you on something I can't call Gnome.

Yeah obviously... as if I cant live without the applications that are run on top of gnome-panel

```

bod@bod-ubuntu:~$ sudo apt-get remove gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-applets gnome-panel indicator-applet indicator-messages
0 upgraded, 0 newly installed, 4 to remove and 39 not upgraded.
After this operation, 2462kB disk space will be freed.
Do you want to continue [Y/n]? 


```

---

### Post by blur xc on 2009-10-08
> **OpenGuard said:**
> Tiling WM's ( Awesome, Wmii, Xmonad, ... ) will always let you use more space, without thinking about how to align 3 terminal windows, file manager, music player and probably, even vim.

Though not as efficient as a true tiling wm, the maximumize plugin for compiz is great for 'tiling' of windows...  And there's a compiz hotkey button (haven't found it myself yet) that lets you turn of window decorations.

Add gnome-global menu applet (though doesn't work w/ all apps, ie. ff, oo, etc...) and that'a good start for a system that looks trick.

BM

---

### Post by madjr on 2009-10-08
dude what you need is a compact firefox theme like stratini and my menu to hide the menu

---

### Post by Xbehave on 2009-10-08
> **madjr said:**
> dude what you need is a compact firefox theme like stratini and my menu to hide the menu
That helps firefox, but what about all the other gnome apps? KDE ftw :P

p.s
[fission]("http://mozilla.zeniko.ch/fission.html")
[personal menu]("https://addons.mozilla.org/en-US/firefox/addon/3895/")
and a modified userchrome and you can be cool like me (or just get a minimal firefox)

---

### Post by NinjaNumberNine on 2009-10-08
Gnome, but I use KDE anyway! :lolflag:

---

### Post by mamamia88 on 2009-10-08
i use gnome 1 panel at the top reduced to as few pixels as it would let me.  i think that gives me the most screen real estate does that answer your question?

---

### Post by Warpnow on 2009-10-08
XFCE has alot more minimalistic window decorations than gnome, but both can save space.

XFCE setup with a bottom panel for normal screen, or on the side for a widescreen, and running maximus so that maximized applications don't have window decorations.

sudo apt-get install maximus

Alternatively, you can save ALOT of space by using gnome-do docky instead of the panel, with maximus.

---

### Post by Tibuda on 2009-10-08
> **OpenGuard said:**
> Since when ? All you need to do is to remove it from required components list in gconf-editor.

I stand corrected. I admit I have not tried more than "killall gnome-panel", which just restart the panel.

---

### Post by Boom!!! on 2009-10-08
KDE is a dream, Gnome by default has 2 panels so takes up more space on the screen and gives you less space.

---

### Post by xpod on 2009-10-08
> **Boom!!! said:**
> KDE is a dream, Gnome by default has 2 panels so takes up more space on the screen and gives you less space.

Does that mean that right clicking a panel and selecting "delete this panel" in Gnome is a complete nightmare?

---

### Post by Dimitriid on 2009-10-08
> **Boom!!! said:**
> KDE is a dream, Gnome by default has 2 panels so takes up more space on the screen and gives you less space.

If we are talking defaults KDE taskbar is thick, huge and ugly.

---

### Post by Boom!!! on 2009-10-08
> **xpod said:**
> Does that mean that right clicking a panel and selecting "delete this panel" in Gnome is a complete nightmare?


Well, that's another question. I could come back and ask "Is setting kde panel to autohide so difficult"

---

### Post by Boom!!! on 2009-10-08
> **Dimitriid said:**
> If we are talking defaults KDE taskbar is thick, huge and ugly.


Was that the original question, no. go back and check it.

---

### Post by eeperson on 2009-10-08
> **Firestem4 said:**
> While physical size does not change, KDE's new Plasma Netbook interface ads an extra bit of usable real-estate by acting as a scrollable desktop. Conceptually its neat, and I saw a good demo of it by Aseigo.

You can actually add a scrollable desktop (by which I mean a desktop that is bigger than your monitors resolution) to any window manager.  This is actually a feature of X.  You can configure it in xorg.conf.

However, this is the first time I have heard of it used as part of a default configuration for a DE.  I am intrigued.

---

### Post by Xbehave on 2009-10-08
> **eeperson said:**
> You can actually add a scrollable desktop (by which I mean a desktop that is bigger than your monitors resolution) to any window manager.  This is actually a feature of X.  You can configure it in xorg.conf.

However, this is the first time I have heard of it used as part of a default configuration for a DE.  I am intrigued.
+1 i would appreciate a link
I suspect the kde trick does something clever with panels aswell or this is a very lame "feature"

---

### Post by eeperson on 2009-10-08
The way I have done it in the past is by adding the following line to the Display sub section of my xorg.conf:
```
Virtual 1024 768
``` 
The numbers are the x and y dimensions for the desktop space you have to scroll around on.

I couldn't find a link with directions on how to do this.  [Here]("http://ubuntuforums.org/showthread.php?t=816825") is link to a post someone did where they accidentally stumbled on this feature.  It might make things more clear.

You can also find more info in the xorg.conf man page.

---

### Post by Xbehave on 2009-10-08
> **eeperson said:**
> The way I have done it in the past is by adding the following line to the Display sub section of my xorg.conf:
```
Virtual 1024 768
``` 
The numbers are the x and y dimensions for the desktop space you have to scroll around on.

I couldn't find a link with directions on how to do this.  [Here]("http://ubuntuforums.org/showthread.php?t=816825") is link to a post someone did where they accidentally stumbled on this feature.  It might make things more clear.

You can also find more info in the xorg.conf man page.
Yeah i've stumbled/used that feature before i was wondering what th poster talking about it in regards to KDE was on about. Just out of interest any idea how you would get that effect on an xorg.conf less setup, would you need to modify hal or can it be achived with xrandr or would you just add xorg.conf again as it seams like the best place to put it?

---

### Post by praveesh on 2009-10-08
Same if the auto hiding of the panels are enabled. Otherwise, kde. But,in your case, kde 4.3 may be the best choice with auto hide enabled.

---

### Post by praveesh on 2009-10-08
Kde won't mess(atleast by default) your desktop with mounted harddisks and others

---

### Post by praveesh on 2009-10-08
> **Dimitriid said:**
> If we are talking defaults KDE taskbar is thick, huge and ugly.

no . From kde 4.3 onwards, the default panel is not thick , huge and ugly

---

### Post by praveesh on 2009-10-08
> **Boom!!! said:**
> Well, that's another question. I could come back and ask "Is setting kde panel to autohide so difficult"

no. Click on a cashew on the panel. Then click on advanced settings . Then on auto hide panel .

---

### Post by eeperson on 2009-10-09
> **Xbehave said:**
> Yeah i've stumbled/used that feature before i was wondering what th poster talking about it in regards to KDE was on about. Just out of interest any idea how you would get that effect on an xorg.conf less setup, would you need to modify hal or can it be achived with xrandr or would you just add xorg.conf again as it seams like the best place to put it?

I just checked out the xrandr man page and it looks like you can set this up using the --panning flag.  Xrandr also appears to give you more options.

---

### Post by Screwdriver0815 on 2009-10-09
I have checked it on the Laptop too. And my result is: Gnome gives more space. Because you have more space in the lower panel for the open windows.
So looking for an open window on the lower panel and starting the apps on the upper panel avoids confusion.

another reason is ****ing KNetworkmanager is not capable to connect via WLAN in my particular case and I don't want to fiddle around :lolflag:

but anyway: you also can add a second or third or fourth panel to KDE :D

---

### Post by Xbehave on 2009-10-09
> **Screwdriver0815 said:**
> another reason is ****ing KNetworkmanager is not capable to connect via WLAN in my particular case and I don't want to fiddle around :lolflag
That is a terrible reason, yes KNetworkmanager is pretty broken (hey its largely a gnome project) but its much easier to just run nm-applet under kde than switch DE (this is fedora's solution to the problem and it works well).

For all the pro-gnome arguments It seams gnome lacks
[LIST]
[*]Non full width window decorations (ala BII)
[*]Non full width panels
[*]On-top panels (e.g but it on top an unused corner or a window/window decoration)
[/LIST]

Short of going all out and having a setup like mine the best way to maximise screenspace is to:
*auto-hide all panels (downside is that you don't get a permanent clock or system tray/other widgets to watch the system state)
*a single vertical panel (downside to this is that your taskbar may be hard to use, something like stasks deals with it well) [is this doable in gnome?]

---

### Post by Tibuda on 2009-10-09
> **Xbehave said:**
> *auto-hide all panels (downside is that you don't get a permanent clock or system tray/other widgets to watch the system state)conky and stalonetray can fix this downside.

---

### Post by RiceMonster on 2009-10-09
> **Xbehave said:**
> That is a terrible reason, yes KNetworkmanager is pretty broken (hey its largely a gnome project) but its much easier to just run nm-applet under kde than switch DE (this is fedora's solution to the problem and it works well).

I use wicd in kde. It's gtk, but it works very well (I prefer it to netwprk manager) and is pretty DE independent.

---

