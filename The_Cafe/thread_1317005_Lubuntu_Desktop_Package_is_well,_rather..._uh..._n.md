---
title: "Lubuntu Desktop Package is well, rather... uh... not what the screens showed"
date: 2009-11-06
forum: The Cafe
---

### Post by coldReactive on 2009-11-06
So, I decided to install the lubuntu-desktop package with the mini.iso. Everything was fine, until I got to the desktop.

A. Lubuntu uses gnome-panel, not lxpanel by default
B. Lubuntu does not come with ANY wallpapers (including that nice LXDE wallpaper.
C. Lubuntu installs metacity, gtk, qt but doesn't install any of the themes (IE: Human Metacity, Clearlooks, etc. Just the gtk and qt base themes.)
D. Lubuntu installs synaptic only for firefox, and removing Firefox and firefox 3.5 will make synaptic be in the auto-remove list, sadly.
E. wicd will give you a nice error when you first configure it in the setup portion of the installation back in the minimal install. Don't fret though, it's somehow normal. Just select your users that you want added to netdev, and it'll add netdev and the users basically at the end.
F. wicd tries to auto-connect from the right-click menu, so if you have a security-enabled network, left click the wicd icon instead and click your network's connect button on the wicd dialog.
G. Pidgin is installed by default (just like xubuntu) YAY
H. nautilis is installed even though pcman is installed.
I. no splash screen, have to install xsplash manually (this will give you the ubuntu xsplash and ubuntu gdm theme.)
J. leafpad is the default text editor. Yay
K. As with all ubuntu distros, Firefox is the default. I suggest removing it and installing midori. BUT REMEMBER, as I said before, synaptic will be in the autoremove list when you do this! DO NOT autoremove blindly!
L. smplayer and mplayer are the default media players. Unfortunately, they don't play files too well on lubuntu for some reason. I suggest totem, since you already have tons of gnome stuff in your lubuntu.
M. Lubuntu installs (as I said above) lots and lots and lots of gnome, kde and xfce stuff.
N. Pulseaudio is installed. YOU CANNOT INSTALL ESOUND, IT WILL NOT WORK AS OF THIS RELEASE OF UBUNTU (esound cannot be started at all, esd will hang terminal.)
O. Transmission is installed (I suggest deluge.)
P. The fast user switch applet will crash as soon as you login. Remove it.

If you're running a ThinkPad T41 like me, your resolution will be at 1400 x 1050, switching it lower, may cause you not to be able to login again on gdm. Yeah, there's... there's my testimonial about the lubuntu package.

---

### Post by RiceMonster on 2009-11-06
> **coldReactive said:**
> B. Lubuntu does not come with ANY wallpapers (including that nice LXDE wallpaper.

Download some. 

> I. no splash screen, have to install xsplash manually (this will give you the ubuntu xsplash and ubuntu gdm theme.)

Who cares? How much time do you spend watching your boot screen?

> L. smplayer and mplayer are the default media players. Unfortunately, they don't play files too well on lubuntu for some reason. I suggest totem, since you already have tons of gnome stuff in your lubuntu.

So install totem.

> O. Transmission is installed (I suggest deluge.)

So install deluge.

---

### Post by coldReactive on 2009-11-06
> **RiceMonster said:**
> <snip>

Those yays were not sarcastic actually.

Also added:

P. The fast user switch applet will crash as soon as you login. Remove it.

---

### Post by cariboo on 2009-11-06
Have you passed your complaints on to the developers?

---

### Post by Warpnow on 2009-11-06
The presence of anything gnome or kde in lubuntu-desktop seems to me to make it pointless.

---

### Post by Grifulkin on 2009-11-06
The fact that anything gnome or kde is in the lubuntu-desktop saddens me, I thought the developers would keep it, I don't know how it was supposed to be, LXDE.  Not LXDE, gnome edition.

---

### Post by Sealbhach on 2009-11-06
> **coldReactive said:**
> 
D. Lubuntu installs synaptic only for firefox, and removing Firefox and firefox 3.5 will make synaptic be in the auto-remove list, sadly.


That is weird, I presume that's just a mistake?

.

---

### Post by coldReactive on 2009-11-06
> **cariboo907 said:**
> Have you passed your complaints on to the developers?

How and where do I get their ears?

---

### Post by snowpine on 2009-11-06
> **Grifulkin said:**
> The fact that anything gnome or kde is in the lubuntu-desktop saddens me, I thought the developers would keep it, I don't know how it was supposed to be, LXDE.  Not LXDE, gnome edition.

But if all you want is "vanilla" LXDE, why not just 'sudo apt-get install lxde'? Presumably (when it is released for 10.04) Lubuntu is going to be similar to Xubuntu, which is not "plain" Xfce at all.

---

### Post by whoop on 2009-11-06
> **Warpnow said:**
> The presence of anything gnome or kde in lubuntu-desktop seems to me to make it pointless.

I agree. Xubuntu is getting too bloated/heavy for some old machines I am maintaining so I was thinking about installing Lubuntu on them (when/if it matures a bit).
If they start bloating Lubuntu with stuff this will completely make it useless.

---

### Post by cariboo on 2009-11-06
There is plenty of contact info [here]("https://launchpad.net/~lubuntu-desktop")

---

### Post by earthpigg on 2009-11-06
> A. Lubuntu uses gnome-panel, not lxpanel by default
try installing a display manager before you install lubuntu-desktop. avoid gdm, which depends on... well, essentially, it depends on gnome.

> E. wicd will give you a nice error when you first configure it in the setup portion of the installation back in the minimal install. Don't fret though, it's somehow normal. Just select your users that you want added to netdev, and it'll add netdev and the users basically at the end.

or install/use NetworkManager and nm-applet.
```
sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/nm-applet.desktop 
```
[source]("http://sites.google.com/site/masonux/home/notes-to-myself") on that command.

> H. nautilis is installed even though pcman is installed.
see above about the new gdm and gnome.

> M. Lubuntu installs (as I said above) lots and lots and lots of gnome, kde and xfce stuff.
yup, annoying.



im not a fan of the way the lubuntu-desktop metapackage currently is. keep in mind it is not considered stable yet. iirc, the version number is 0.7 or something?

this is where my shameless self-promotion comes in...
|
|
|
(no 9.10 release yet, though. sorry. workin on it.)
|
|
|
\/

---

### Post by Tibuda on 2009-11-06
> **coldReactive said:**
> C. Lubuntu installs metacity, gtk, qt but doesn't install any of the themes (IE: Human **Metacity**, Clearlooks, etc. Just the gtk and qt base themes.)

LXDE uses Openbox as a window manager by default, not Metacity or Compiz, so you won't be able to use Metacity themes. But I agree it would be good for Lubuntu to have some extra Gtk+ themes available.

---

### Post by earthpigg on 2009-11-06
> **danielrmt said:**
> LXDE uses Openbox as a window manager, not Metacity or Compiz, so you won't be able to use Metacity themes. But I agree it would be good for Lubuntu to have some extra Gtk+ themes available.

ubuntu did a lot of things i find perplexing to the lxde metapackage (not lubuntu-desktop, but lxde).

differences between lxde in 9.04 and 9.10:

-the got rid of all the themes and desktop backgrounds.
-some silly stuff regarding depends.
-obconf seems... wierd. only works as root sometimes. no idea what the deal with that is.
-other random stuff i havent taken notes on as well as i should.

9.04 had a better implementation of lxde than what is in the 9.10 repos. in my opinion.

im not going to report it, though, because a lot of it feels... by design? intentional? i dunno. the hypothetical *why* behind some of this stuff is absolutely perplexing & discouraging me from directly advocating change via bug reports, etc. it would be swimming against a current, the flow of which i have no understanding of - i'd much rather just swim in my own little stream ***with*** the current: im going attempt to fix it (probably involving making my own metapackage), clearly document how and what i did, and release Masonux 9.10. :D

middlestream (ubuntu or debian testing... none of the problems are all the way upstream to LXDE) is more than welcome to look at what i did and undo whatever meddling they did with the lxde-related metapackages.

---

### Post by sledge73 on 2009-11-06
why don't you try to roll your own 

sudo apt-get install --without-recommends lxde

then you can add whatever you want

---

### Post by earthpigg on 2009-11-06
> **sledge73 said:**
> why don't you try to roll your own 

sudo apt-get install --without-recommends lxde

then you can add whatever you want

im all over it, dude :D see above. as soon as remastersys learns to work with grub2. or, maybe ill say "screw it", use grub legacy, and cut a release sooner.

i'd just hate to make a grub legacy based release and then have remastersys support for grub2 come out the next day...

---

### Post by epp on 2009-11-08
> **coldReactive said:**
> How and where do I get their ears?

You can also try the [LXDE Forum](http://forum.lxde.org/). 

Hope this helps.

---

