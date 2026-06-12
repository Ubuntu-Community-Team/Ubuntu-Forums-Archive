---
title: "Kde sc 4.5 rc2"
date: 2010-07-10
forum: The Cafe
---

### Post by isaacj87 on 2010-07-10
So, the dust has finally settled and RC2 has been released. It's been a couple of days and I wanted to really play with RC2 before saying anything. So far, I'm actually having more problems with RC2 than RC1. However, it could be due to the fact that I'm running openSUSE 11.3 RC2 or something got lost in translation during packaging. Regardless, here are my thoughts:

What's good?

- Fast. KDE has always been a hog on my netbook, but on my desktop, it feels right at home. The speed of the environment has increased and RC2 feels nice and lively. Kwin has improved dramatically and the animations are smooth. Plasma doesn't feel heavy (not that it really did in 4.4) which is great.

- Feature-rich. It seems all the technologies that the devs have been busily working on for the last couple of years are finally coming together. Plasma is pretty damn great. Desktop searching and tagging works as it should and the menus are complete and easy to navigate.

- Notification area. I know, an area as small as this is usually overlooked. However, the system tray has been vastly improved. It's actually useful now instead of being bothersome. 

- It's all coming together. It's hard to believe that KDE 4.0 has transformed into this. Amazing.

What's bad?

- Graphical glitches. While the animations have improved, they still seem to jump a bit. My Nvidia card and the proprietary driver could be to blame, but it's annoying nevertheless. I'm not getting shadows for my drop-down menus. Also, while I love the new blur effect, it is inconsistent. Certain aspects of the plasma workspace have the blur effect enabled, while some don't. Widgets don't receive the blur effect which is odd.

- Wasted space. In OSX, the menus will adjust and resize depending on the content presented in the window. I wonder if this is possible with Qt. It seems like there's a lot of padding everywhere. 

- Buttons. If you look at the Plasma's "Air" theme, it has different buttons than those found everywhere else. The buttons found throughout are rectangular, harsh-looking and could probably be "smoothed" out. 

That's all I can think of right now. Mostly I complained about superficial problems. The actual core technologies in KDE work pretty well and I'm bored now that I'm not running into as many problems. Surprisingly, that's actually a good thing. It's a shame that openSUSE isn't taking quite an ambitious approach to their distro that Ubuntu is, but I love KDE. And KDE runs best on openSUSE. Overall, my experience on KDE seems no different than Windows 7 or OS X's user interfaces. The KDE devs have created a modern, attractive DE and it's pretty impressive. I've included the obligatory picture. Enjoy :)

---

### Post by NormanFLinux on 2010-07-11
When it comes out of beta, it will be the default KDE desktop. Kubuntu will have it by the fall and rolling distros will have it earlier.

---

### Post by cguy on 2010-07-11
I installed KDE 4.5 when it was in beta 2.
Sucks on my setup.

When the effects are enabled, my CPU usage (when idle) jumps between 40 and 90 percent.

With the effects disabled, the usage is between 20 and 50%.

The culprit is Xorg.

I already have a semi-crappy CPU, so you can imagine how it's like when I have to do some work.
:( should have stuck with 4.4 ...

---

### Post by irrdev on 2010-07-11
I have KDE 4.5 RC2 running on my Kubuntu desktop and it is absolutely amazing! It's hard to believe that this is the same desktop as KDE 4.0 Beta 1 which I attempted using several years ago... concerning graphic glitches, I think they are probably related to your graphic card drivers. I have intel integrated graphics and everything is running perfectly smoothly on my machine, with full kwin effects + compositing enabled.

---

### Post by isaacj87 on 2010-07-11
> **cguy said:**
> I installed KDE 4.5 when it was in beta 2.
Sucks on my setup.

When the effects are enabled, my CPU usage (when idle) jumps between 40 and 90 percent.

With the effects disabled, the usage is between 20 and 50%.

The culprit is Xorg.

I already have a semi-crappy CPU, so you can imagine how it's like when I have to do some work.
:( should have stuck with 4.4 ...

Hmmm...seems to be the same on my system as well. Never noticed that before.

---

### Post by cguy on 2010-07-13
adding this ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

doing an upgrade

and disabling the blur effect

improves the situation.

---

### Post by nrs on 2010-07-13
> **isaacj87 said:**
> Wasted space. In OSX, the menus will adjust and resize depending on the content presented in the window. I wonder if this is possible with Qt. It seems like there's a lot of padding everywhere. 

Really? This is actually one of the big reasons I dislike GNOME/GTK+ applications visually. I mean, let's compare.

I don't think you can really deny that the GTK+ application looks/feels 'bigger'. I tried to give them the same dimensions. It's worth pointing out that  the evolution windows couldn't be resized any lower, and I added an HTML  formatting toolbar to the kmail compose window to turn and make a more  meaningful comparison.

---

### Post by nrs on 2010-07-13
Editing fail. Delete if read by mod.

---

### Post by isaacj87 on 2010-07-13
> **nrs said:**
> Really? This is actually one of the big reasons I dislike GNOME/GTK+ applications visually. I mean, let's compare.

I don't think you can really deny that the GTK+ application looks/feels 'bigger'. I tried to give them the same dimensions. It's worth pointing out that  the evolution windows couldn't be resized any lower, and I added an HTML  formatting toolbar to the kmail compose window to turn and make a more  meaningful comparison.

True. And the pics you added are evidence to that, but what about a situation like the example I provided?

I won't deny the fact that KDE/Qt applications are *usually* cleaner and more eye-appealing, but I'll never understand why, in some instances, so much room is given to so little content.

---

### Post by Islington on 2010-07-13
> **isaacj87 said:**
> True. And the pics you added are evidence to that, but what about a situation like the example I provided?

I won't deny the fact that KDE/Qt applications are *usually* cleaner and more eye-appealing, but I'll never understand why, in some instances, so much room is given to so little content.

This panel will be crucial as the activities become more stabilized, and some cool features are added. you can see the beginnings of it in the activities manager now, but individual activities will have options in the future: what kinds of windows to associate with activity for example.

edit: also I must point out that air =/= oxygen. The only thing I did not like about the air default theme are the new notification icons. yuck :P

---

### Post by nerdy_kid on 2010-07-14
runs smooth as silk on my machine -- after i deleted all my config files to fix a stupid plasma bug.  but it was worth it -- gonna be the best release ever!

---

### Post by RevengeOfTheToxicRodent on 2010-07-14
Is Kubuntu 10.10 daily using the RC2 yet?

---

