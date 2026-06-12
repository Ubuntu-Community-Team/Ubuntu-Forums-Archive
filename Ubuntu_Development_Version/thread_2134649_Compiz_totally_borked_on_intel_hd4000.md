---
title: "Compiz totally borked on intel hd4000"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by screaminj3sus on 2013-04-11
Tried today's raring ISO, hoping compiz was finally useable. Seems worse than ever, Simply minimizing a window appears to totally freeze compiz.

---

### Post by mc4man on 2013-04-11
> **screaminj3sus said:**
> Tried today's raring ISO, hoping compiz was finally useable. Seems worse than ever, Simply minimizing a window appears to totally freeze compiz, these regressions are getting absurd.
You aren't happening to be using compiz without nautilus handling the desktop, in that scenario one cannot minimize windows
(maybe if animations are disabled.

---

### Post by screaminj3sus on 2013-04-11
> **mc4man said:**
> You aren't happening to be using compiz without nautilus handling the desktop, in that scenario one cannot minimize windows
(maybe if animations are disabled.

just the default vanilla ubuntu unity desktop...

---

### Post by mc4man on 2013-04-11
The only hardware I've got ubuntu on is a laptop with nvidia,(nouveau), things are generally ok.
(though compiz performs a bit  better when the unity plugin is disabled

I do have a new laptop with hd4000 (nvidia gtx 660m, optimus) though I've only used ubuntu 13.04 in a live session.
( no big rush to install ubuntu on it, kinda nice to have everything work well, especially from a multimedia perspective..
 It seemed fine,  though in a live session FM handling the Desktop is default disabled

---

### Post by screaminj3sus on 2013-04-11
> **mc4man said:**
> The only hardware I've got ubuntu on is a laptop with nvidia,(nouveau), things are generally ok.
(though compiz performs a bit  better when the unity plugin is disabled

I do have a new laptop with hd4000 (nvidia gtx 660m, optimus) though I've only used ubuntu 13.04 in a live session.
( no big rush to install ubuntu on it, kinda nice to have everything work well, especially from a multimedia perspective..
 It seemed fine,  though in a live session FM handling the Desktop is default disabled

I was in the live session so it should be the same defaults you were using in yours.

---

### Post by mc4man on 2013-04-11
Just tried today's live image on the intel laptop, it seems it's again having the Desktop enabled vs. about a week ago or so ago & before  when it wasn't enabled. (you see 2 icons, can right click on Desktop, ect?

The min. works fine here, get the initial slow animation as expected.

---

### Post by screaminj3sus on 2013-04-12
You were right, the iso i downloaded defaulted to not having nautilus handling desktop icons, and re-enabling nautilus handling the desktop fixed the freezing.

---

### Post by mc4man on 2013-04-12
What I've noticed lately is some interest from a few in fixing compiz bugs & plugins, some very longstanding like bindings for scale > window picker for window group, ect. 
What the endgame is for compiz-0.9.x is no clue, does it die when unity stops using or does it continue ?? (& if so for what use..

While I'd certainly reserve judgment on unity next on the desktop till there is something more in place than currently can be sampled, it wouldn't surprise me if **I** find it uninteresting for my use. (on a desktop or laptop

---

### Post by screaminj3sus on 2013-04-12
Luckily, after using it for a while after re-enabling nautilus compiz seems to be working quite well, and all the other bugs I had been dealing with before I ran into this one seem to be fixed :).

I think this bug exemplifies how fragile things are with compiz at the moment though lol, when nautilus was disable compiz just totally freaked out, constantly freezing and acting so bizarre that it was unusable.

---

### Post by mc4man on 2013-04-12
Even the qt4 menu deal is fixed (fixed committed), should show soon. 
I still think most of compiz's issues  like ^ where caused by the unityshell plugin & gles2 support

Any way this bug fix, if it happens, is of interest here. I currently enable thru a dbus command & custom plank launcher/keyboard binding but as is typical the command in compiz > commands disappears fairly regularly & has to be reset.

[https://bugs.launchpad.net/bugs/774059](https://bugs.launchpad.net/bugs/774059)

---

