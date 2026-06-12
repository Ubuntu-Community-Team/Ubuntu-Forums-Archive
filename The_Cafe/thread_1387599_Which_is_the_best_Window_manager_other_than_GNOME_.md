---
title: "Which is the best Window manager other than GNOME / KDE / XFCE?"
date: 2010-01-22
forum: The Cafe
---

### Post by bilalakhtar on 2010-01-22
Hi guys,
Which is the best X window manager other than GNOME, KDE and XFCE?
Please vote...

---

### Post by bilalakhtar on 2010-01-22
Forgot to add LXDE , sorry.

---

### Post by mocoloco on 2010-01-22
^^ Yes you did, and that's exactly the one I would vote for, LXDE :)

---

### Post by Bodsda on 2010-01-22
My vote is Fluxbox - Tabbing windows together is a wonderful feature and the slit is pretty cool as well

---

### Post by Tibuda on 2010-01-22
Openbox

---

### Post by fancypiper on 2010-01-22
Fluxbox rules!

Tabbed windows maximises screen area and the slit holds gkrellm nicely.

---

### Post by XubuRoxMySox on 2010-01-22
I haven't even tried them all, so I guess I'm not qualified to vote... besides it depends on what you want from a DE/WM. Speed and simplicity or way-kewl super razoo 3D animated special effects or whatever.

I really like Openbox ([Crunchbang]("http://crunchbanglinux.org") is awesome!), and I love the simplicity and uber-lightweight speed of [LXDE]("http://lxde.org") (on Debian Squeeze). But LXDE on minimal Ubuntu was plagued with maddeningly persistent bugs. It drove me to Xubuntu, which is really great, a delightful surprise to me.

-Robin

---

### Post by AllRadioisDead on 2010-01-22
Gnome/KDE/XFCE are not window managers, they are desktop environments.
Metacity, Kwin, and Xfwm are window managers.

---

### Post by Rhubarb on 2010-01-22
I put my vote in for wmii.  It's a tiling window manager that's heavily biased towards keyboard (only) use.  There's shortcuts everywhere for it :)

But, unfortunately its primarily configured for qwerty use, so us dvorak keyboard layout people get the rough end of the stick.

[wmii]("http://wmii.suckless.org/")
[wmii on wikipedia]("http://en.wikipedia.org/wiki/Wmii")

---

### Post by Rhubarb on 2010-01-22
.

---

### Post by chucky chuckaluck on 2010-01-22
i think i've tried just about every wm available. the one i keep coming back to is openbox. i get bored as hell with it, sometimes, but when i need things to work (and work in a way that suits me), i pick openbox. there may be wms that most of us could agree aren't very good, but choosing the 'best' is going to be a matter of personal preference.

---

### Post by K.Mandla on 2010-01-22
Musca. Or screen. If I must use something with title bars, it will be Openbox.

---

### Post by RiceMonster on 2010-01-22
dwm, because it's tiling and isn't a nightmare to configure.

If it's floating, I'll just go with one of the three in the title.

---

### Post by Daisuke_Aramaki on 2010-01-22
Fvwm and a close call between scrotwm and wmii for tiling wm's. Having said that, I use twm on a lot of old boxes and on my eee as the only wm, with vdesk support and i like it too.

---

### Post by Mark76 on 2010-01-22
Nice to see more people aware of the ROX DE as well as the filer.

Perhaps this might lead to more Dev love eventually :D

---

### Post by chucky chuckaluck on 2010-01-22
> **K.Mandla said:**
> Musca. Or screen. If I must use something with title bars, it will be Openbox.

you know about something like this, don't you?

```

<applications>

  <!-- match all windows, and remove their decorations -->
  <application class="*">
    <decor>no</decor>
  </application>

</applications>
```

(i'm not sure that's right, but i've used something similar to get rid of title bars in ob.)

---

### Post by jpkotta on 2010-01-22
I like Fvwm.  Other WMs look very interesting, but I know Fvwm well enough that I can fix almost any annoyance I have easily (N.B. "annoyance" is very person-dependent).  So basically, I'm too lazy to try anything else, because what I have works so well.  It was quite a journey getting to this point though.  

> **chucky chuckaluck said:**
> you know about something like this, don't you?

```

<applications>

  <!-- match all windows, and remove their decorations -->
  <application class="*">
    <decor>no</decor>
  </application>

</applications>
```

(i'm not sure that's right, but i've used something similar to get rid of title bars in ob.)

In Fvwm, it would be ```
Style * !Title, !Borders
```

---

### Post by k64 on 2010-01-22
I personally like Compiz by itself.

---

### Post by Psumi on 2010-01-23
> **k64 said:**
> I personally like Compiz by itself.

lol.

Can't believe no one said mutter yet.

---

### Post by earthpigg on 2010-01-23
lxde/openbox.

or just openbox with lxpanel configured to start with openbox.

---

### Post by chessnerd on 2010-01-23
LXDE. I'm running it right now on this desktop and it's working great. Harder to configure than XFCE, but it's lighter and, once configured, easy to use.

---

### Post by earthpigg on 2010-01-23
> **chessnerd said:**
> LXDE. I'm running it right now on this desktop and it's working great. Harder to configure than XFCE, but it's lighter and, once configured, easy to use.

you can use certain gnome/xfce tools to configure lxde... for example, alacarte to add things to the menus.

---

### Post by nmaster on 2010-01-23
i like ice for lightweight stuff like on older machines.

---

### Post by chris4585 on 2010-01-23
Openbox.

LXDE is a desktop environment not a windows manager, the windows manager LXDE uses is openbox by default.

---

### Post by &#32 Greg on 2010-01-23
Xmonad.

---

### Post by koleoptero on 2010-01-23
I can't believe you left out openbox. Shame on you :P

---

### Post by dragos240 on 2010-01-23
Metacity. GNOME isn't a wm.

---

### Post by chris4585 on 2010-01-23
> **koleoptero said:**
> I can't believe you left out openbox. Shame on you :P

inorite, the OP put in fluxbox but not openbox?

---

### Post by koleoptero on 2010-01-23
> **chris4585 said:**
> inorite, the OP put in fluxbox but not openbox?

No fluxbox is ok, and popular enough. But ROX? Who uses rox anyway? ;)

---

### Post by Psumi on 2010-01-23
> **koleoptero said:**
> No fluxbox is ok, and popular enough. But ROX? Who uses rox anyway? ;)

I had the worst time trying to figure out how to switch desktops via fluxkeys. So I just installed openbox and it already had that feature. I've been with openbox over fluxbox whenever I want a *box.

Problem is: I still don't know how to get the debian menu into obmenu so that I don't have to keep adding apps to obmenu manually.

---

### Post by Mark76 on 2010-01-23
> **koleoptero said:**
> No fluxbox is ok, and popular enough. But ROX? Who uses rox anyway? ;)

Ahem

*points to sig*

---

### Post by RabbitWho on 2010-01-23
Icewrm is the only other one I've used besides those three, with Spri and Puppy Linux, and I love it.

---

### Post by koleoptero on 2010-01-23
> **Psumi said:**
> I had the worst time trying to figure out how to switch desktops via fluxkeys. So I just installed openbox and it already had that feature. I've been with openbox over fluxbox whenever I want a *box.

Problem is: I still don't know how to get the debian menu into obmenu so that I don't have to keep adding apps to obmenu manually.
My openbox setup had the debian menu in by default. Want me to check how it does it?

EDIT:

```
<!-- This requires the presence of the 'menu' package to work -->
                <separator/>
                <menu id="Debian"/>
                <separator/>
                <menu id="client-list-menu"/>
                <separator/>

```
There's a package called "menu" so I believe that it's the one responsible.
> **Mark76 said:**
> Ahem

*points to sig*
I just wanted to see how fast you'd react to it! That was fast! :D

---

### Post by Psumi on 2010-01-23
> **koleoptero said:**
> My openbox setup had the debian menu in by default. Want me to check how it does it?

When you open the obmenu editor, you'll notice that Debian is a "Link."

Sadly, when on a mini.iso and you install openbox, xorg, and wdm (or slim or whatever), and then open the openbox menu, the debian menu won't be there. I've already tried this before. It's there, it just doesn't work.

---

### Post by koleoptero on 2010-01-23
> **Psumi said:**
> When you open the obmenu editor, you'll notice that Debian is a "Link."

Sadly, when on a mini.iso and you install openbox, xorg, and wdm (or slim or whatever), and then open the openbox menu, the debian menu won't be there. I've already tried this before. It's there, it just doesn't work.

```
lo-fi@lo-fi-lappy:~$ sudo apt-cache show menu
[sudo] password for lo-fi: 
Package: menu
Priority: optional
Section: universe/admin
Installed-Size: 1940
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Bill Allombert <ballombe@debian.org>
Architecture: i386
Version: 2.1.41ubuntu1
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1)
Suggests: gksu | kdebase-bin | kdebase-runtime | ktsuss | sux
Filename: pool/universe/m/menu/menu_2.1.41ubuntu1_i386.deb
Size: 438218
MD5sum: 429b0fad74d94d04487c661d7c4a139c
SHA1: 60c6a7b7901dc3ce19816cfdb5ab1f4106898636
SHA256: 1e18fcf318d2536cb0c75feafcfb17c4dcf1f388f6238c1a9893a624d7f350e9
Description: generates programs menu for all menu-aware applications
 Debian menu keeps transparently the menus in the different
 window-managers in sync with the list of installed programs.
 .
 Debian menu relies on a list of menu entries provided by programs
 and a list of menu-methods provided by window-managers and other
 menu-aware applications.
 .
 Menu provides system-level and user-level configuration and overrides
 for both menu entries and menu-methods.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

:popcorn:

---

### Post by Psumi on 2010-01-23
> **koleoptero said:**
> ```
lo-fi@lo-fi-lappy:~$ sudo apt-cache show menu
[sudo] password for lo-fi: 
Package: menu
Priority: optional
Section: universe/admin
Installed-Size: 1940
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Bill Allombert <ballombe@debian.org>
Architecture: i386
Version: 2.1.41ubuntu1
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1)
Suggests: gksu | kdebase-bin | kdebase-runtime | ktsuss | sux
Filename: pool/universe/m/menu/menu_2.1.41ubuntu1_i386.deb
Size: 438218
MD5sum: 429b0fad74d94d04487c661d7c4a139c
SHA1: 60c6a7b7901dc3ce19816cfdb5ab1f4106898636
SHA256: 1e18fcf318d2536cb0c75feafcfb17c4dcf1f388f6238c1a9893a624d7f350e9
Description: generates programs menu for all menu-aware applications
 Debian menu keeps transparently the menus in the different
 window-managers in sync with the list of installed programs.
 .
 Debian menu relies on a list of menu entries provided by programs
 and a list of menu-methods provided by window-managers and other
 menu-aware applications.
 .
 Menu provides system-level and user-level configuration and overrides
 for both menu entries and menu-methods.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

:popcorn:

I'll try that next time that I'm on just openbox.

---

### Post by koleoptero on 2010-01-23
> **Psumi said:**
> I'll try that next time that I'm on just openbox.

Bear in mind though that even the debian menu isn't that good a solution. Some programs aren't listed, like xfburn and decibel-audio-player, and some are listed in awkward places, like vlc under viewers.

I find that the best solution is to have obmenu and make entries as I need them.

---

### Post by Chilli Bob on 2010-01-23
iceWM and JWM are both awesome and light.

---

### Post by K.Mandla on 2010-01-23
> **chucky chuckaluck said:**
> you know about something like this, don't you?

```

<applications>

  <!-- match all windows, and remove their decorations -->
  <application class="*">
    <decor>no</decor>
  </application>

</applications>
```

(i'm not sure that's right, but i've used something similar to get rid of title bars in ob.)
That's way too much work. I can't be bothered to configure anything. :roll:

---

### Post by &#32 Greg on 2010-01-23
> **K.Mandla said:**
> That's way too much work. I can't be bothered to configure anything. :roll:

First a P4 computer, now not configuring anything... what will Motho ke motho ka botho come to?

;;And does it get weird when people like me, who you have no idea who they are, make comments like this?

---

### Post by koleoptero on 2010-01-23
> **K.Mandla said:**
> That's way too much work. I can't be bothered to configure anything. :roll:

Just put the titlebar font to size 1 :P

---

### Post by Mark76 on 2010-01-24
ROX Desktop isn't a window manager (the official ROX DE window manager is OroboROX).

Maybe there should be a separate poll for alternative DEs

---

### Post by SushiR on 2010-01-24
Openbox - powerful and elegant

---

### Post by AllRadioisDead on 2010-01-24
dwm :D

---

### Post by Hetor on 2010-01-24
Standalone compiz.

---

### Post by ElSlunko on 2010-01-24
I use gnome primarily, but I do love some good openbox desktops I've seen around here. I play with the idea of going openbox at times.

---

### Post by gutterslob on 2010-01-24
was tempted to vote for ROX (Mark seemed lonely)

Anyways,
I'm in the Openbox camp. I actually didn't like it until I tried it on CrunchBang, and now I try to mimic #! on my Debian+Openbox setups.
Tried out a few other window managers like FVWM, DWM, PekWM, FluxBox, XMonad, Compiz, and they all had their advantages (DWM was particularly awesome), but somehow always came back to Openbox. 

There's just so much it does right for me, plus I also think it's beautiful when themed right (I was never into theming and customizing until I started using Openbox, which says a lot about the WM and the type of person I am, I guess). I tend to prefer greyish/monochromatic setups, and Openbox seems to agree with my style more readily than other WM's.

I did miss tiling, but then I started using _**[PyTyle]("http://pytyle.com/wiki/Features")**_ with it, and the rest is history.

On a side note, I've been meaning to try ScrotWM, but haven't found enough free time to actually sit down and get it configured yet.

---

### Post by stanca on 2010-02-13
In spite the fact that Openbox seems to be more popular these days,especially on this forum,and that each WM has +'s and -'s,personally I always stick with E17-Ecomorph and Fluxbox in the end.They just suit my taste.
But from time to time I miss Gnome's compiz too.;):)

---

### Post by chucky chuckaluck on 2010-02-13
> **K.Mandla said:**
> That's way too much work. I can't be bothered to configure anything. :roll:

oh, an ootb type, eh?

---

