---
title: "Ambiance theme doesn't apply to all apps?"
date: 2012-06-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 67GTA on 2012-06-10
I normally don't install development versions. I just installed Beta 1 and updated. Several apps refuse to use the light themes, and look like windows 95. Firefox, chromium, synaptic, and any/all KDE apps so far. I have not tested all of them yet. Is this normal for the early iso's, or is this a bug?

---

### Post by scradock on 2012-06-10
Yes, I also like the light themes (Radiance rather than Ambiance) and also noticed that QQ was not using it yesterday. Firefox had odd icons, also. I'm sure it will be fixed in a while.

---

### Post by 67GTA on 2012-06-10
I actually meant radiance. I always get them mixed up. Just making sure it wasn't just me.

---

### Post by Merk42 on 2012-06-10
> **67GTA said:**
> I normally don't install development versions. I just installed Beta 1 and updated. Several apps refuse to use the light themes, and look like windows 95. Firefox, chromium, synaptic, and any/all KDE apps so far. I have not tested all of them yet. Is this normal for the early iso's, or is this a bug?Quantal right now is **Alpha** not **Beta**, so not uncommon to see breakage far beyond what you describe.

---

### Post by mc4man on 2012-06-10
radiance, which I don't use but obviously can check, seems about the same as it's been, ok except if using unity & lowering the panel opacity below 0.7000 or so. Apps like FF, synaptic, ect.  that still use gtk2 (gtkrc..) seem fine here.
(the color of the context menus may be slightly off, don't know having not used radiance often enough 

Maybe you are on Kubuntu?, some mention of KDE in 1st. post though you tagged this thread 'ubuntu'

---

### Post by balloons on 2012-06-11
> **67GTA said:**
> I normally don't install development versions. I just installed Beta 1 and updated. Several apps refuse to use the light themes, and look like windows 95. Firefox, chromium, synaptic, and any/all KDE apps so far. I have not tested all of them yet. Is this normal for the early iso's, or is this a bug?

Awesome! Thanks for helping out. Would you mind reporting your result on the iso tracker? 

[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds)

Find your build, and add your result to it. There's a wiki page with info on how to do it here -- you just need your ubuntu sso account. Feel free to ask questions!
[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

On your issue, this sounds like the bug I reported, which JUST got fixed.. Should show up in tomorrow's iso.

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1010675](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1010675)

Check and see if gnome-settings-daemon is running. My guess is it's not. Try running gnome-settings-daemon in a terminal window, and likely there's an error and it will close. The fix for that bug is in the archive, it might fix itself to just update. The fix for me was to remove my config settings (for gnome and gtk) and reset unity.

---

### Post by 67GTA on 2012-06-11
I'll check the updates tomorrow. I was getting an apport message about gnome-settings-daemon at boot. That is probably the culprit.

---

### Post by 67GTA on 2012-06-13
Still not fixed on my end. Running gnome-settings-daemon gives: "** (gnome-settings-daemon:5846): WARNING **: Name taken or bus went away - shutting down" The light-themes apply to the core Ubuntu apps and sub menus, but not any other apps.

---

### Post by paul_in_london on 2012-06-19
> **67GTA said:**
> Still not fixed on my end. Running gnome-settings-daemon gives: "** (gnome-settings-daemon:5846): WARNING **: Name taken or bus went away - shutting down" The light-themes apply to the core Ubuntu apps and sub menus, but not any other apps.

I'm using gnome classic at the moment and the theming was all messed up. I had selected Ambiance Dark or something quite a while ago from a gnome-shell session.

A work-around for me was to start **[COLOR="Red"]gnome-control-center[/COLOR]** from the terminal and then select **[COLOR="Red"]Ambiance[/COLOR]** - the default and only Ambiance theme available for selection in gnome classic.

Now everything is back to normal apart from the horrible white sub-menus in firefox etc. (and apart from ugly white lines on the sides and bottom of the active window on the bottom panel)! :)

EDIT: When I say "back to normal", I mean in terms of the theming at least.

---

### Post by mc4man on 2012-06-19
> **paul_in_london said:**
> I'm using gnome classic ...
Now everything is back to normal apart from the horrible white sub-menus in firefox etc. (and apart from ugly white lines on the sides and bottom of the active window on the bottom panel)! :)

EDIT: When I say "back to normal", I mean in terms of the theming at least.
If you mean sub menus like in screen then that's 'fixable', though ATM the new gtk 3.5.4 has messed up some things in light-themes so may be better fixed when stuff settles out
(firefox & some other apps, (gtk2),  are  adjusted thru the gtkrc  file

---

### Post by paul_in_london on 2012-06-24
> **mc4man said:**
> If you mean sub menus like in screen then that's 'fixable', though ATM the new gtk 3.5.4 has messed up some things in light-themes so may be better fixed when stuff settles out
(firefox & some other apps, (gtk2),  are  adjusted thru the gtkrc  file

You'll probably see what I mean from this screenshot.

---

### Post by mc4man on 2012-06-24
> **paul_in_london said:**
> You'll probably see what I mean from this screenshot.
I guess I'm looking at a browser in gnome Classic?, no global menu?
Anyway browsers still use gtk2 (gtkrc) for in window menus as do some other apps & window deco context menus

Here I don't use the default though do ck. it out, then switch to an ambiance I've keep going since 11.10, as things break or are changed (usually from gtk3), i edit to fix.

So here ATM all is quite fine except for one small issue I see in both mine & the current default

As far as your gtk2 menu color, I'll attach my current gtkrc, you can try if desired, if it improves great, if not then just put back the current one

To try - 
open /usr/share/themes/Ambiance/gtk-2.0 as root, rename the current gtkrc & paste in the new one. you may need to do a log out/in after

(you could otherwise search out an ambiance mod by StanAngeloff, if he hasn't adjusted for 12.10 then it would need a little help, it also addresses normal context menu color (gtk3

If curious this is the small issue I see with both the current LT & my mod, haven't found a way to fix other then reset after login with a gsettings command(s)
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014948](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014948)

---

### Post by paul_in_london on 2012-06-24
> **mc4man said:**
> I guess I'm looking at a browser in gnome Classic?, no global menu?
Anyway browsers still use gtk2 (gtkrc) for in window menus as do some other apps & window deco context menus

Here I don't use the default though do ck. it out, then switch to an ambiance I've keep going since 11.10, as things break or are changed (usually from gtk3), i edit to fix.

So here ATM all is quite fine except for one small issue I see in both mine & the current default

As far as your gtk2 menu color, I'll attach my current gtkrc, you can try if desired, if it improves great, if not then just put back the current one

To try - 
open /usr/share/themes/Ambiance/gtk-2.0 as root, rename the current gtkrc & paste in the new one. you may need to do a log out/in after

(you could otherwise search out an ambiance mod by StanAngeloff, if he hasn't adjusted for 12.10 then it would need a little help, it also addresses normal context menu color (gtk3

If curious this is the small issue I see with both the current LT & my mod, haven't found a way to fix other then reset after login with a gsettings command(s)
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014948](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014948)

Thanks **mc4man**. What I ended up doing (before I saw your post a second ago) was installing **[COLOR="Red"]ambiance-dark-gtk-theme[/COLOR]** from here (no quantal branch at the moment):

[https://launchpad.net/~kokoto-java/+archive/omgubuntu-stuff?field.series_filter=precise](https://launchpad.net/~kokoto-java/+archive/omgubuntu-stuff?field.series_filter=precise)

A little too dark maybe (see screenshot). :lolflag:

---

### Post by mc4man on 2012-06-24
Doesn't look that bad, seems to use black?

At least here for my current I use the same as ambiance - #3c3b37

Without seeing the theme fully (nautilus, ect.) I might be inclined to darken the selected_fg_color so it stands out a bit
(here I use a selected_fg_color:#3c3b37 to go with ambiance default, it looks better with the selected_bg_color:#D3B37D I use

So this may be interesting (or not

```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_fg_color:#000000"
```
To unset back to theme default
```
gsettings set org.gnome.desktop.interface gtk-color-scheme ""
```

There are likely a number of xsession-errors warning with that theme, not terribly important

---

### Post by paul_in_london on 2012-06-24
> **mc4man said:**
> Doesn't look that bad, seems to use black?

At least here for my current I use the same as ambiance - #3c3b37

Without seeing the theme fully (nautilus, ect.) I might be inclined to darken the selected_fg_color so it stands out a bit
(here I use a selected_fg_color:#3c3b37 to go with ambiance default, it looks better with the selected_bg_color:#D3B37D I use

So this may be interesting (or not

```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_fg_color:#000000"
```
To unset back to theme default
```
gsettings set org.gnome.desktop.interface gtk-color-scheme ""
```

There are likely a number of xsession-errors warning with that theme, not terribly important

Thanks again. Does it work for you? I get:

```
paul@quantal-64:~$ gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_fg_color:#000000"

** (process:3523): WARNING **: Could not connect: Connection refused

** (process:3523): WARNING **: Could not connect: Connection refused
paul@quantal-64:~$
```

Previously (after changing theme) I also wanted to reset my terminal background colour so I tried:

```
paul@quantal-64:~$ gconftool --type string --set /desktop/gnome/background/prima
ry_color "#2F0B24"

(gconftool:7160): GConf-WARNING **: Client failed to connect to the D-BUS daemon
:
Failed to connect to socket /tmp/dbus-6h5eo9VUQc: Connection refused
Error setting value: No D-BUS daemon running

paul@quantal-64:~$ 
```

---

### Post by VinDSL on 2012-06-24
> **paul_in_london said:**
> Thanks **mc4man**. What I ended up doing (before I saw your post a second ago) was installing **[COLOR="Red"]ambiance-dark-gtk-theme[/COLOR]** from here (no quantal branch at the moment):

[https://launchpad.net/~kokoto-java/+archive/omgubuntu-stuff?field.series_filter=precise](https://launchpad.net/~kokoto-java/+archive/omgubuntu-stuff?field.series_filter=precise)

A little too dark maybe (see screenshot). :lolflag:
That's hilarious!  What a small world!?!?!?!

I installed that theme, not more than 15 minutes ago.  Looks great in LXDE/Openbox!  

Guess I'll go take a look-see in Unity.  :)

---

### Post by paul_in_london on 2012-06-24
Actually after I installed the 3.5-rc4 kernel and rebooted I didn't get those errors any more.

---

### Post by VinDSL on 2012-06-24
> **paul_in_london said:**
> Actually after I installed the 3.5-rc4 kernel and rebooted I didn't get those errors any more.
Heh!

Downloading, as we "speak"...  :D

Thanks!

---

### Post by mc4man on 2012-06-24
> **paul_in_london said:**
> Actually after I installed the 3.5-rc4 kernel and rebooted I didn't get those errors any more.

Was going to post I tried your gconf command in a Classic session & no issue (though I guess if I wanted to change a terminal I'd likely do in profile preferences instead

As far as the gsettings command(s), they work fine

For the moment to 'fix' that small 'rendering' issue I see when I log in I run a reset combo, then my selected_fg is correct

Ie.  - 
```
gsettings set org.gnome.desktop.interface gtk-color-scheme "" && \
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#D3B37D;selected_fg_color:#3c3b37"
```

That key is also in dconf as in screen

Atm I'm sticking with compiz/unity/nautilus/ambiance though not sure if the future is rosy for mods

---

### Post by paul_in_london on 2012-06-24
> **mc4man said:**
> Was going to post I tried your gconf command in a Classic session & no issue (though I guess if I wanted to change a terminal I'd likely do in profile preferences instead

As far as the gsettings command(s), they work fine

For the moment to 'fix' that small 'rendering' issue I see when I log in I run a reset combo, then my selected_fg is correct

Ie.  - 
```
gsettings set org.gnome.desktop.interface gtk-color-scheme "" && \
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#D3B37D;selected_fg_color:#3c3b37"
```

That key is also in dconf as in screen

Atm I'm sticking with compiz/unity/nautilus/ambiance though not sure if the future is rosy for mods

EDIT: Got what I wanted after I edited the terminal profile via the GUI and unticked "Use colors from system theme". 

I know the terminal background colour code I want to use, but the GUI way isn't working for some reason (I've done it that way before without any problem) so that's why I tried the gconf command, but it didn't change anything.

Also tried this:

```
gconftool-2 -t string -s /apps/gnome-terminal/profiles/Default/background_color "#2F0B24"
```

but still no effect.

EDIT: Got what I wanted after I edited the terminal profile via the GUI and unticked "Use colors from system theme".

---

### Post by VinDSL on 2012-06-25
Hrm... I'm fully updated, and nothing has changed, for me.  If anything, it's gotten worse.

Under Unity, I cannot even download a file, because the menu wouldn't allow me to choose a download location, e.g folder.  It's stuck in /home/vindsl with a quivering pointer.  LoL!  :D

I'm using an alternate DE/WM in UbuQQ, for now, until this gets sorted.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-jun-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-jun-2012-1.png")[/INDENT]


Wake me up, when it's fixed...  ;)

---

### Post by paul_in_london on 2012-06-26
Found another theme I prefer - **[COLOR="Red"]salience[/COLOR]**.

```
sudo add-apt-repository ppa:salience-team/salience-devel-ppa
sudo aptitude update
sudo aptitude install salience-theme
```

---

