---
title: "9wm: the pinochle of human achievment"
date: 2007-10-06
forum: The Cafe
---

### Post by fuscia on 2007-10-06
looks like rav's already moved on. anyway...

this has got to be the most minimal of all wms. all you get is a right lick menu that offers the five choices of *new, reshape, move, delete* and *hide*. *new* opens up an xterm. when you open an app, a cross appears and you place and shape the window with that cross. that's pretty much it. oh, and xfce panel and conky work with it (haven't tried a bunch of the rest with it).

---

### Post by yabbadabbadont on 2007-10-06
Sounds like the old X default, TWM.

---

### Post by fuscia on 2007-10-06
> **yabbadabbadont said:**
> Sounds like the old X default, TWM.

i haven't used twm very much (the ugly green and stupid circles were too much), but all this is, is black outlines.

---

### Post by -grubby on 2007-10-06
yep. Pretty minimal and non-exciting looking

---

### Post by yabbadabbadont on 2007-10-06
> **fuscia said:**
> i haven't used twm very much (the ugly green and stupid circles were too much), but all this is, is black outlines.

TWM can be customized much like any other window manager.  I forget who it is, but there is a long time Gentoo user who uses nothing else.  His screenshots were very nice too.

Edit: It is papal_authority.

---

### Post by fuscia on 2007-10-06
> **nathangrubb said:**
> yep. Pretty minimal and non-exciting looking

the idea is to provide your own excitement.

---

### Post by Fbot1 on 2007-10-06
I actually like rio.

---

### Post by fuscia on 2007-10-06
> **Fbot1 said:**
> I actually like rio.

i want to die in rio, after a week of partying.

---

### Post by D-EJ915 on 2007-10-06
Twm is not really much like it to be honest although you can make twm look like it at least, 9wm isn't quite as configurable.  In real plan 9 you can make each window contain the actual desktop, that leads to much excitement :P

I wouldn't use it as my main wm, but it's fun to mess around with.

---

### Post by Fbot1 on 2007-10-06
> **fuscia said:**
> i want to die in rio, after a week of partying.

That's what we're talking about right? Rio the window manager?

---

### Post by n3tfury on 2007-10-06
> **nathangrubb said:**
> yep. Pretty minimal and non-exciting looking

there are a few people here that take the minimalistic base and can really make something their own.  i don't recall all the names (see desktop thread in sticky section) but fuscia's one of them. but then again, some people just want to click 'apply' to install a new theme.  obviously this sort of thing isn't for them.

*edit* loke's another one.  i mean, tell me this isn't secksi  [http://icedloki.deviantart.com/art/Desktop-as-seen-on-10-06-07-66678349](http://icedloki.deviantart.com/art/Desktop-as-seen-on-10-06-07-66678349)

---

### Post by fuscia on 2007-10-06
thanks for the compliment, n3t. hopefully, this will be a humble illustration of what you say...

---

### Post by n3tfury on 2007-10-06
NICE!  i don't post much in that desktop thread because that's all i'd be saying heh.  i've still not had a chance to mess with openbox because of such a full workload (and no *nix box at work :/ ) but it'll happen.   keep it up - always inspiring.

---

### Post by Lux Perpetua on 2007-10-07
> **fuscia said:**
> looks like rav's already moved on. anyway...

this has got to be the most minimal of all wms. all you get is a right lick menu that offers the five choices of *new, reshape, move, delete* and *hide*. *new* opens up an xterm. when you open an app, a cross appears and you place and shape the window with that cross. that's pretty much it. oh, and xfce panel and conky work with it (haven't tried a bunch of the rest with it).Is it more minimal than [XMonad](www.xmonad.org)? XMonad gives you next to nothing by default, not even a menu. I reckon there's only so much a person can fit into 500 lines of Haskell code. You can basically start an xterm, switch layouts, (sort of) shuffle windows, (sort of) resize windows, and switch workspaces. To add your own configuration, you have to modify the source and recompile it (easier than it sounds). I'm trying to get some of the user-contributed extensions working right now.

---

### Post by fuscia on 2007-10-07
> **Lux Perpetua said:**
> Is it more minimal than [XMonad](www.xmonad.org)? XMonad gives you next to nothing by default, not even a menu. I reckon there's only so much a person can fit into 500 lines of Haskell code. You can basically start an xterm, switch layouts, (sort of) shuffle windows, (sort of) resize windows, and switch workspaces. To add your own configuration, you have to modify the source and recompile it (easier than it sounds). I'm trying to get some of the user-contributed extensions working right now.

sounds interesting. what's this cabal thing? if i install ghc6 - GHC, is that enough to build xmonad? (end user, here.)
:popcorn:

---

### Post by bobbocanfly on 2007-10-07
9wm and Xmonad sound really cool. Will give them both a shot in the near future

---

### Post by yabbadabbadont on 2007-10-08
@fuscia: papal_authority got back to me with a few screenshots of his setup using TWM.  You can see them here:

[http://omploader.org/vNTgx/twm0.jpg](http://omploader.org/vNTgx/twm0.jpg)
[http://omploader.org/vNTgy/twm1.png](http://omploader.org/vNTgy/twm1.png)
[http://omploader.org/vNTgz/twm2.png](http://omploader.org/vNTgz/twm2.png)
[http://omploader.org/vNTg1/twm4.png](http://omploader.org/vNTg1/twm4.png)

I left out the shot that included foul language in his chat client.  ;)

---

### Post by Lux Perpetua on 2007-10-08
> **fuscia said:**
> sounds interesting. what's this cabal thing? if i install ghc6 - GHC, is that enough to build xmonad? (end user, here.)
:popcorn:It has a few other dependencies. From the README: ```
Building:

Get the dependencies

    It is likely that you already have some of these dependencies.  To check
    whether you've got a package run 'ghc-pkg list some_package_name'

    mtl             http://hackage.haskell.org/cgi-bin/hackage-scripts/package/mtl-1.0
    unix            http://hackage.haskell.org/cgi-bin/hackage-scripts/package/unix-2.0 
    X11             http://hackage.haskell.org/cgi-bin/hackage-scripts/package/X11-1.2.2
    X11-extras:     http://hackage.haskell.org/cgi-bin/hackage-scripts/package/X11-extras-0.3

And then build with Cabal:

    runhaskell Setup.lhs configure --prefix=$HOME
    runhaskell Setup.lhs build
    runhaskell Setup.lhs install --user
```I think mtl and X11 are in the repositories (libghc6-mtl-dev and libghc6-x11-dev), but I couldn't find X11-extras. Apparently, unix-2.0 came with ghc. Anyway, all of those packages are at hackage.haskell.org, and to build them, you can just do the last three runhaskell commands after downloading (except sometimes Setup.lhs is Setup.hs). I had mixed success with the repositories: mtl seemed to work, but I had to use X11 from hackage.

---

### Post by fuscia on 2007-10-08
getting xmonad installed sounds like a giant pain in the butt. i'll probably try it the next time i get bored. thanks for the info. i'll be needing it.


yabba, with the exception of the menu font, those are some pretty fun looking screenshots.

---

### Post by fuscia on 2007-10-31
it's like driving a stick instead of buying a cake with someone else's name on it...

---

### Post by D-EJ915 on 2007-10-31
> **fuscia said:**
> it's like driving a stick instead of buying a cake with someone else's name on it...
that's an interesting way of putting it...weird how everything is with the right mouse button though

[[IMG]http://img.photobucket.com/albums/v104/enthauptet/bin/th_9wm.jpg[/IMG]](http://img.photobucket.com/albums/v104/enthauptet/bin/9wm.jpg)

---

### Post by fuscia on 2007-11-17
i just realized that i can use urxvt instead of xterm as the default by putting *9wm -term urxvt* in my .xinitrc and then use .Xdefaults to setup how i want urxvt to look. pretty cool. you can also set font and color and some other thing, but i haven't messed with those yet.

---

### Post by Palmyra on 2007-11-17
Do you mean pinnacle or pinochle?  They're both words, but pinochle is about playing cards.

---

### Post by fuscia on 2007-11-17
> **Palmyra said:**
> Do you mean pinnacle or pinochle?

yes.

---

### Post by Iandefor on 2007-11-17
If 9wm is the pinochle, what's the blackjack of human achievement?

---

### Post by fuscia on 2007-11-17
> **Iandefor said:**
> If 9wm is the pinochle, what's the blackjack of human achievement?

windows. unless you're a really good player, the dealer has the best chance of winning.

---

