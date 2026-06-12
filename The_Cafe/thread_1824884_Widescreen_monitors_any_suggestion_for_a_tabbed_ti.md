---
title: "Widescreen monitors: any suggestion for a tabbed tiled wm?"
date: 2011-08-14
forum: The Cafe
---

### Post by keithpeter on 2011-08-14
Hello All

Might be time for a new monitor soon (backlight uneven and getting dimmer).

Good value LCDs are all wide-screen now, around 1920 by 1080 being common in the 23/24 inch size range. We have those at work and I never seem to use the right hand part of the screen.

What i'd like is a wide region on the left, say 1200 pixels and full height. Then a 'gutter' on the right that could be split into two (or more) small 700 by 500 regions.

Within each region, it would be possible to load and maximise several applications. EG the main region could have Firefox / LibreOffice apps. Side panels could be mail/music or text editors &c. The various applications would be tabbed within their regions, and would load into the appropriate region on start up.

Any ideas on how this could be achieved? A combination tiled and tabbed window manager? Running inside Gnome or with XCFE or at least GDM for services? 

This is a PC with wired network. Thanks.

---

### Post by keithpeter on 2011-08-15
OK, I'm bumping this as I have discovered bluetile

[http://www.bluetile.org/](http://www.bluetile.org/)

and have it installed along with Gnome 2-something on a Debian Squeeze 'play' partition. Just need to learn the keyboard shortcuts!

[http://dhost.info/devnull/new-monitor-browser.jpg](http://dhost.info/devnull/new-monitor-browser.jpg)

is what it looks like. Any other suggestions welcome. I've tried dwm and awesome, may spend more time working out how awesome works as it seems a little 'unstable' to me.

---

### Post by PhillyPhil on 2011-08-15
I don't know how good it is but X-Tile will do what you want..

---

### Post by 3Miro on 2011-08-15
Something simple that you can try:

With XFWM4 you can specify an area in pixels to the left or right (also top/bottom) of your screen that maximized windows will not cover (also regular windows will not cover by default). You can specify such area of say 700 pixels so that the main windows (Firefox and LO) will not cover. Then you can manually put whatever windows you want in the remaining 700 pixels and you can tell them to show on all screens (so you have it on all workspaces).

Notice that on the picture Firefox is maximized, although I couldn't make it reserve more than 1/4 of the size of the screen.

---

### Post by aeiah on 2011-08-15
i think scrotwm does tabbing as well as tiling. tabbing fuctionality is probably gonna be your limiting factor here.

---

### Post by keithpeter on 2011-08-15
@3Miro Thanks very much, I'll try that one out soon

@aeiah I'm working my way through the tile wms one by one. Thanks for the suggestion.

@PhillyPhil: anything from the author of CherryTree will be interesting: I'll try it out in a fresh Gnome session, thanks

Bluetile seems a good compromise right now, but I know its not the final answer.

---

### Post by BrokenKingpin on 2011-08-16
I have also been interested in a tiling WM/DE. I have a 24" monitor running Xfce, and having tiling support would be awesome.

X-Tile is just an applet that will arrange your windows automatically for you, but not even close to a tiling WM.

Bluetile is really cool, but it is only for Gnome2. If I could get a tiling WM integrated into Xfce that would be awesome.

I have tried tiling WMs in the past and liked them, but I prefer a full DE that has tiling support. Apparently KDE has decent true tiling support, unfortunately I just don't like the rest of KDE lol.

@3Miro... that looks pretty cool, I might have to give that a try. It is not true tiling, but could give me enough of what I am looking for.

---

### Post by aeiah on 2011-08-16
i think pytyle works with openbox, if you dont mind jumping away slightly from xfce. xmonad, probably the most popular tiling wm, can work with gnome2 and xfce

---

### Post by aeiah on 2011-08-16
just to add: i use openbox, and have keypad binds for manual tiling functionality. i dont always need things to tile, and so i find this the most efficient way of doing things. i explain it a bit here:
[http://ubuntuforums.org/showpost.php?p=10515916&postcount=18](http://ubuntuforums.org/showpost.php?p=10515916&postcount=18)

as well as resizing+moving to 50% height/width, i also have key combos to resize+move horizontally at 66%/33% so i can have small ones to the right and one (or two) larger windows on the left.

---

### Post by keithpeter on 2011-08-16
Hello All

Thanks for these suggestions, looks like I'm going to have to try xmonad as bluetile is based/fits in with that more comprehensive system. But xmonad is a half gigabyte install on Debian Squeeze - I have no idea what they have got in there.

I'd like to have what bluetile does with XFCE as well by the way.

---

### Post by BrokenKingpin on 2011-08-16
Bluetile is basically Gnome with xmonad as the window manager. As aeiah stated above, you can apparently use xmonad with Xfce, but will requires a bit of configuration and setup work.

[http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE)

---

### Post by red_Marvin on 2011-08-16
I am personally using i3 and can recommend it. It is a manual tiler,
so windows are not fit into a layout automatically as in (most uses of)
dwm/awesome/xmonad, but instead a new window is opened in the currently
selected "cell", and then you can move it to adjacent cells creating new
ones if there is none.

---

### Post by FreeTheBee on 2011-08-16
> **aeiah said:**
> i think pytyle works with openbox, if you dont mind jumping away slightly from xfce.

Pytyle works with xfce as well.

---

### Post by keithpeter on 2011-08-16
> **BrokenKingpin said:**
> Bluetile is basically Gnome with xmonad as the window manager. As aeiah stated above, you can apparently use xmonad with Xfce, but will requires a bit of configuration and setup work.

[http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE)

Thanks for this, currently I'm just using Gnome 2 on Debian Squeeze and I used gconf-editor to replace gnome-wm with xmonad. Just a minimal xmonad.hs file from

[http://upsilon.cc/~zack/blog/posts/2009/04/xmonad_+_gnome_on_Debian/](http://upsilon.cc/~zack/blog/posts/2009/04/xmonad_+_gnome_on_Debian/)

and now I'm trying to work out how to add this GIMP layout

[http://nathanhowell.net/2009/03/08/xmonad-and-the-gimp/](http://nathanhowell.net/2009/03/08/xmonad-and-the-gimp/)

which means learning the rudiments of the language I suppose :o

Its all rather nice, much less messing about with resizing windows

---

### Post by Random_Dude on 2011-08-16
I've tried some tiled window managers and my favourite ones are Awesome WM and WMFS.

Awesome WM is really great, but in order to configure it, you have to know Lua (which is a pain in the ***). WMFS has some easy to use config files, but the bar is not as good as awesome's IMHO.

Good luck in finding a WM that suits you.
I love tiled window managers, but some of their aspects are not very user-friendly. Which prevents me from using them exclusively. :(

I wish someone would invest some time in making them more accessible.

Cheers :cool:

---

### Post by keithpeter on 2011-08-17
> **Random_Dude said:**
> Good luck in finding a WM that suits you.
I love tiled window managers, but some of their aspects are not very user-friendly. Which prevents me from using them exclusively. :(

I wish someone would invest some time in making them more accessible.

I'm keeping Gnome and Bluetile around as my 'security blanket'. It was quite easy to get going, and by choosing the 'stack' layout you can revert to normal window chaos at any time. I'd say that combination was pretty accessible. When I installed it on Debian Squeeze, I ended up with two log in options, Gnome and Gnome + Bluetile.

Thanks to all who have contributed, I'll be trying xmonad with xfce later on tonight. I think xmonad within a desktop environment is the way to go for me despite the humungous download.

---

### Post by mips on 2012-02-26
[http://askubuntu.com/questions/103456/automatically-size-windows-using-xfce-like-in-gnome](http://askubuntu.com/questions/103456/automatically-size-windows-using-xfce-like-in-gnome)

Just installed this but not sure how to use it...

---

