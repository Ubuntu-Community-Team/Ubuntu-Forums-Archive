---
title: "suggest some lightweight alternatives to well known programs"
date: 2008-01-24
forum: The Cafe
---

### Post by chris4585 on 2008-01-24
well, i'd like to know what other people use for example, instaed of pidgin for instance can be replaced by SIM (small instant messanger?) anything is appreciated.

---

### Post by fuscia on 2008-01-24
centerim is an instant message thing for the terminal.

---

### Post by Lord Illidan on 2008-01-24
Firefox -> Epiphany or Dillo
Amarok -> mpd


Basically, fire up Damn Small Linux or Zenwalk and see what kind of applications they use.

---

### Post by Mateo on 2008-01-24
Epiphany isn't any more lightweight than Firefox.  That's a myth based on the fact that Epiphany is more simplistic (and I'm a Epiphany user).  They both use Gecko and thus use about the same amount of memory. Sure, Firefox is heavier when you add a ton of extensions, but it's not heavier by itself.

---

### Post by jrusso2 on 2008-01-24
Have a look at the default applications on the damn small linux distro.

There are many light weight replacements on there for regular programs.

[http://damnsmalllinux.org/applications.html](http://damnsmalllinux.org/applications.html)

---

### Post by Lostincyberspace on 2008-01-24
> **jrusso2 said:**
> Have a look at the default applications on the damn small linux distro.

There are many light weight replacements on there for regular programs.

[http://damnsmalllinux.org/applications.html](http://damnsmalllinux.org/applications.html)
another amarok one - pytone a really good cli based player.

---

### Post by Mazza558 on 2008-01-24
Nautilus can be replaced with Thunar, one of my favourite Filemanagers.

---

### Post by chris4585 on 2008-01-24
thunar is good for a lightweight file manager, but i like pcmanfm a bit

---

### Post by LaRoza on 2008-01-24
Abiword for word processing instead of OO.org

Lynx instead of Firefox/Opera

---

### Post by urukrama on 2008-01-24
Feh as an image viewer, Thunar as a file manager, mpd as a music player, GMPC as a light *graphical* frontend for mpd, Openbox as a window manager.

---

### Post by chris4585 on 2008-01-24
> **LaRoza said:**
> Abiword for word processing instead of OO.org

Lynx instead of Firefox/Opera


i found lynx quite interesting

---

### Post by chris4585 on 2008-01-24
> **fuscia said:**
> centerim is an instant message thing for the terminal.

for some reason i couldnt stay connected with this program :/

---

### Post by Lord Illidan on 2008-01-24
Lynx is a bit hardcore, heh.

rtorrent can be used to download torrents from cli.

---

### Post by chris4585 on 2008-01-24
> **urukrama said:**
> Feh as an image viewer, Thunar as a file manager, mpd as a music player, GMPC as a light *graphical* frontend for mpd, Openbox as a window manager.

i tried feh not really what i'm looking for, so far the only thing that does what i want is gwenview and the only problem with that is that it takes a bit for it to load up, and i'm using fvwm-crystal for my wm

---

### Post by chris4585 on 2008-01-24
i've tried moc before and it froze while trying to load my playlist, which was huge, and for a music player i now use quod libet, not very lightweight but i like it, it does what i want it to do

---

### Post by K.Mandla on 2008-01-24
gimp -- mtpaint
gqview -- mirage
firefox -- kazehakase
nautilus -- pcmanfm, emelfm2 or xfe
evolution -- sylpheed
evince -- epdfview

And so forth. Basically anything that avoids Gnome or can run in a terminal is a great choice. Use the [packages search page]("http://packages.ubuntu.com") to check dependencies and try them out as you find them.

---

### Post by urukrama on 2008-01-24
> **chris4585 said:**
> i tried feh not really what i'm looking for, so far the only thing that does what i want is gwenview and the only problem with that is that it takes a bit for it to load up, and i'm using fvwm-crystal for my wm

Feh is great if you want to view a single image file. It is the fastest image viewer I've used so far, and it has quite a lot of options you can use -- see the man page of feh (man feh).

If you want a slightly more sophisticated image viewer, try gpicview. It is quite light.

EDIT: and I second epdfview.

---

### Post by chris4585 on 2008-01-24
i liked K.Mandle's list, and feh seems very good for a single image viewer, i'm searching for something that does pretty much gwenview but faster, the scroll bar button switches pictures, i like this feature, and the fit to window, fit to hight, fit to width are the other things i like from gwenview

---

### Post by K.Mandla on 2008-01-24
Some more, torn out of a guide some clown wrote and posted on a blog. :D

> **X-based**

The default X environment in Ubuntu has a string of included "software" that might be of use to you. They're generally very, very ugly, but can work in a pinch, or might offer some short amusement.

terminal emulators
	xterm

desktop utilities
	xbiff
	xclipboard
	xcutsel
	xmag
	xmessage
	xmore
	xsetroot

font utilities
	xfd
	xfontsel

gimmicks
	xeyes
	xgc
	xlogo

image tools
	xwd
	xwud

system utilities
	xconsole
	xload
	xset
	xsm

accessories
	xcalc
	xclock

There are more available in the repositories, if you're a big X-based application fan. Check the man pages for details; some can be a bit cryptic, but others are very useful.

**GTK1.2-based**

GTK1.2 has lighter requirements and is probably better on sub-400Mhz hardware. These programs are generally uglier (or public opinion says they're uglier), but much faster than GTK2. It's a compromise between the better appearance offered by GTK2, and the stark efficiency of X-based or console applications. 

Don't discount them though: The list includes some venerable, masterful Linux software -- like the classic XMMS music player and the wicked-fast Dillo browser. Development may have paused on some of these, but many, many people still put them to use.

e-mail clients
	sylpheed-gtk1

terminal emulators
	aterm

music players
	xmms

image viewers
	feh (not really GTK1.2-based I guess, but around there)
	xzgv

pdf viewers
	xpdf

file managers
	emelfm
	xfe (actually FOX-based, but of a similar caliber and likewise rather ugly)

Don't forget to install gtk-theme-switch and a few GTK engines, which will allow you to use a much better looking theme than the Raleigh default. Yuck.

**GTK2-based**

GTK2 is a little more demanding on your video system, but offers a much more attractive appearance. And since most modern machines can handle the workload, it tends to be a little more popular among developers. Remember that just because a program uses GTK2 doesn't mean it can't run on older machines. Some of these, such as mtpaint or xpad, are sufficiently light to work well on very old hardware too.

e-mail clients
	sylpheed

terminal emulators
	rxvt-unicode
	mrxvt
	Sakura*

music players
	audacious

file managers
	emelfm2*
	pcmanfm
	rox-filer

chat clients
	xchat

image viewers
	mirage
	gpicview*
	gqview

editors
	leafpad
	geany

system utilities
	synaptic

music tag editors
	easytag

torrent clients
	deluge
	transmission

graphics
	gimp
	mtpaint

office applications
	abiword
	gnumeric-gtk
	epdfview
	inkscape
	zim

accessories
	galculator
	xpad

*These programs are not in the Gutsy repositories, but are installable as deb files from outside sources -- sometimes alternative renditions of Ubuntu, sometimes collections of software compiled for Ubuntu but hosted elsewhere.

Don't forget to install gtk-theme-switch and a few GTK engines, which will allow you to use a much better looking theme than the Raleigh default. Double yuck. If you prefer, you can add gtk-chtheme, which is a vast improvment over switch2, and is in the repositories for Gutsy.

---

### Post by Incense on 2008-01-24
That's an INCREDIBLE list! I'm going to have to try out some of those! Thanks for sharing!

---

### Post by chris4585 on 2008-01-24
indeed thanks K.Mandla

---

### Post by igknighted on 2008-01-24
No one has mentioned Finch for a text-based IM client?  It's built on top of libpurple, so its essentially a text based version of pidgin... very nice.

---

### Post by chris4585 on 2008-01-24
> **igknighted said:**
> No one has mentioned Finch for a text-based IM client?  It's built on top of libpurple, so its essentially a text based version of pidgin... very nice.

i just tried finch, and its awesome! i dont even like pigin that much but this is amazing

---

### Post by chris4585 on 2008-01-24
anyone know of a torrent package thats lightweight? i've downloaded transmission but not sure if thats what i want, i'm trying to come up with a lightweight system

---

### Post by p_quarles on 2008-01-25
> **chris4585 said:**
> anyone know of a torrent package thats lightweight? i've downloaded transmission but not sure if thats what i want, i'm trying to come up with a lightweight system
rtorrent

---

### Post by urukrama on 2008-01-25
> **p_quarles said:**
> rtorrent

+1. See [here]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") how to use it.

For more applications, see also [this]("http://ubuntuforums.org/showthread.php?t=447007") thread and [this]("http://ubuntuforums.org/showpost.php?p=2862243&postcount=5") post.

---

### Post by RomeReactor on 2008-01-25
> **chris4585 said:**
> anyone know of a torrent package thats lightweight? i've downloaded transmission but not sure if thats what i want, i'm trying to come up with a lightweight system

You could also use the default BitTorrent client from the terminal; to download a single file:
```
btdownloadcurses /PATH/TO/FILE
```
Where FILE is the **.torrent** file to start the download. To start multiple downloads from .torrent files located in a folder called "TORRENTS":
```
btlaunchmanycurses /PATH/TO/TORRENTS
```
Note that by default, the terminal opens in your home folder and that's where your downloads are going to be saved; if you want to save the files elsewhere, navigate to the desired location before starting. Both methods allow for resuming partial downloads; just remember that if you chose another destination for the downloads, you must navigate there before resuming. To resume the download, just issue the command again.

---

### Post by jeffus_il on 2008-01-25
Quod Libet is probably the lightest full featured music player.

---

### Post by urukrama on 2008-01-25
> **jeffus_il said:**
> Quod Libet is probably the lightest full featured music player.

Quod Libet is nice, but if you want things light try MPD + GMPC for a graphical player, or MPD + NCMPC for a command-line player.

---

### Post by Lord Illidan on 2008-01-25
I took the liberty of fixing a typo in the title.

---

### Post by Havoc on 2008-01-25
Konqueror/Embedded as a browser. Either one of the old snapshots which use QT2 (Latest snapshot with QT2 is [HERE](http://developer.kde.org/~hausmann/snapshots/Attic/konqueror-embedded-snapshot-20030705.tar.gz)) or newer snapshots which require QT3. Compiling these from source is a pain in the ***, but it's the fastest CSS/Javascript compliant web-browser out there (at least the QT2 version, which I've tested).

Sylpheed 1.0.6 is probably the best e-mail client using gtk-1.2.

Xwc (Xwincommander), on which xfe is based upon is a great filemanager.

Finch is great these days. IM for the console, it comes with pidgin.

The "latest" release of Abiword with GTK-1.2 is 1.0.7. You'll have to build it with gcc-3.x though.

---

### Post by chris4585 on 2008-01-25
> **jeffus_il said:**
> Quod Libet is probably the lightest full featured music player.

+1 i use quod libet, it handles my library of about 19,000 files pretty smoothly

thanks all for all the info, and links, sorry i didnt take the time to search, i havent had time to try all of these applications but i will eventually

---

### Post by ynnhoj on 2008-01-25
[bitlbee](http://www.bitlbee.org/) for instant messaging; if you tend to have an irc application open, it makes perfect sense.  i use bitlbee with weechat -- recently switched back from irssi, which i was using for a while -- and it's great.  finch, as others have mentioned, is nice too.. but finch is a bit clunky to me.

---

### Post by chris4585 on 2008-01-27
what about a screen capture program? i dont like the one that comes with the usual gnome install, and ksnapshot might be a bit slow at times, anything for this?

---

### Post by p_quarles on 2008-01-27
> **chris4585 said:**
> what about a screen capture program? i dont like the one that comes with the usual gnome install, and ksnapshot might be a bit slow at times, anything for this?
scrot

A CLI based screen-capture app.

---

### Post by chris4585 on 2008-01-27
ty works nicely

---

### Post by chris4585 on 2008-01-27
balsa or sylpheed for an e-mail client? which offers the most options and being the lightest, i'm heard balsa is lighter than sylpheed, but i'm not an e-mail person i do need to know this though

---

### Post by redrider on 2009-01-20
Others will probably be falling into this thread while researching openbox and ubuntu, just as I did. I was looking for instructions about setting background with feh. I got just what I needed here.

About light and fast apps, I would suggest 2 browsers:

opera -- for the full browser experience when you need it. It may not be that light, but it's a lot faster than firefox (especially when you consider that it already has built-in many of the basic usefulness that needs to be added on to firefox. I install the .deb file downloaded directly from Opera's website.

links2 -- not just links, but links2 from the repositories. Links 2 should automatically run in graphics mode when called from the standard menus, or if you call it from a terminal, links2 -g. I've tried pretty much all the light text-based browsers, and I like links2 the most primarily because it shows graphics and renders pages very close to normal when in graphics mode.

I love openbox, by the way. I find that it has the best combination of minimalness and functionality. It also works great with any gnome programs you might need (for example, I have to run gnome network manager and nm-applet in order to get wifi on my laptop.

One more suggestion... if you want a fairly light setup that gets you up and running almost immediately with a minimum of manual setup, install xubuntu first (not ubuntu), and then install openbox. Both xfce4 itself, and openbox run lightning fast on my 1.8 Ghz AMD Turion with 1 gig of ram (shared with the ATI graphics card).

---

