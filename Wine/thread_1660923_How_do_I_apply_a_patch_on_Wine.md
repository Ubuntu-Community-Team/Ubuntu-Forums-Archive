---
title: "How do I apply a patch on Wine?"
date: 2011-01-06
forum: Wine
---

### Post by Mr. ViC on 2011-01-06
So, after a lot of work and headaches I finally got the game I wanted (Sanitarium) running well on Wine.

Except one thing.

The cursor leaves this anoying trace of black color behind. And the game is a "point&click" game. Which makes this really anoying.

Did some research already, and I think this would solve it:

```
[http://bugs.winehq.org/show_bug.cgi?id=10708](http://bugs.winehq.org/show_bug.cgi?id=10708)
```And I found this tutorial to apply it:

```
[http://www.sdconsult.no/linux/wine-doc/getting-upgrading.html](http://www.sdconsult.no/linux/wine-doc/getting-upgrading.html)
```But no sucess.

Can anyone, please, explain me how to apply that patch like I'm 5 year old?

This might also help other people in the future with the same problem (that's how I solve most of mine without bothering you guys).

Thank you.

---

### Post by ronnielsen1 on 2011-01-06
edit out

---

### Post by Mr. ViC on 2011-01-06
What?

By the way, I have found this:

```
http://wiki.winehq.org/Patching
```

Good and safe to follow?

---

### Post by cogadh on 2011-01-06
That bug is a "closed fixed" bug, meaning whatever that patch was supposed to correct has already been included in the current version of Wine; IIRC its been fixed since the 1.1.9 version of Wine. Not only will applying that patch not accomplish anything, it will very likely break things in Wine, that is, assuming you are using at least the current stable version of Wine, 1.2.2.

---

### Post by Mr. ViC on 2011-01-06
Understood, thanks.

Applied the patch before I read what you wrote, but everything works just fine (in Wine).

The game cursor still has that problem, it creates a drawing of black squares when moving it. They disappear after a few milliseconds.

Is there other way I can solve this? On AppDB people don't seem to complain about that on older (and unstable) versions of the game.

I was able to take a screen of it:

[img]http://img.myph.us/FYh.png[/img]

Thank you.

---

### Post by Mr. ViC on 2011-01-06
Just to say I found a solution. Changed DirectDraw in Wine Registry from OpenGL to gdi and it works great.

Thank you.

---

