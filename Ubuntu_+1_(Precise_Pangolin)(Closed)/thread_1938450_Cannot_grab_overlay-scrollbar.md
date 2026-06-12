---
title: "Cannot grab overlay-scrollbar"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by manzdagratiano on 2012-03-09
Hey people,

I did not find an existing thread on this - I just realized that I seem to be unable to grab the overlay scrollbar with a left click - I have a Synaptics Touchpad. I can scroll in the window using the right edge of the touchpad, but when I attempt to grab the scrollbar itself, it disappears, and I end up grabbing the window edge which would resize it. Has anyone seen this issue? Or is there a new behavior I am missing?

Also, I see a reference to the 'thumb' of the scrollbar in bug reports (unrelated) - could someone clarify if this refers to a region of the scrollbar or the user's thumb on the touchpad (odd)?

---

### Post by x-shaney-x on 2012-03-09
I also have a synaptics pad.
I hadn't actually tried grabbing it before, since I normally just 2-finger scroll but tried it after reading your thread and yes, the same happens.
The overlay just vanishes.

Mind you, I'd like to see them vanish altogether but quite this way :)

As for the "thumb" I would assume that means the actual grab-able part of it (that is vanishing).

---

### Post by mc4man on 2012-03-09
> **manzdagratiano said:**
> Hey people,

I did not find an existing thread on this - I just realized that I seem to be unable to grab the overlay scrollbar with a left click - I have a Synaptics Touchpad. I can scroll in the window using the right edge of the touchpad, but when I attempt to grab the scrollbar itself, it disappears, and I end up grabbing the window edge which would resize it. Has anyone seen this issue? Or is there a new behavior I am missing?

Also, I see a reference to the 'thumb' of the scrollbar in bug reports (unrelated) - could someone clarify if this refers to a region of the scrollbar or the user's thumb on the touchpad (odd)?

The 'thumb' is what is shown in the screen, that's the 'grab-able' part of the overlay scrollbar (so I'm fairly sure you see it ?

Initially it has a very short life, 250 ms till it starts to fade, an additional 750 ms till it's gone & would need to be re-aquired 

(- which isn't hard, more the issue is it sometimes gets in the way. That may be one reason that the thumb can now be used for window resizing hortizontally, just grab & move left or right

The current issue here is that 'scroll on thumb' is broken, nothing happens & it disappears. (could be hardware & or Arch related.
[https://bugs.launchpad.net/bugs/951121](https://bugs.launchpad.net/bugs/951121)

---

### Post by manzdagratiano on 2012-03-09
I just upgraded my other computer, which has an nvidia driver, and on that one, grabbing the scrollbar works just fine! The first one has an Intel driver - could this possibly be graphics related (I fail to understand why but that is the only obvious difference)?

---

### Post by x-shaney-x on 2012-03-10
> **manzdagratiano said:**
> I just upgraded my other computer, which has an nvidia driver, and on that one, grabbing the scrollbar works just fine! The first one has an Intel driver - could this possibly be graphics related (I fail to understand why but that is the only obvious difference)?

Well since I also have the problem and am also on Intel graphics than it looks like it could be the problem.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-10
Same problem here, very annoying. If a cursor is moved closer on the left side of the scrollbar, the "thumb" shows, but as soon as you try to move the pointer over it, it disappears. What gives?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-16
I wonder if anyone is still having this problem? As I recall, Unity was updated and this bug was supposed to be fixed, but I'm still experiencing it, Unity 5.6.0-0ubuntu4.

---

### Post by x-shaney-x on 2012-03-16
When I move the pointer over the overlay area, the thumb appears but flickers and as soon as I let pressure off the touchpad, it vanishes.

If I move the pointer over it and then move up and down without letting go, the thumb moves (still flickering) but doesn't actually scroll.

If I move the pointer over it and VERY quickly double-tap on the touchpad, I am able to move the thumb and scroll.

So no, certainly not working as it should.

---

### Post by mc4man on 2012-03-16
> **&#1058 said:**
> I wonder if anyone is still having this problem? As I recall, Unity was updated and this bug was supposed to be fixed, but I'm still experiencing it, Unity 5.6.0-0ubuntu4.
It affects some hardware, (usually some touchpads),  but not others, for example I can grab it fine here with a touchpad though I can't scroll **on** it but can scroll with it

---

### Post by screaminj3sus on 2012-03-16
Here's the bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/951121](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/951121)


But I'm fairly sure its actually because of this bug:
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414)

GTK 3.3.18 isn't handling events from touchpads correctly, resulting in these two issues.

---

### Post by mc4man on 2012-03-16
> **screaminj3sus said:**
> Here's the bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/951121](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/951121)


**But I'm fairly sure its actually because of this bug:**
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414)

GTK 3.3.18 isn't handling events from touchpads correctly, resulting in these two issues.

Well the 1st report is mine & was orig. just specific to scrolling **on** the thumb, not with it. But i'm not too sure anyone gets the distinction
Additionally I can't scroll **on** the thumb with a mouse either

Otherwise all scroll functions work with my touchpad - 
normal in window scrolling
grabbing the thumb & moving
clicking the arrow buttons on the thumb
repositioning the thumb & middle click for a 'quick' scroll to thumb position

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-16
So if I understand correctly, the bug still hasn't been fixed. I thought it has. Thanks. Guess we'll wait...

---

### Post by screaminj3sus on 2012-03-16
> **&#1058 said:**
> So if I understand correctly, the bug still hasn't been fixed. I thought it has. Thanks. Guess we'll wait...

It probably won't be fixed, until this is fixed:
[https://bugzilla.gnome.org/show_bug.cgi?id=672009](https://bugzilla.gnome.org/show_bug.cgi?id=672009)

---

### Post by screaminj3sus on 2012-03-20
This is now fixed for me with today's updates (both menus and overlay scrollbar)

---

### Post by cryptotheslow on 2012-03-20
Likewise - fixed for me with today's updates thankfully - it was a really annoying glitch for something so trivial.

---

### Post by screaminj3sus on 2012-03-20
> **cryptotheslow said:**
> Likewise - fixed for me with today's updates thankfully - it was a really annoying glitch for something so trivial.

Yeah, it was slowly driving me insane xD

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-20
Still exists here... :roll:

---

### Post by cryptotheslow on 2012-03-20
Did the latest updates hit your repository yet?

I believe the one that fixed it was libgtk-3-bin:amd64 (3.3.18-0ubuntu3, 3.3.18-0ubuntu4) for me. Only became available here a few hours back.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-20
It didn't by the time I posted my last reply. It's fixed on my machine now as well, thank God :D

---

### Post by cryptotheslow on 2012-03-20
Good stuff - now sanity can resume :D That one annoyed me so much I grabbed the xubuntu and lubuntu desktops to try out.

---

