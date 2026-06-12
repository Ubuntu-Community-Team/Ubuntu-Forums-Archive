---
title: "In love with Xubuntu"
date: 2005-11-26
forum: The Cafe
---

### Post by sapo on 2005-11-26
First of all, i want all the informations about the Xubuntu project that you can give me, website, where are the forums about it, and more info, man.. i m in love with it.

I will install Ubuntu in a 400mhz pc this monday, finally convinced my boss that i would work better if i was in linux.

So i read about Xubuntu and decided to try it out at my home pc (A64 2800+, 512MB RAM).

And now i m in love with it, good bye Ubuntu (Gnome), welcome Xubuntu (xfce).

My first impressions couldnt be better.

1 - I really loved the blue boot up screen.
2 - It flies man.. i cant believe how fast my computer is running
3 - I though it was kinda of a "ripped" desktop without anything, but i was wrong, i has almost everything i had in gnome.
4 - I love being able to drag my windows to another desktop and go to another desktop draging the mouse to the edge of the screen.
5 - The control panel rules, its perfect, in the screenshot below you can see it, it changed my resolution without restarting X, and its very easy and intuitive to use.

But i disliked some stuffs, o here are my questions

1 - How can i make the main panel fill all the screen width?
2 - Is there a way to make rox delete with DEL and not CTRL + X? Is there any Tree views or sidebars on it? Can it generate video thumbnails?
3 - Is there some kind of way to have a desktop? or maybe a right click feature on the wallpaper?

And i really wanna know more about the project, but the main question in this thread is:

Is there any plans for a Xubuntu CD, that will install Xubuntu, and JUST Xubuntu, of course with all the ubuntu apps and features.

Here a screenshot:
[[IMG]http://img358.imageshack.us/img358/5476/xubuntu18ys.th.jpg[/IMG]](http://img358.imageshack.us/my.php?image=xubuntu18ys.jpg)

And for those who want to install it:

```

sudo apt-get install xubuntu-desktop

```

Install it, you are not going to regret it :)

---

### Post by kairu0 on 2005-11-26
[QUOTE=sapo]
1 - How can i make the main panel fill all the screen width?[/QUOTE]

If I remember correctly, you can't maximize the panel but you can maximize the taskbar. So, I added the taskbar to my main panel and then made the taskbar expand to fill the bottom of the screen. (aka windows-style)

---

### Post by majikstreet on 2005-11-26
[QUOTE=sapo]
2 - Is there a way to make rox delete with DEL and not CTRL + X? [/QUOTE]
That'd be interesting to know. When I used Xfce I used ROX and in the beginning of fluxbox I used it.. Now it's pretty much all command line for me...

---

### Post by sapo on 2005-11-26
[QUOTE=majikstreet]That'd be interesting to know. When I used Xfce I used ROX and in the beginning of fluxbox I used it.. Now it's pretty much all command line for me...[/QUOTE]
The 3 things i miss in rox:

1 - Tree view
2 - Video thubnails
3 - Move Files

But that thing is fast O_O

---

### Post by qalimas on 2005-11-26
I love Xfce, really I do, I'd use it, if only I could get it to make windows flash like in GNOME and KDE.  I'd adore you for life if you could tell me how to do that XD

---

### Post by Luggy on 2005-11-26
I used to ues Xfce back in the day when I ran Gentoo.
Those slim window managers like xfce and openbox never really did it for me, I always felt less user friendly to me.

---

### Post by ranf on 2005-11-26
[QUOTE=sapo]First of all, i want all the informations about the Xubuntu project that you can give me, website, where are the forums about it, and more info, man.. i m in love with it.
[/QUOTE]
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=sapo]
4 - I love being able to drag my windows to another desktop and go to another desktop draging the mouse to the edge of the screen.[/QUOTE]

The program called brightside lets you do that in Gnome.

---

### Post by psychicdragon on 2005-11-27
You can use the Del key in rox with a little bit of tweaking.

Add this line to the file .gtkrc-2.0 in your home directory. Or create it if it does not exist.
```
gtk-can-change-accels = 1
```
Close any Rox windows. Then open Rox again and hover the mouse over the Delete command in the context menu. Press the Del key and the accelerator will disappear. Press Del again and 'Delete' will show up as the new accelerator. You can repeat this process to change any of the shortcuts.

There is a way to get thumbnails for video files but I haven't ever tried to install it myself. Here's the URL though: [http://www.kerofin.demon.co.uk/rox/VideoThumbnail.html](http://www.kerofin.demon.co.uk/rox/VideoThumbnail.html)

Totally Off-Topic edit:
Sapo, what group has done subs for One Piece up to episode 206!?

---

### Post by blair on 2005-11-29
I'd like to experiment with xfce on Ubuntu, but I'm afraid I'd break my system. Questions:

1. What happens to system when you run install xubuntu-desktop? Does the system automatically switch from Gnome to Xfce?

2. If not, how do I switch my default desktop loaded on startup from Gnome to Xfce. Is there a modification required to a startup script? If so, what and where?

3. How do I switch my default desktop back to Gnome?

4. How do I manually switch between them, e.g. keep Gnome as my default startup desktop and switch to xfce on the fly when I want to experiment. 

I'd like to try it, but I'd want to get a comfort level with it before switching it over as my default. Thus the need to know how to easily switch between the two on the fly, and the need to eventually know how to permanently switch the default  startup desktop. 

thanks.

---

### Post by erikpiper on 2005-11-29
When you log in, there is a button labeled "sessions". Try it! When you install xubuntu-desktop you start it from there. (Self explanitory)

---

### Post by kairu0 on 2005-11-30
[QUOTE=Luggy]I used to ues Xfce back in the day when I ran Gentoo.
Those slim window managers like xfce and openbox never really did it for me, I always felt less user friendly to me.[/QUOTE]

I don't like the XFCE panels. I don't like metacity.

Thank goodness you can fuse Gnome with xfwm for a hybrid experience.

---

### Post by otake-tux on 2005-11-30
I love xfce and I use to use it a lot when I was running gentoo but I find Xubuntu buggy.

This happened last night, for some unknown reason I could not make the menu appear when I right clicked on the dektop.  I thought it was strange but probably nothing.Later I restarted my machine, went into xfce and No wallpaper. all I have is a brown screen with the taskbar and panel. And when I right click I still get no menus.  The settings say the wallpaper is there yet its not.  I have no idea what the problem is and it never happened in Gentoo.  Has anyone else experienced this?

---

### Post by ranf on 2005-11-30
[QUOTE=otake-tux]I love xfce and I use to use it a lot when I was running gentoo but I find Xubuntu buggy.

This happened last night, for some unknown reason I could not make the menu appear when I right clicked on the dektop.  I thought it was strange but probably nothing.Later I restarted my machine, went into xfce and No wallpaper. all I have is a brown screen with the taskbar and panel. And when I right click I still get no menus.  The settings say the wallpaper is there yet its not.  I have no idea what the problem is and it never happened in Gentoo.  Has anyone else experienced this?[/QUOTE]
Did you eventually run Nautilus?

---

### Post by kaamos on 2005-11-30
[QUOTE=otake-tux]Later I restarted my machine, went into xfce and No wallpaper. all I have is a brown screen with the taskbar and panel. And when I right click I still get no menus.  The settings say the wallpaper is there yet its not.  I have no idea what the problem is and it never happened in Gentoo.  Has anyone else experienced this?[/QUOTE]

alt+f2 -> xfdesktop

Then save your session when logging out.

---

### Post by SFN on 2005-11-30
[QUOTE=blair]I'd like to experiment with xfce on Ubuntu, but I'm afraid I'd break my system. Questions:

1. What happens to system when you run install xubuntu-desktop? Does the system automatically switch from Gnome to Xfce?[/QUOTE]
No. Both Xfce and Gnome will be available. Gnome will start up by default.
[QUOTE=blair]2. If not, how do I switch my default desktop loaded on startup from Gnome to Xfce. Is there a modification required to a startup script? If so, what and where?[/QUOTE]
At the login screen, click "Sessions" and choose "Xfce Session", then click OK. Once you've done that, log in. You will be prompted to either make Xfce your default for all future sessions or just for this session.
[QUOTE=blair]3. How do I switch my default desktop back to Gnome?[/QUOTE]
If you chose "Just for this session" you will automatically be put back in Gnome next time you log in. If you chose "Make Default", getting back to Gnome is the same procedure as before. Just choose "Gnome" instead of "Xfce Session" after clicking "Sessions" on the login screen.
[QUOTE=blair]4. How do I manually switch between them, e.g. keep Gnome as my default startup desktop and switch to xfce on the fly when I want to experiment.[/QUOTE]
On the fly? You've got me there. I've never had a need to do it on the fly so I've never bothered trying to find out. I know that other distros (SuSE comes to mind) will allow you to switch from one to the other without logging out. Ubuntu may as well. I just took a quick look through the menus and didn't find anything but it may still be there.

---

### Post by otake-tux on 2005-11-30
xfdesktop
thats did it.

---

### Post by kairu0 on 2005-12-01
[QUOTE=otake-tux]xfdesktop
thats did it.[/QUOTE]

You can fix that by running the Gnome Configuration Editor and disabling the option under Nautilus called show_desktop. Then, you can run Nautilus all you like.

---

### Post by purdy hate machine on 2005-12-01
I really like XFCE; I can see it replacing Gome as my default DE one I get to grips with it.  
Is there a reason I can’t drag and drop a file onto the desktop? :confused:

---

### Post by kairu0 on 2005-12-01
[QUOTE=purdy hate machine]I really like XFCE; I can see it replacing Gome as my default DE one I get to grips with it.  
Is there a reason I can’t drag and drop a file onto the desktop? :confused:[/QUOTE]

You need to have a file manager handling desktop icons to do that, such as rox or Nautilus running in the background, drawing your wallpaper and icons.

---

### Post by purdy hate machine on 2005-12-01
[QUOTE=kairu0]You need to have a file manager handling desktop icons to do that, such as rox or Nautilus running in the background, drawing your wallpaper and icons.[/QUOTE]

Thanks, I'll give that a try.

---

### Post by sapo on 2005-12-01
Hi guys, i ve made a howto to help people who like me dont like rox as a file manager.

So you can install Thunar as a file manager, thunar pwnz :)

[http://ubuntuforums.org/showthread.php?t=95934](http://ubuntuforums.org/showthread.php?t=95934)

---

### Post by manicka on 2005-12-01
[QUOTE=sapo]

So you can install Thunar as a file manager, thunar pwnz :)

[http://ubuntuforums.org/showthread.php?t=95934](http://ubuntuforums.org/showthread.php?t=95934)[/QUOTE]

Looks just like nautilus?

---

### Post by szatyor on 2005-12-01
I really like Xubuntu, but how can I make it automount my CDs and DVDs. (It dosn't do.)
When I insert a CD, on the Gnome panel it appears, but nothing happens in Xfce.
THX

---

### Post by sapo on 2005-12-01
Yep, that look and feel are just like nautilus, it still doesnt have all the nautilus features, but is far faster than nautilus, and far easier than rox, its worth a try :)

---

### Post by phen on 2005-12-01
szatyor: try to load gnome-volume-manager  inside a terminal. does the cd automount now? if yes, try to autostart gnome-volume manager. i dont know how to do that in xfce, but there has to be some way :-)

---

### Post by jrincon87 on 2005-12-01
Hey, I haven't installed Xubuntu yet, because Synaptic says that it has to remove Abiword-gnome and replace it with Abiword. Does this mean that Abiword won't work anymore on Gnome?
And another question. Does Thunar or Rox support Gnome scripts, or is there a page where I can download some sort of plugin/script for Thunar/Rox? 
Thanks.

---

### Post by kairu0 on 2005-12-01
[QUOTE=jrincon87]Hey, I haven't installed Xubuntu yet, because Synaptic says that it has to remove Abiword-gnome and replace it with Abiword. Does this mean that Abiword won't work anymore on Gnome?[/QUOTE]

No. You might miss a little GNOME-specific functionality, but you certainly won't lose Abiword.

---

### Post by jrincon87 on 2005-12-01
Hey. I installed Xubuntu. Really fast but I didn't like it so much. It still lacks of features. How can I remove Xubuntu with all the bunch of packages it installed and that are not necessary anymore?
Thanks.

---

### Post by A-star on 2005-12-02
How did you get your launch bar at the top of the screen?
-> drag and drop apparently, how could I have ignored that.

---

### Post by kaamos on 2005-12-02
[QUOTE=jrincon87]Hey. I installed Xubuntu. Really fast but I didn't like it so much. It still lacks of features. How can I remove Xubuntu with all the bunch of packages it installed and that are not necessary anymore?
Thanks.[/QUOTE]

These are the packages that I got with it. Yours might obviously be slightly different.. I installed on on gnome, so if you're using kubuntu there might also be a couple of gnome packages.
```

  abiword abiword-common gqview gtk2-engines-xfce libexo0.3-0
  libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3
  mousepad rox-filer xfcalendar xfce4 xfce4-appfinder xfce4-artwork
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-datetime-plugin
  xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies
  xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins
  xfce4-minicmd-plugin xfce4-mixer xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-panel-menu-plugin xfce4-sensors-plugin xfce4-session
  xfce4-showdesktop-plugin xfce4-systemload-plugin xfce4-systray
  xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-toys
  xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin
  xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4
  xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-desktop

```

---

### Post by SFN on 2005-12-07
[QUOTE=phen]try to autostart gnome-volume manager. i dont know how to do that in xfce, but there has to be some way :-)[/QUOTE]

Click the Xfce Menu button and choose "Run Application..."
Type in "gnome-volume-manager &&" (without the quotes)
Click the Xfce Menu button again and choose "Quit"
Make sure that "Save session for future logins" and "Reboot the computer" are checked and click the button labeled "OK"
Once you log back in, gnome-volume-manager should be running

It's not actually necessary to reboot. You could choose "Quit current session" instead of "Reboot the computer" but I reboot anyway to make sure that things are running the way I want them to on actual startup.

---

### Post by DariusTriplet on 2005-12-07
I have to agree that XFCE rocks.  When it comes to DEs, I'm more practical than aesthetical; I gladly sacrificed Gnome's pizzaz for XFCE's speed.

One of these days, I might make the final step and start using EvilWM.  :p

---

### Post by kairu0 on 2005-12-07
[QUOTE=DariusTriplet]I have to agree that XFCE rocks.  When it comes to DEs, I'm more practical than aesthetical; I gladly sacrificed Gnome's pizzaz for XFCE's speed.[/QUOTE]

I really don't feel like I'm sacrificing anything by using XFCE. There are really no gnome features that I use and can't find in xfce.

---

### Post by towsonu2003 on 2005-12-10
I've got this for your 'will there be a CD for xubuntu' question, but I have no idea whether it will work or not or whether anyone will be interested in it or not... pure luck :) And someone has to do it first so that it can be helpful for you or anyone who wants an offline xubuntu install... 

[http://ubuntuforums.org/showthread.php?t=101790](http://ubuntuforums.org/showthread.php?t=101790)

PS. I used xfce in Slackware and it was nice (I like the crazy running mouse)...

---

### Post by blair on 2005-12-11
SFN, thanks for the reply. You answered my questions. When I said 'on the fly' I meant without permanently wedding by OS to one desktop. The ability to select which window manager I want to use at login time is perfect and what I wa looking for. Thanks.

---

### Post by Neo40 on 2005-12-12
Hi,

I have just installed xubuntu on my another hdd. Everything went fine except when I boot, I dont see the splash ubuntu logo. How can I active it?

Thanks!

---

### Post by kaamos on 2005-12-12
Try: sudo dpkg-reconfigure linux-image-$(uname -r)

---

### Post by SFN on 2005-12-13
[QUOTE=blair]SFN, thanks for the reply. You answered my questions. When I said 'on the fly' I meant without permanently wedding by OS to one desktop. The ability to select which window manager I want to use at login time is perfect and what I wa looking for. Thanks.[/QUOTE]

Ahh, OK. Glad I could help.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=kairu0]I really don't feel like I'm sacrificing anything by using XFCE. There are really no gnome features that I use and can't find in xfce.[/QUOTE]

Tell that to my pen drive (that lacks a neat icon on the desktop in XFCE).

---

