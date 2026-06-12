---
title: "Getting a super fast desktop"
date: 2008-04-12
forum: The Cafe
---

### Post by blithen on 2008-04-12
In booting and loading in general.
anyone have tips on what config files to edit?
I'll probably switch to XFCE for my GUI.
And all it's programs for pretty quick loading and running.
But Anymore I can do besides that?

---

### Post by akiratheoni on 2008-04-12
> **blithen said:**
> In booting and loading in general.
anyone have tips on what config files to edit?
I'll probably switch to XFCE for my GUI.
And all it's programs for pretty quick loading and running.
But Anymore I can do besides that?

Config files for what? To install XFCE or to configure it? 

From what I've used of XFCE (i've used it a bit, but not as my main desktop environment on my main computer, just messed around with it on my laptop) there isn't really a lot of config files to edit unless you want to do something like change the color of the panels which involve editing your gtkrc-2.0 file (I think).

If you want a super fast desktop, try a *box like Fluxbox, Blackbox, or Openbox. I hear that Awesomewm, PekWM, IceWM are fast too, although I haven't used either too much.

The only issue with the *boxes and the *wms are that each of them are slightly more difficult to configure because most of them are done through text files rather than GUIs like GNOME and KDE.

---

### Post by Kingsley on 2008-04-12
You could speed up your system by turning off unneeded processes. 

This link has a lot of good information:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by blithen on 2008-04-12
> **akiratheoni said:**
> Config files for what? To install XFCE or to configure it? 

From what I've used of XFCE (i've used it a bit, but not as my main desktop environment on my main computer, just messed around with it on my laptop) there isn't really a lot of config files to edit unless you want to do something like change the color of the panels which involve editing your gtkrc-2.0 file (I think).

If you want a super fast desktop, try a *box like Fluxbox, Blackbox, or Openbox. I hear that Awesomewm, PekWM, IceWM are fast too, although I haven't used either too much.

The only issue with the *boxes and the *wms are that each of them are slightly more difficult to configure because most of them are done through text files rather than GUIs like GNOME and KDE.
I wasn't talking about XFCE config files. It was more of like..system tweaking config files.

---

### Post by myusername on 2008-04-12
this is a very good how to

[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

just be careful

---

### Post by cardinals_fan on 2008-04-13
Use Openbox - you'll never go back...

---

### Post by Calibre on 2008-04-13
If you want super fast go for Arch or Gentoo.

---

### Post by chucky chuckaluck on 2008-04-13
in addition to shutting off processes you don't need (as others have suggested), i found things got faster when i dumped usplash and gdm. my laptop usually boots up in around 15 seconds.

---

### Post by cardinals_fan on 2008-04-13
> **akiratheoni said:**
> 
The only issue with the *boxes and the *wms are that each of them are slightly more difficult to configure because most of them are done through text files rather than GUIs like GNOME and KDE.
But it's worth it, because this makes them both extremely configurable and very portable (if I install a new distro, I just copy over the config files and have all my settings).

---

### Post by zmjjmz on 2008-04-13
You could also drop using gtk all together (if you don't mind ugliness).
Then drop gnome-terminal, use mxrvt (I think that's the name) instead of whatever terminal, ROX for a file manager, screw panels completely and just use twm (or vtwm if you _need_ a virtual desktop), use an old version of Konquerer or Dillo or links2-gui for web browsing, XMMS for music, rtorrent, feh for backgrounds, irssi, Ted (or Abiword if you have bad grammar too) mplayer for movies, tftp, nano, don't even bother with synaptic and just use aptitude, Naim, connect to wireless networks via command line, etc.
DSL and DeLi are light, and so can you!

---

### Post by kerry_s on 2008-04-13
go custom, if you start from the base and install only what you need/use you'll get a much faster system. using simple wm's and light programs really makes a big difference. try different things, see what you like most.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

i prefer debian, so i build mine from a debian base.

---

### Post by Breakage on 2008-04-13
Also if you compile new programs use optimised cflags.

---

### Post by frenchn00b on 2008-04-13
> **blithen said:**
> In booting and loading in general.
anyone have tips on what config files to edit?
I'll probably switch to XFCE for my GUI.
And all it's programs for pretty quick loading and running.
But Anymore I can do besides that?

I run fvwm with gnome-panel; 
but you would get the best results with no gdm/kdm and running autologin 
[http://linuxgazette.net/issue72/chung.html](http://linuxgazette.net/issue72/chung.html)
,
 and with Openbox. Nothing beats openbox. Avoid running processes that you dont use at boot in /etc/rc2.d/ ; no openftp ...

---

### Post by Tundro Walker on 2008-04-13
Man, you Linux folks make things so freakin' complicated.

Look, jst do like the Vista folks do and get a faster computer.    Problem solved!

;)

---

### Post by Breakage on 2008-04-13
> **Tundro Walker said:**
> Man, you Linux folks make things so freakin' complicated.

Look, jst do like the Vista folks do and get a faster computer.    Problem solved!

;)

Linux is for people with brains. If i was on xp and got a new pc just to run vista at the same speed xp was running, where's the logic in that?

---

### Post by kerry_s on 2008-04-13
> **Tundro Walker said:**
> Man, you Linux folks make things so freakin' complicated.

Look, jst do like the Vista folks do and get a faster computer.    Problem solved!

;)

:lolflag:

---

### Post by kerry_s on 2008-04-13
> **Breakage said:**
> Linux is for people with brains. If i was on xp and got a new pc just to run vista at the same speed xp was running, where's the logic in that?

it's a joke, your suppose to have a since of humor to go with your brain.

---

### Post by finferflu on 2008-04-13
> **Calibre said:**
> If you want super fast go for Arch or Gentoo.
+1 for Arch! :D

---

### Post by jacob01 on 2008-04-13
> **Tundro Walker said:**
> Man, you Linux folks make things so freakin' complicated.

Look, jst do like the Vista folks do and get a faster computer.    Problem solved!

;)

lol bute force approach

another one would be just live with it, that one is used by most win users :lolflag:

---

### Post by herbster on 2008-04-13
16 second boot on Arch here, always a flux session. But I reboot once a month so it's no biggie.

---

### Post by RedSquirrel on 2008-04-13
K.Mandla's guide might help when you want to tweak your system a bit:

[http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)

As mentioned above, if you install the base system and build up from there you should get good results. That's what I always do (on Ubuntu, Debian, Arch, ...). 

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Xfce is a pretty nice DE, but I prefer a light window manager instead of a full DE (Openbox is my current favourite).

---

### Post by blithen on 2008-04-27
I've been working on my desktop for awhile now, and It's getting there.
But what's the difference between open and fluxbox?

---

### Post by myusername on 2008-04-28
Everywhere I Have Read Says That Flux Is Better...but I Have Yet To Try Openbox

---

### Post by blithen on 2008-04-28
> **myusername said:**
> Everywhere I Have Read Says That Flux Is Better...but I Have Yet To Try Openbox

Wasn't asking that though. I was asking if there was any distinct differences between the two window managers.

---

### Post by akiratheoni on 2008-04-28
> **cardinals_fan said:**
> But it's worth it, because this makes them both extremely configurable and very portable (if I install a new distro, I just copy over the config files and have all my settings).

Oh, of course it is. It's just not the newb-friendliest thing. But if you can handle text files, then it's completely worth it. If you can't, I suggest you start learning :P

> But what's the difference between open and fluxbox? 

From my experience (I haven't used Fluxbox all that much) fluxbox comes with a panel whereas openbox doesn't. That's the only difference I've seen so I'm sure more Fluxbox-savvy users can help me out here.

Openbox needs to rely on a separate panel. I use pypanel although I used Tint in the past.

---

### Post by kerry_s on 2008-04-28
> **blithen said:**
> Wasn't asking that though. I was asking if there was any distinct differences between the two window managers.

openbox is like fluxbox naked. it only provides a window manager, you pick everything else from the panel to a background setter. other than that no real difference in use.

you should try jwm.

---

### Post by maniacmusician on 2008-04-28
what about blackbox?

---

### Post by blithen on 2008-04-28
> **maniacmusician said:**
> what about blackbox?
:P Another, 'what makes it different' query.

---

### Post by maniacmusician on 2008-04-28
I'm not really too sure. It was a couple of years ago that I messed around with the various WMs, but I never really sat down and used any of them seriously. I always got the impression though, that people didn't like blackbox or just tended to ignore it. I never understood why, because I remember liking it a whole bunch; not for any special reason, but I think it was just pretty easy to use.

Anyways, these are all pretty small packages. Why not install them and try them out? Would probably give you a better overview than forum posts, and faster too.

---

### Post by Jammin80503 on 2008-04-28
Take a look at Fluxbuntu - its a little confusing at first, but very nice and really fast once you get used to it.

---

### Post by chris4585 on 2008-04-28
> **cardinals_fan said:**
> Use Openbox - you'll never go back...

+1 for openbox! its stable and super fast.

Here's a image of my setup.

[http://i29.tinypic.com/4janex.jpg]("http://i29.tinypic.com/4janex.jpg")

---

### Post by urukrama on 2008-04-28
> **blithen said:**
> Wasn't asking that though. I was asking if there was any distinct differences between the two window managers.

Have a look at [this post]("http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/") on my blog. It offers a comparison of Icewm, Fluxbox, Openbox and Pekwm.

My opinion? Though Openbox seems to have less features (no panel, no transparency, no pixmap themes), I believe it actually has a lot more features and options. It is also more actively developped, and new (excellent) features are added with every release. Openbox is the most polished window manager.

---

### Post by insane_alien on 2008-04-28
why don't you just dump the GUI all together? THAT speeds up your system a whole lot. :D

---

### Post by blithen on 2008-04-28
> **insane_alien said:**
> why don't you just dump the GUI all together? THAT speeds up your system a whole lot. :D

:P I've tried, I just can't live without pretty pictures.

---

### Post by blithen on 2008-04-28
> **urukrama said:**
> Have a look at [this post]("http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/") on my blog. It offers a comparison of Icewm, Fluxbox, Openbox and Pekwm.

My opinion? Though Openbox seems to have less features (no panel, no transparency, no pixmap themes), I believe it actually has a lot more features and options. It is also more actively developped, and new (excellent) features are added with every release. Openbox is the most polished window manager.

EXCELLENT work!

---

### Post by herbster on 2008-04-28
I used open for a while and then tried flux, have stuck with it since. I don't know if I can pinpoint what keeps me on flux, I can say the flux toolbar is the best I've used by miles, no comparison for me with pypanel, which I really don't like.

Either of 'em are speedy, though, and will wind up teaching you a lot about configuration, window settings, layouts, etc. just via regular usage.

---

### Post by urukrama on 2008-04-28
> **herbster said:**
> I can say the flux toolbar is the best I've used by miles, no comparison for me with pypanel, which I really don't like.

It's funny. I would say the exact opposite ;-)

> **blithen said:**
> EXCELLENT work!

Thank you.

---

### Post by RedSquirrel on 2008-04-29
One important difference is that Openbox is configured via XML files, whereas Fluxbox uses a custom syntax. Both are fairly easy to learn.

I've noticed on really old hardware that Openbox is a tiny bit faster. On newer computers I don't think anyone would notice a speed difference.

For a panel, I like fbpanel.

As for Blackbox, well, it's not in active development, but some people still use it. I prefer to use software that *is* in active development, but that's just me.


> **urukrama said:**
> Have a look at [this post]("http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/") on my blog. It offers a comparison of Icewm, Fluxbox, Openbox and Pekwm.

Nicely done! :)

I haven't had time to review the entire table, but I did notice one small correction: Fluxbox is written in C++, not C. ;)

---

### Post by urukrama on 2008-04-30
> **RedSquirrel said:**
> Nicely done! :)

I haven't had time to review the entire table, but I did notice one small correction: Fluxbox is written in C++, not C. ;)

Thank you, RedSquirrel. I'll correct that. If you find any more errors, please let me know.

---

### Post by ssam on 2008-04-30
install preload. it speeds up program loading.

---

### Post by herbster on 2008-04-30
> **urukrama said:**
> It's funny. I would say the exact opposite ;-)



Thank you.

Nunca! The flux toolbar is incredible, it's the only toolbar I have used yet that fits my clicking/minimizing/etc habits perfectly. Pypanel is good, just a lil' cousin to flux though.

---

### Post by urukrama on 2008-04-30
> **herbster said:**
> Nunca! The flux toolbar is incredible, it's the only toolbar I have used yet that fits my clicking/minimizing/etc habits perfectly. Pypanel is good, just a lil' cousin to flux though.

You know you can customize pypanel's clicking/minimizing/etc behaviour, right?

---

### Post by herbster on 2008-04-30
Oh of course, I customized the hell out of pypanel. The tray was buggy with certain apps (pidgin/amarok that I can recall) as icons would show/not show sometimes, the toolbar flickered quite a bit, some others I'm forgetting at the moment.

Hey, to each his own :)

---

### Post by akiratheoni on 2008-04-30
> **herbster said:**
> Oh of course, I customized the hell out of pypanel. The tray was buggy with certain apps (pidgin/amarok that I can recall) as icons would show/not show sometimes, the toolbar flickered quite a bit, some others I'm forgetting at the moment.

Hey, to each his own :)

For me, pypanel only flickers when Firefox finishes a download and the little 'all downloads have finished' tooltip thingy pops up. I haven't had any issues with the tray with Pidgin or Amarok though.

---

### Post by seatex on 2008-04-30
Something else to suggest, especially for those on laptops...

Make sure you have the latest BIOS installed and check your settings.  The BIOS in my Gateway T7200 lappy had some like...

OS - Win 2k, XP/Vista, Other (UNIX & LINUX)

---

