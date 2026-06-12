---
title: "uberlight WM's"
date: 2007-12-27
forum: The Cafe
---

### Post by bonzodog on 2007-12-27
I have been looking at the really lightweight WM's recently, after having used openbox for over a year now.

The 4 I see that really appeal to me are:

dwm
wmii
Awesome WM
XMonad

Out of these, which one would people say is the best -- I know that they are all kind of related to each other (dwm is a hack of wmii, awesome is a hack of dwm). XMonad stands alone from this however.

Also, do any of these support gtk theming on apps like firefox?

---

### Post by fuscia on 2007-12-27
dwm and wmii both support gtk theming(sp?). didn't try awesome long enough (kind of annoyed me) and i only tried xmonad for a brief moment, a month or so ago. i used dwm for a while and then switched to wmii, which i'm loving.

---

### Post by jseiser on 2008-01-25
i thikn xmonad is just dwm rewrote in haskell, and then it became more configurable then dwm and allows configuration on the fly.  Dont know if that helps :)

---

### Post by Havoc on 2008-01-25
dwm for those that want just the *very* basic things from their WMs. I like dwm and use it a lot. I find it very usable and well thought-out.

wmii is pretty much the same as dwm, but it provides extensive facilities for customisation through scripting provided by 9p and all those Plan 9 stuff. :D

---

### Post by ~LoKe on 2008-01-25
Awesome allows you to reload your config without restarting the xserver, just need to press mod4+ctrl+r.  It also has excellent support for mutli-display.  Awesome 2.1 allows you to have as many windgets in the status bar as you want, and has two more layout styles than DWM.

---

### Post by shearn89 on 2008-01-26
+1 for awesome.

Haven't tried xmonad - awesome is really good though. Perfect if you don't need eye candy, reconfigurable on-the-fly, gtk support, can get "conky-like" statusbar widgets...

---

### Post by ynnhoj on 2008-01-26
i'm a big fan of dwm, so i would tend to say it's the best.  awesome is probably more user-friendly to some people (i prefer the simplicity of plain old dwm, though).

i like aspects of wmii and xmonad, but there are some turn-offs; for wmii it's the plan9 stuff, and for xmonad it's haskell :P.  oh, you might also want to consider ion3.  it's actually pretty nice if you can get over the awful lua config files, and the fact that the developer is a bit of a tyrant (but that's another discussion altogether).

one more window manager to throw into the hat: [evilwm](http://www.6809.org.uk/evilwm/).  evilwm is super simple.  if you give it a try, read the man page (or the useage section on the above link) to make sure you know how to open a terminal and stuff.  most of the configuration is done with whatever command-line options you use when you start evilwm, so take note of them too :)

oh, and have you given ratpoison a fair try?  it's pretty solid too.

---

### Post by Mateo on 2008-01-26
it depends what you're looking for.  If you want a true tiling wm you're better off going with dwm or wmii.  Both are quite good.  However, I've noticed a lot of people here that use these windows managers without using tiling.  To me that defeats the purpose of a tiling windows manager, you might as well just use fluxbox, but to each his own I guess.  For a more full featured version, xmonad stands alone.

---

### Post by Gigamo on 2008-01-26
> **Mateo said:**
> it depends what you're looking for.  If you want a true tiling wm you're better off going with dwm or wmii.  Both are quite good.  However, I've noticed a lot of people here that use these windows managers without using tiling.  To me that defeats the purpose of a tiling windows manager, you might as well just use fluxbox, but to each his own I guess.  For a more full featured version, xmonad stands alone.

When I started using awesome I was using floating layouts almost everywhere. However, the tiling layout is starting to grow on me. I don't think its possible to switch to a tiling mode permanently when you've been used to floating desktops for YEARS. :)

After using it more, I see myself using tiling layouts way more often.

---

### Post by ynnhoj on 2008-01-26
> **Gigamo said:**
> When I started using awesome I was using floating layouts almost everywhere. However, the tiling layout is starting to grow on me. I don't think its possible to switch to a tiling mode permanently when you've been used to floating desktops for YEARS. :)

i don't think there's any sense in switching to a tiling window manager if you find that you prefer a floating layout.  that said, it's still good to experiment!  when i first tried wmii and dwm, it was, more or less, just for the hell of it (if anything, i figured i'd be an openbox user until the end :)) but i really embraced the tiling layout.  even though i've been tinkering with evilwm lately, i still like dwm best.

it's also unfortunate that some applications don't work well at all in tiling mode..

---

### Post by urukrama on 2008-01-27
> **ynnhoj said:**
> if anything, i figured i'd be an openbox user until the end

Deep down, everyone is an Openbox user. There are only those that recognise that, and those that don't :p :-s

---

### Post by shearn89 on 2008-01-27
> **urukrama said:**
> Deep down, everyone is an Openbox user. There are only those that recognise that, and those that don't :p :-s
haha... i tried openbox briefly about a week ago in order to check out a pypanel config, but couldn't see the point of staying - everything i could do in openbox i could do in awesome... OB is still installed though!

---

### Post by fuscia on 2008-01-27
> **urukrama said:**
> Deep down, everyone is an Openbox user. There are only those that recognise that, and those that don't :p :-s

weird! i thought everyone was a wmii user, deep down.

---

### Post by urukrama on 2008-01-27
> **fuscia said:**
> weird! i thought everyone was a wmii user, deep down.

You have to go a little deeper still.

---

### Post by Mateo on 2008-01-27
what are the advantages of openbox over fluxbox?  Aren't they more or less the same, except that openbox doesn't do window docking?

---

### Post by fuscia on 2008-01-27
> **urukrama said:**
> You have to go a little deeper still.

hey, i know! let's start a wmii vs. openbox flame war. (i bet that one hasn't been done yet.)

---

### Post by Gigamo on 2008-01-27
OpenBox is lighter than fluxbox , and has very nice obconf/obmenu apps.

---

### Post by sujoy on 2008-01-27
> **fuscia said:**
> weird! i thought everyone was a wmii user, deep down.

any good wiki or such for setting up wmii, with a minimal ubuntu or arch setup?

---

### Post by urukrama on 2008-01-27
> **fuscia said:**
> hey, i know! let's start a wmii vs. openbox flame war. (i bet that one hasn't been done yet.)

Sorry, I think I'll spare you the fun.

My praise of Openbox was an expression of love, and hence not to be taken literally. 

I've never felt comfortable in tiling window managers, though. I've tried ratpoison, wmii and dwm, but I always return to Openbox. The main reason is that I keep most of my most frequently used apps (Opera, OpenOffice) maximized, and that sort of goes against tiling wm (or do I totally not understand how tiling wms work?).

---

### Post by ynnhoj on 2008-01-27
> **sujoy said:**
> any good wiki or such for setting up wmii, with a minimal ubuntu or arch setup?
i'm probably over-simplifying, but...
[list][*]install base system
[*]install & configure x
[*]pacman --sync wmii (or sudo aptitude install wmii, as the case may be..)
[*]add "exec wmii" to the end of yer ~/.xinitrc and then startx
[*]press alt + enter to open up a terminal, and then read wmii's manual page from that terminal ("man wmii")[/list]

:D


@ uru: maximized apps don't necessarily go against the idea of tiling window managers; if you want certain applications to be full-screen you can give them a different tag.  or in wmii, you can use max- or stack-mode.

---

### Post by fuscia on 2008-01-27
> **urukrama said:**
> Sorry, I think I'll spare you the fun.

My praise of Openbox was an expression of love, and hence not to be taken literally. 

I've never felt comfortable in tiling window managers, though. I've tried ratpoison, wmii and dwm, but I always return to Openbox. The main reason is that I keep most of my most frequently used apps (Opera, OpenOffice) maximized, and that sort of goes against tiling wm (or do I totally not understand how tiling wms work?).

you can maximize apps, just as in openbox (alt+tab through the apps, or put them on different workspaces). the two things that made it for me were the menu and what happens when you open new apps. the menu pops up with a key combo and you just start typing the app name until it's highlighted (usually two or three letters). when an app opens, it doesn't open in the middle of the app you've been looking at, it divides the space in a variety of ways (tiles, grid, verticle, etc), with each app owning its own place. 

the first time i tried a tiling window manager, it was ratpoison and i thought it was absolutely retarded, same with dwm. something clicked and i stayed. as with all this stuff, it's a matter of choice. no need for a war (of course, i was joking, as you've probably already assumed). we can all coexist in joy and harmony.

---

### Post by urukrama on 2008-02-03
I'm giving wmii another try. It is rather hard getting used to the way it works. I'll have to give it some time...

Any tips you have to share? I could use some encouragement. :-)

---

