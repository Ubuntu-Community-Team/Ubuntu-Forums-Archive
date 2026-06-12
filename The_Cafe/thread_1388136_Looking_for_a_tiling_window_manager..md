---
title: "Looking for a tiling window manager."
date: 2010-01-22
forum: The Cafe
---

### Post by AllRadioisDead on 2010-01-22
Hi guys, 
I'm looking for a nice simple tiling window manager. I'm interested in trying one out, I've played with awesome a bit but it's far too complicated for me. With all the widgets, key-bindings and the config file in lua, it's a little bit too complex for me. Not to say there isn't great documentation available, it's just a lot to take on at once. I'd like to get the feel to how one works. Any suggestions? I hope this doesn't turn into a flame war like the browser war threads. :(

---

### Post by dragos240 on 2010-01-22
I've played around with DWM. There is a slight learning curve, but you'll get used to it.

---

### Post by schauerlich on 2010-01-22
[wmii](http://wmii.suckless.org/)

---

### Post by m_duck on 2010-01-22
I would also recommend [dwm](http://dwm.suckless.org/). All of the configuration is done by modifying the config.h source file. This means that to see changes, it must be recompiled, but that takes all of half a second. For that reason I tend not to actually *install* it as such, but download the source, configure it, **make**, and then run the resulting executable from where it is. Probably bad practice but hey ho.

---

### Post by n0dix on 2010-01-22
The more popular are: awesome, dwm, xmonad, a big etc

---

### Post by mikkie on 2010-01-22
Ratpoison 4 life! It is the most minimalistic and easy to use and configure tiling window manager. Give it a try!

---

### Post by ~sHyLoCk~ on 2010-01-22
+1 for ratpoison

---

### Post by AllRadioisDead on 2010-01-22
> **mikkie said:**
> Ratpoison 4 life! It is the most minimalistic and easy to use and configure tiling window manager. Give it a try!
I'll look into it, thanks.
> **n0dix said:**
> The more popular are: awesome, dwm, xmonad, a big etc
Thanks, but I'm not necessarily looking for the most popular.

> **m_duck said:**
> I would also recommend [dwm]("http://dwm.suckless.org/"). All of the configuration is done by modifying the config.h source file. This means that to see changes, it must be recompiled, but that takes all of half a second. For that reason I tend not to actually *install* it as such, but download the source, configure it, **make**, and then run the resulting executable from where it is. Probably bad practice but hey ho.
I'll look into it, thanks.
> **schauerlich said:**
> [wmii]("http://wmii.suckless.org/")
Reasoning?

---

### Post by schauerlich on 2010-01-22
> **ihermit said:**
> Reasoning?

Suckless makes good stuff. Small, easily customizable, doesn't require recompiling each time you change something.

---

### Post by AllRadioisDead on 2010-01-22
> **schauerlich said:**
> Suckless makes good stuff. Small, easily customizable, doesn't require recompiling each time you change something.
Fair enough.

However, on my search I ran into a nice window manager called scrotwm, and I must say I love it. It' just what I'm looking for, nice and simple. The keybindings are logical and after printing out the page about it on the archwiki, I'm good to go. It's very easy to use and configure, and doesn't need compiling.

---

### Post by kk0sse54 on 2010-01-22
> **ihermit said:**
> Fair enough.

However, on my search I ran into a nice window manager called scrotwm, and I must say I love it. It' just what I'm looking for, nice and simple. The keybindings are logical and after printing out the page about it on the archwiki, I'm good to go. It's very easy to use and configure, and doesn't need compiling.

I was just about to recommend scrotwm :p. It's a great window manager though and another quality piece of software coming from some of the OpenBSD crew. If I wasn't already in love with awesome I'd use it more extensively.

---

### Post by RiceMonster on 2010-01-22
I like dwm because it's very simple and straight forward. Sure you have to edit a header file and recompile, but the way it's organized, it's not much different than editing a config file. 

Scrotwm would be next in line.

---

### Post by k64 on 2010-01-22
I would just have bare X and Compiz. I personally LOVE compositing.

---

### Post by AllRadioisDead on 2010-01-22
> **C!oud said:**
> I was just about to recommend scrotwm :p. It's a great window manager though and another quality piece of software coming from some of the OpenBSD crew. If I wasn't already in love with awesome I'd use it more extensively.
Awesome does look amazing, and I still believe I have to give it a fair chance. I will read some more and maybe give it another try. It looks really extensible. 
> **RiceMonster said:**
> I like dwm because it's very simple and straight forward. Sure you have to edit a header file and recompile, but the way it's organized, it's not much different than editing a config file. 

Scrotwm would be next in line.
DWM looks tempting as well, I will do some reading up on it.
> **k64 said:**
> I would just have bare X and Compiz. I personally LOVE compositing.
That's nice, unfortunately that's not what I was looking for.

---

### Post by schauerlich on 2010-01-22
> **ihermit said:**
> I'm looking for a nice simple tiling window manager. 

> **k64 said:**
> I would just have bare X and Compiz.

What is this I don't even

---

### Post by kevCast on 2010-01-23
Stumpwm. It's the successor to Ratpoison, and written entirely in Common Lisp.

---

### Post by k64 on 2010-01-23
By any luck, I would stick with a full DE, such as [GNOME]('apt:/ubuntu-desktop') or [KDE]('apt:/kubuntu-desktop')

---

### Post by ~sHyLoCk~ on 2010-01-23
Omg I almost forgot the epic wm try Musca! It's pretty sweet. Has features from ratpoison and dwm. It's really light and fast, takes like 400Kb of mem.

---

### Post by AllRadioisDead on 2010-01-23
> **k64 said:**
> By any luck, I would stick with a full DE, such as [GNOME]("apt:/ubuntu-desktop") or [KDE]("apt:/kubuntu-desktop")
That's nice, but once again it has nothing to do with the thread.
> **~sHyLoCk~ said:**
> Omg I almost forgot the epic wm try Musca! It's pretty sweet. Has features from ratpoison and dwm. It's really light and fast, takes like 400Kb of mem.
I read that musca doesn't have support for floating windows, if this is true I think I'll have to rule it out.

---

### Post by &#32 Greg on 2010-01-23
Something you might want to check out is bluetile (just to play with, in case you find ScrotWM not what you were looking for after all).

---

### Post by AllRadioisDead on 2010-01-23
> **&#32 Greg said:**
> Something you might want to check out is bluetile (just to play with, in case you find ScrotWM not what you were looking for after all).
Looks cool, I didn't know anything like that existed. I wanted to get away from gnome though, looks cool. I definitely will try it.

---

### Post by &#32 Greg on 2010-01-23
> **ihermit said:**
> Looks cool, I didn't know anything like that existed. I wanted to get away from gnome though, looks cool. I definitely will try it.

It would probably work nicely en route to pure Xmonad...

---

### Post by n0dix on 2010-01-23
> **  Greg said:**
> It would probably work nicely en route to pure Xmonad...

+1 agree. Xmonad ftw. :lol:

---

### Post by AllRadioisDead on 2010-01-23
I'm playing with dwm right now, it works the same way as scrotwm so it feels familiar. 
Also, since there's no system tray, I need to use a third party app like trayer right? 
I know openbox has an autostart.sh, but how can I autostart applications in dwm/scrotwm?
Sorry, I know this isn't support, and I know I'm nub.
Thanks :D

---

### Post by AllRadioisDead on 2010-01-24
I'm officially addicted to dwm. I love it.
I've installed a crunchbang lite system, and removed all the openbox stuff, it comes preinstalled with dwm, so I removed it and then downloaded the source, customized the config file and compiled. Works great!

---

### Post by m_duck on 2010-01-24
How are you starting dwm? Via xinitrc and startx or a login manager (... or some other way)? If via xinitrc there are a couple of possibilities, both amounting to being almost the same.

The first is just add the programs you want autostarted before the exec dwm line, such as:```
# Wallpaper
eval `cat $HOME/.fehbg` &
pidgin &
exec dwm
```The second is to move all that into a script to keep xinitrc looking nice, so you don't need to comment a bunch of stuff if you change window managers. So .xinitrc would look like:```
exec $HOME/scripts/startdwm
```Then you need to write a script called (in the case of the above) ~/scripts/startdwm:```
#!/bin/bash
eval `cat $HOME/.fehbg` &
pidgin &
exec dwm
```Once you have written the script, make it executable and you're good to go:```
chmod +x ~/scripts/startdwm
```Note that if you have not installed dwm as I mentioned in an earlier post (I think), where I have written ***exec dwm***, it would need to be ***exec /path/to/dwm***.

If you use a login manager... I'm not sure as I've not used one in a while. I should imagine the same basic idea would apply. Possibly you have to make a new .desktop file, and where the command */usr/bin/dwm* would go, just point it to the script.

---

### Post by n0dix on 2010-01-24
> **ihermit said:**
> I'm officially addicted to dwm. I love it.


I recommend you to use for a while and then change to another tiling. In my case i started to use awesome, then change to dwm, and i'm trying xmonad. I think this is the way you can form an opinion yourself. 

Btw, to customize dwm: [http://ubuntuforums.org/showthread.php?t=642808](http://ubuntuforums.org/showthread.php?t=642808)

---

### Post by AllRadioisDead on 2010-01-24
> **m_duck said:**
> How are you starting dwm? Via xinitrc and startx or a login manager (... or some other way)? If via xinitrc there are a couple of possibilities, both amounting to being almost the same.

The first is just add the programs you want autostarted before the exec dwm line, such as:```
# Wallpaper
eval `cat $HOME/.fehbg` &
pidgin &
exec dwm
```The second is to move all that into a script to keep xinitrc looking nice, so you don't need to comment a bunch of stuff if you change window managers. So .xinitrc would look like:```
exec $HOME/scripts/startdwm
```Then you need to write a script called (in the case of the above) ~/scripts/startdwm:```
#!/bin/bash
eval `cat $HOME/.fehbg` &
pidgin &
exec dwm
```Once you have written the script, make it executable and you're good to go:```
chmod +x ~/scripts/startdwm
```Note that if you have not installed dwm as I mentioned in an earlier post (I think), where I have written ***exec dwm***, it would need to be ***exec /path/to/dwm***.

If you use a login manager... I'm not sure as I've not used one in a while. I should imagine the same basic idea would apply. Possibly you have to make a new .desktop file, and where the command */usr/bin/dwm* would go, just point it to the script.
I am using a login manager, gdm. Upon compiling dwm for the first time, I did create a .desktop file for dwm and it works fine. If I'm using a login manager, will .xinitrc not work? I've done a little bit of digging but I can't find anything.
> **n0dix said:**
> I recommend you to use for a while and then change to another tiling. In my case i started to use awesome, then change to dwm, and i'm trying xmonad. I think this is the way you can form an opinion yourself. 

Btw, to customize dwm: [http://ubuntuforums.org/showthread.php?t=642808](http://ubuntuforums.org/showthread.php?t=642808)
Thanks for the thread, I've already been reading it. The thread's a bit dated, but helpful nonetheless. :P

---

### Post by RiceMonster on 2010-01-24
> **ihermit said:**
> I am using a login manager, gdm. Upon compiling dwm for the first time, I did create a .desktop file for dwm and it works fine. If I'm using a login manager, will .xinitrc not work? I've done a little bit of digging but I can't find anything.

Create a script, like so
```
#!/bin/bash
# Add whatever you want to autostart here (don't forget the & after each program)
trayer &
nitrogen --restore &
super-cool-awesome-autostart-this &

# THE BELOW LINE MUST BE LAST
exec dwm
```

Now edit the .desktop file you created, and point to the script at Exec=

---

### Post by AllRadioisDead on 2010-01-24
> **RiceMonster said:**
> Create a script, like so
```
#!/bin/bash
# Add whatever you want to autostart here (don't forget the & after each program)
trayer &
nitrogen --restore &
super-cool-awesome-autostart-this &

# THE BELOW LINE MUST BE LAST
exec dwm
```Now edit the .desktop file you created, and point to the script at Exec=
Thanks RiceMonster!
Worked like a charm.

---

