---
title: "i don't understand...uh, compiz"
date: 2006-08-11
forum: The Cafe
---

### Post by fuscia on 2006-08-11
all i know about it is that it's some kind of funny effects thing. there have been a number of things at gnome-look for cgwd (wtf is that?:confused: ) that i would like to try. i need new eye candy tools. i don't know what to do. please hold my hand, mommy. i have a nvidea nv43 geo force 6600 kind of thing. i got my laptop with dapper installed, so i don't know what was done with the video card, etc. etc. you get the idea - r*t*rd doesn't understand the manual.

---

### Post by 23meg on 2006-08-11
> all i know about it is that it's some kind of funny effects thing. It's a compositing manager + a window manager + a set of user interface enhanchements.

Did you follow [these instructions]("http://www.ubuntuforums.org/showthread.php?t=222034")? At what step did you fail or what do you not understand?

(PS: this should perhaps be moved to a support forum)

---

### Post by fuscia on 2006-08-11
> **23meg said:**
> It's a compositing manager + a window manager + a set of user interface enhanchements.

Did you follow [these instructions]("http://www.ubuntuforums.org/showthread.php?t=222034")? At what step did you fail or what do you not understand?

it's all so foreign to me. should i just do that and i'll be all set?

---

### Post by ComplexNumber on 2006-08-11
> **fuscia said:**
> all i know about it is that it's some kind of funny effects thing. there have been a number of things at gnome-look for cgwd (wtf is that?:confused: ) that i would like to try. i need new eye candy tools. i don't know what to do. please hold my hand, mommy. i have a nvidea nv43 geo force 6600 kind of thing. i got my laptop with dapper installed, so i don't know what was done with the video card, etc. etc. you get the idea - r*t*rd doesn't understand the manual.
from what i remember, you need several components:
-gnome & metacity (no idea what the score is with kde or any other WM)
-xcompmgr
-x11-damage
-x11-composite
-x11-something else that i can't remember

sorry i can't be more helpful. that link that 23meg has provided doesn't seem to want to open for me, so maybe its the same for you.

---

### Post by GuitarHero on 2006-08-11
[http://www.ubuntuforums.org/showthread.php?t=194993&highlight=automatic+installation+xgl](http://www.ubuntuforums.org/showthread.php?t=194993&highlight=automatic+installation+xgl)

---

### Post by fuscia on 2006-08-11
> **GuitarHero said:**
> [http://www.ubuntuforums.org/showthread.php?t=194993&highlight=automatic+installation+xgl](http://www.ubuntuforums.org/showthread.php?t=194993&highlight=automatic+installation+xgl)

well, it's running. (the script, that is.)

---

### Post by fuscia on 2006-08-11
ok, so i ran that script, rebooted and found xgl in the gdm menu, but now, i can not long into xgl, or gnome (i'm using openbox for this post). what do i do now?

---

### Post by gruvsyco on 2006-08-11
Firstly, do you have the accelerated drivers running?  The first thing in getting Compiz/XGL running and enjoyable is getting your accelerated X drivers running.

---

### Post by gruvsyco on 2006-08-11
Oh... and just a little aside note here... CGWD is a hack that Quinn and Co did on the original Compiz Window decorations to support theming and later theming engines.

---

### Post by fuscia on 2006-08-11
> **gruvsyco said:**
> Firstly, do you have the accelerated drivers running?  The first thing in getting Compiz/XGL running and enjoyable is getting your accelerated X drivers running.

accelerated drivers? what's that?

---

### Post by 23meg on 2006-08-11
The proprietary NVidia driver.

---

### Post by fuscia on 2006-08-11
so, i can get into kde and openbox, but not xgl or gnome. what can i do?

---

### Post by gruvsyco on 2006-08-11
I tried looking at the script you ran to see what all it did.  I couldn't figure it out.  If it's using the "Start XGL via GDM" method it should not have done anything to Gnome.

Is there an uninstall option for what it did?  I saw something in the script about saving original config stuff out.
```

"This scrip may have modified and backed up the following files: /etc/apt/sources.list and /etc/X11/xorg.conf."
```

Personally, at the state that Compiz/XGL is at and all the difficulties people have with it, I wouldn't use any complete automation script yet.  But, don't give up on it...  Just do it step by step.  If you can get your gnome back, try again by first getting your drivers installed.

I'll keep watching here to see what I can do to help out.. I'm on ATI hardware so I can't offer much help there but, after that, I can try my best to help.

---

### Post by fuscia on 2006-08-11
i think i just need to uninstall what i just did and go back to the times of innocense. how would i uninstall this mess?

---

### Post by nalmeth on 2006-08-11
Did you ever do this fuscia?
```
 sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
 sudo nvidia-glx-config enable
```  Don't give up just yet

In the case that this messes up X and you can't log in, go to virtual terminal and get back to normal with
```
 sudo dpkg-reconfigure xserver-xorg
```
and pick the nv rather than nvidia driver

---

### Post by OffHand on 2006-08-11
I just managed to get it working myself after a lot of tweaking and excellent help on irc. I really recommend you go there for help. It's awesome ro run xgl and some fx are amazing.

/join #xgl
/join #ubuntu-xgl

and check this video:

[http://www.youtube.com/watch?v=i9JC5NQ7G0o](http://www.youtube.com/watch?v=i9JC5NQ7G0o)

---

### Post by ComplexNumber on 2006-08-11
**fuscia**
you say that you can't log into gnome. what actually happens when you try to log in? any errror messages etc?

---

### Post by fuscia on 2006-08-11
> **ComplexNumber said:**
> **fuscia**
you say that you can't log into gnome. what actually happens when you try to log in? any errror messages etc?

it tries to login and then just goes back to gdm.

i no longer want to get this working. i want to uninstall xgl and go back to the way things were. how can i do that?

---

### Post by nalmeth on 2006-08-11
I read through the thread where you found the script.. It installed the quinn packages, which (i think) are the newer less stable compiz packages. Could be wrong.

You should try posting there for help backtracking and removing what the script did.

I know you want compiz gone, but aparently what you've having isn't uncommon after running that script, and a possible solution appears to be:
```
 sudo apt-get install libgl1-mesa libglitz1 libglitz-glx1 xserver-xgl compiz compiz-gnome gset-compiz
```to get gnome to be able to load. 
Leave out gset-compiz if it doesn't find it. Just try this first before you try removing stuff that could dig you even deeper. 
If you have no window borders, just run metacity in a terminal or with ALT-F2

Another possible solution (to go back to normal) would be to backup the current xorg.conf, and make a new one, but with a new Xserver installed I don't know what the script did, and what might happen. 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.xgl
sudo dpkg-reconfigure xserver-xorg
``` Pick all the defaults unless you know better
Still I would hold off the above measure, since you can still use openbox. I don't know what could happen, since I haven't messed around much with this, because it just worked for me. Since it's backed up though, you will still be able to revert to the old xorg.conf if things don't work out.

Probably the best thing to do is go to that thread and ask the author or others for help.

Maybe next time you might want to just try out the Kororaa liveCD, or follow a step-by-step thread instead. It's easier to fix things then

Good luck man

---

### Post by fuscia on 2006-08-11
> **nalmeth said:**
> code] sudo apt-get install libgl1-mesa libglitz1 libglitz-glx1 xserver-xgl compiz compiz-gnome gset-compiz[/code]

so, i just tried that and got a little further into gnome. the panels started to appear and then i got the black screen of disappointment and gdm came back on. i've pm'ed the author of the script for advice.

---

### Post by atrus123 on 2006-08-11
It sort of sounds to me like XGL is loading but Compiz isn't.

Did you add cgwd & and compiz --replace gconf & to your sessions?

---

### Post by fuscia on 2006-08-11
> **atrus123 said:**
> It sort of sounds to me like XGL is loading but Compiz isn't.

Did you add cgwd & and compiz --replace gconf & to your sessions?

no, i don't even know what that stuff is. you wouldn't happen to know how i could get rid of all this, would you?

---

### Post by benplaut on 2006-08-11
hehehehehehe!!!!!

this is why us openbox users don't like fx :D

---

### Post by fuscia on 2006-08-12
> **benplaut said:**
> hehehehehehe!!!!!

this is why us openbox users don't like fx :D

your kind thoughts, at this difficult time, have been a comfort to my whole family.

---

### Post by forrestcupp on 2006-08-12
If you want to uninstall, I think what you need to do is:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

then delete the following lines out that you should have already entered earlier:

```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

if you added a startcompiz (or similar) script to your session startup, you need to go back in, and take it out.

Then go to synaptic, and search for xserver-xgl.  If it truly was installed, remove it.

You should reboot to a normal xorg server.

Basically what you're doing is the reverse of what you did when you followed the how-to on installing it.

---

### Post by fuscia on 2006-08-12
> **forrestcupp said:**
> If you want to uninstall, I think what you need to do is:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

then delete the following lines out that you should have already entered earlier:

```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

anytime i've checked that file, during these tragic events, there has never been anything after *[ server ]*

> if you added a startcompiz (or similar) script to your session startup, you need to go back in, and take it out.


i'm not sure what the session startup files are. if you mean .xsession and .xinitrc, both of those are blank. 

obviously, xgl is not ready for the desktops of total morons who have no idea wtf they're doing. (we need a 't*rd smiley.)

---

### Post by OffHand on 2006-08-12
> **fuscia said:**
> anytime i've checked that file, during these tragic events, there has never been anything after *[ server ]*



i'm not sure what the session startup files are. if you mean .xsession and .xinitrc, both of those are blank. 

obviously, xgl is not ready for the desktops of total morons who have no idea wtf they're doing. (we need a 't*rd smiley.)

Why don't you go to their irc channel and ask? They have excellent support.

---

### Post by fuscia on 2006-08-12
woooooooooooooohooooooooooooooooooo!!!1 i got gnome back. i couldn't find any of the things in gdm.conf-custom that everyone was suggesting i needed to get rid of, so i just went into synaptic and removed all the xgl/compiz stuff and now, gnome is back. 

thanks everyone for your help on my way into stupid and on my way back out. and thanks for your patience, as well. (is it really silly to feel elated over something like this?)

---

### Post by nalmeth on 2006-08-12
[Kororaa LiveCD]("http://kororaa.org/static.php?page=static060318-181203")

In all fairness, I think the problems came up because you ran a script that automates something that at this point should be done step by step.

There are a few guides out there that offer awesome 'stepbystep' 'copyandpaste' instructions.

Don't mean to take anything away from the author, because it seems to have worked great for a lot of people.

---

### Post by fuscia on 2006-08-12
> **nalmeth said:**
> [Kororaa LiveCD]("http://kororaa.org/static.php?page=static060318-181203")

In all fairness, I think the problems came up because you ran a script that automates something that at this point should be done step by step.

There are a few guides out there that offer awesome 'stepbystep' 'copyandpaste' instructions.

Don't mean to take anything away from the author, because it seems to have worked great for a lot of people.

looking at the screenshots threads, it's obvious a lot of people are getting it working and a number of people got it working from that script. i just wasn't one of them.

---

### Post by gruvsyco on 2006-08-13
It's too bad you gave up.  I notice you post a lot in the screenshots thread, I think you'd probably have a lot of fun with it.  I spent the day today trying to get XGL/Compiz running with KDE and XFCE and playing around inside each DE... great stuff.

---

### Post by fuscia on 2006-08-13
> **gruvsyco said:**
> It's too bad you gave up.  I notice you post a lot in the screenshots thread, I think you'd probably have a lot of fun with it.  I spent the day today trying to get XGL/Compiz running with KDE and XFCE and playing around inside each DE... great stuff.

you're right, i probably would have fun with it, but i don't have the skill or patience to get it running now. i'll just have to wait 'til *xgl for r*t*rds* is available.

---

### Post by forrestcupp on 2006-08-13
If you use any opengl games or apps, it's not worth it right now anyway.  To get things to work right, you have to switch back and forth between xgl and normal server.  When they get kinks like that worked out, I'll go for it, but I tried, and for those reasons decided to take it off, and wait till later.

---

### Post by nalmeth on 2006-08-13
> **forrestcupp said:**
> If you use any opengl games or apps, it's not worth it right now anyway.  To get things to work right, you have to switch back and forth between xgl and normal server.  When they get kinks like that worked out, I'll go for it, but I tried, and for those reasons decided to take it off, and wait till later.
That's not the case for me.
I haven't tried any games while runing AIGLX, but Celestia, Google Earth work fine. Also there is a fix somewhere in the forums for getting 3D games to work simultaneously with XGL

---

### Post by fuscia on 2006-08-13
*locate* is a fine command.

---

### Post by _simon_ on 2006-08-14
> **forrestcupp said:**
> If you use any opengl games or apps, it's not worth it right now anyway.  To get things to work right, you have to switch back and forth between xgl and normal server.  When they get kinks like that worked out, I'll go for it, but I tried, and for those reasons decided to take it off, and wait till later.

Not true.

You just need to do this:

[http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games](http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games)

---

### Post by forrestcupp on 2006-08-14
> **_simon_ said:**
> Not true.

You just need to do this:

[http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games](http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games)

That is just a script to change between Xgl and a regular xorg server, just like I said.  I don't want to have to run all of my games and opengl apps from command line and type nonxgl every time.  I also don't want to redo all of my menu items to use nonxgl.  I just want it to work.  So until Xgl can properly use my nvidia card, I can do without it.  I actually have gotten opengl games to work without a workaround, but it still had texture and speed issues.

---

### Post by _simon_ on 2006-08-14
I run my games from menu items so I only put nonXgl in once... 

You could always make a script to call nonXgl /path/to/game

You only need nonXgl for opengl based games. Apps work fine with XGL - even google earth works ok with XGL

---

