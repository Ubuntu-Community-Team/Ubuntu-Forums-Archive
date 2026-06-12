---
title: "OpenBox - Really Impressed"
date: 2008-08-20
forum: The Cafe
---

### Post by BGFG on 2008-08-20
Hi All, 
Thanks to this thread:

[http://ubuntuforums.org/showthread.php?t=893300&page=5](http://ubuntuforums.org/showthread.php?t=893300&page=5)

I'm now using OpenBox and i have to say i'm really impressed. Looks nice and clean and uber-fast.

Anyone else want to try just:

[LIST=1]
[*]System>>Administration>>Synaptic Package manager then search : Openbox
[*]Install Openbox
[*]Terminal  :  $ openbox --replace
[*]Enjoy the Speed
[/LIST]

[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox) for more information

---

### Post by Dr Small on 2008-08-20
And yet... you are still using the rest of the GNOME desktop. Try to dig down deep and only use Openbox; You will enjoy it better :)

---

### Post by kk0sse54 on 2008-08-20
Pure open box is definitively the best as its just so clean and fast.

---

### Post by Sealbhach on 2008-08-20
It sure is fast, but I like all my snazzy Compiz effects. It doesn't accomodate them.

.

---

### Post by BGFG on 2008-08-20
> **Dr Small said:**
> And yet... you are still using the rest of the GNOME desktop. Try to dig down deep and only use Openbox; You will enjoy it better :)

In the Openbox session right now, Blank Desktop LOL. Should i use the gnome panel or some other ? How can i access apps ? havn't figured it out yet....

Yuh know, maybe if i had a graphics card, i'd be more attached to effects. But i'm turning into a speed demon....

---

### Post by Dr Small on 2008-08-20
> **BGFG said:**
> In the Openbox session right now, Blank Desktop LOL. Should i use the gnome panel or some other ? How can i access apps ? havn't figured it out yet....

Yuh know, maybe if i had a graphics card, i'd be more attached to effects. But i'm turning into a speed demon....
Pypanel for a panel, feh for a desktop wallpaper, obconf for an openbox configuration editor (if you need that). You gave a link to the Wiki page, there is a boatload of information there that should get you started.

Pure Openbox is the way to go.
[[IMG]http://img28.picoodle.com/img/img28/4/7/19/drsmall/t_20080719162m_3cd032a.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/19/drsmall/f_20080719162m_3cd032a.png&srv=img28)

---

### Post by aktiwers on 2008-08-20
You can right-click! :D

I haven't done it yet, but I guess you need to configure it (with config files).
Then find yourself a light panel (if you want a panel) and a light filemanager.

[http://gentoo-wiki.com/HOWTO_Openbox#Standalone_Openbox](http://gentoo-wiki.com/HOWTO_Openbox#Standalone_Openbox)
[http://icculus.org/openbox/index.php/Help:Contents](http://icculus.org/openbox/index.php/Help:Contents)

---

### Post by BGFG on 2008-08-20
> **Dr Small said:**
> Pypanel for a panel, feh for a desktop wallpaper, obconf for an openbox configuration editor (if you need that). You gave a link to the Wiki page, there is a boatload of information there that should get you started.

Pure Openbox is the way to go.

i was looking at the pypanel homepage, maybe i'm wrong but has development stopped ? or is it still ongoing ?
Using obconf already :)

So now i'll have Openbox and Pypanel. Might as well go all the way and change my filemanager.

HA HA ! just installed pypanel
```

sudo aptitude install pypanel

```
Then started it with
```

pypanel

```

Oh My GOD. linux is just too much fun!

---

### Post by picpak on 2008-08-20
See this for help:

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Good luck! :)

---

### Post by BGFG on 2008-08-20
> **aktiwers said:**
> You can right-click! :D

I haven't done it yet, but I guess you need to configure it (with config files).
Then find yourself a light panel (if you want a panel) and a light filemanager.

[http://gentoo-wiki.com/HOWTO_Openbox#Standalone_Openbox](http://gentoo-wiki.com/HOWTO_Openbox#Standalone_Openbox)
[http://icculus.org/openbox/index.php/Help:Contents](http://icculus.org/openbox/index.php/Help:Contents)

hey,
Right clicking does not give me an option to launch apps yet. Nor do i see anywhere to add pypanel to my session rather that 'terminaling' it. 
Is it that i need to configure my keyboard shortcuts ?

Thanks All!


I havn't been reading near enough. Gonna edit my autostart file now. :)

---

### Post by Dr Small on 2008-08-20
Basically for me, I create a init script and include everything I want in it when I want my WM to start. Stuff like xkeymaps, conky, pypanel, my wallpaper and any other thing I like to have startup. Give it +x, and then in my .xinitrc, I have it initialize my init script, so when Openbox runs, all of my other stuff loads before hand.

Example init script:
```
#!/bin/bash
# ~/bin/init

WALLPAPER="/usr/share/wallpapers/archlinux/DSCF0037_1.JPG"
feh --bg-scale $WALLPAPER&

xscreensaver -nosplash&
xmodmap -e "keycode 111 = F13"&
xmodmap -e "pointer = 3 2 1"
#xmodmap -e "keycode 66 = Return"&

sleep 1 
conky&
pypanel&
```

And the example .xinitrc file:
```
#!/bin/sh


. /home/drsmall/bin/init
#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#
#exec wmii
# exec gnome-session
# exec startkde
# exec startxfce4
# exec icewm-session
exec openbox
# exec blackbox
# exec fluxbox
# exec ratpoison
# exec dwm
# ... or any other WM of your choosing ...

```

As for the right-click menu, the file should be located at:
```
/etc/xdg/openbox/menu.xml
```

(This may be different on an Ubuntu Based system)
Copy this file to ~/.config/openbox/ and edit away.

Dr Small

---

### Post by chris4585 on 2008-08-20
fbpanel ftw 

see my signature

---

### Post by BGFG on 2008-08-20
I've done some reading, Some copying and pasting :) 
and this is how my autostart looks currently:

```

# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
gnome-volume-manager &
xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

# SCIM support (for typing non-english characters)
export LC_CTYPE=ja_JP.utf8
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
export QT_IM_MODULE=scim
scim -d &

# Programs that will run after Openbox has started
sleep 2 && pypanel &
sleep 10 && avant-window-navigator &

```

Still rough around the edges i think. I was getting an error with avant until i installed xcompmgr and pypanel isnt loading now. That i think is obvious because both it and avant can't take the same space on the desktop. 

Also, right click on Avant and 'preferences' produces nothing.
And quite honestly, i do not know what that code after xcompmgr is for.

until i get this session up properly, i have to jump between this and gnome sessions. My sister will simply not have it...

---

### Post by RiceMonster on 2008-08-20
Obviously you're impressed by Openbox, it's the best WM around :).

> **Dr Small said:**
> Pypanel for a panel, feh for a desktop wallpaper, obconf for an openbox configuration editor (if you need that). You gave a link to the Wiki page, there is a boatload of information there that should get you started.

Pure Openbox is the way to go.
[[IMG]http://img28.picoodle.com/img/img28/4/7/19/drsmall/t_20080719162m_3cd032a.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/19/drsmall/f_20080719162m_3cd032a.png&srv=img28)

You need a gtk theme man! 

> **chris4585 said:**
> fbpanel ftw 

see my signature

No panel ftw :).

---

### Post by eriqjaffe on 2008-08-20
The code after xcompmgr is simply configuration of xcompmgr, setting things like shadow depth, size, etc.

I don't bother with the SCIM stuff in mine:
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

#Force OpenOffice.org to use GTK theme
export OOO_FORCE_DESKTOP=gnome

# Programs to launch at startup
wget -O /home/eriq/.myip http://whatismyip.com/automation/n09230945.asp
autocutsel -f &
feh --bg-scale /home/eriq/.themes/Life_Envelops_the_Green_World-1680x1050.jpg &
xcompmgr -c -t-5 -l-5 -r0 -o.55 -f &
parcellite &

# Programs that will run after Openbox has started
conky -d &
lxpanel &
cairo-dock &
```
IIRC, to use sleep, you have to do something like:
```
(sleep 2 && command) &
```
...but I could be mistaken about that.  Looking at yours, 15 seconds of sleep time seems a bit excessive.

Also, you should be able to set up pypanel to use the top of your screen instead of the bottom.

---

### Post by BGFG on 2008-08-20
Was getting a Locale error. Took out SCIm support stuff, Avant and pypanel loading fine now.

Starting to feel more comfortable with the autostart file now. Working on getting pypanel to the top of the screen. Also adding the Ubuntu start menu to Avant.

Thanks for posting your autostart file. I have some more work to do :)

---

### Post by picpak on 2008-08-21
Glad to see you're liking it :)

I recommend that you take a look at the [LXDE](http://ubuntuforums.org/showthread.php?t=738958) project. There are some programs there that you could use for your Openbox. I use lxappearance, lxpanel and lxtask. There's also pcmanfm and gpicview, but I prefer Thunar and Ristretto, respectively. You can configure lxtask to run when you press Ctrl-Alt-Delete, and change your GTK theme with lxappearance, and so on and so forth. Have fun!

---

