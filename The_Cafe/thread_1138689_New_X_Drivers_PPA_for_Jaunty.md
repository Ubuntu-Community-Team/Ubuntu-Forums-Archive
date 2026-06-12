---
title: "New X Drivers PPA for Jaunty"
date: 2009-04-26
forum: The Cafe
---

### Post by ghindo on 2009-04-26
It seems that the X people from Canonical have heard our pleas for better X performance in Jaunty, and have answered with an official PPA:[quote="Bryce Harrington of Canonical"]We've started getting requests for new versions of X drivers, that
unfortunately missed the freeze deadline for Jaunty.

I've established a PPA for where updated drivers can be posted:

  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

I've pre-seeded it with some of the simpler ones to update.  If you're
in ubuntu-x-swat, please feel free to add to the collection.  It would
be nice to have mesa 7.4.1, -intel 2.7, and the new restricted drivers.

The idea here is to provide stable updates that we believe should
improve things beyond the stock install.  So no git snapshots (unless
Debian is carrying them), and nothing requiring newer kernel or
xserver.  Drivers that require new libdrm or other libs are ok, so long
as we also provide those deps in this ppa.

Bryce[/quote][https://lists.ubuntu.com/archives/ubuntu-x/2009-April/000518.html](https://lists.ubuntu.com/archives/ubuntu-x/2009-April/000518.html)

---

### Post by Kareeser on 2009-04-26
New intel drivers? Let's see how this changes the performance on my i855 :)

---

### Post by Mazza558 on 2009-04-26
What would really help is if these were tested enough to be added as an official update. That way, every intel graphics user who doesn't know how to add a PPA will suddenly get a performance boost after the updates.

---

### Post by hanzomon4 on 2009-04-26
Well then get to testing! j/k

---

### Post by =^,^= on 2009-04-26
Does this include any ati driver updates?

---

### Post by Kareeser on 2009-04-26
I think at this point, the best we can hope for is backporting, and only for those who've enabled the backports repository :P

---

### Post by Giant Speck on 2009-04-26
I don't actually see any packages on that website...

---

### Post by Daisuke_Aramaki on 2009-04-26
> **Giant Speck said:**
> I don't actually see any packages on that website...

right click on the source driver names and open it in a new tab, you will see the packages.

---

### Post by Giant Speck on 2009-04-26
> **Daisuke_Aramaki said:**
> right click on the source driver names and open it in a new tab, you will see the packages.

Thanks!  I would have never thought of that!

---

### Post by gletob on 2009-04-26
I'm on an Intel i965 and my results amaze me.  Running with no issues yet.

Old glxgears
```
2968 frames in 5.0 seconds = 593.453 FPS
3038 frames in 5.0 seconds = 607.432 FPS
3037 frames in 5.0 seconds = 607.384 FPS
2888 frames in 5.0 seconds = 577.478 FPS
```
New glxgears
```
27160 frames in 5.0 seconds = 5431.944 FPS
37861 frames in 5.0 seconds = 7572.053 FPS
34632 frames in 5.0 seconds = 6926.389 FPS
32513 frames in 5.0 seconds = 6502.451 FPS

```

---

### Post by steeleyuk on 2009-04-26
Big difference here on the laptop as well. While Compiz is NOT running, the jump with glxgears was from ~210 to ~1360 FPS. With Compiz, not much difference.

---

### Post by Kareeser on 2009-04-26
> **gletob said:**
> I'm on an Intel i965 and my results amaze me.  Running with no issues yet.

Old glxgears
```
2968 frames in 5.0 seconds = 593.453 FPS
3038 frames in 5.0 seconds = 607.432 FPS
3037 frames in 5.0 seconds = 607.384 FPS
2888 frames in 5.0 seconds = 577.478 FPS
```
New glxgears
```
27160 frames in 5.0 seconds = 5431.944 FPS
37861 frames in 5.0 seconds = 7572.053 FPS
34632 frames in 5.0 seconds = 6926.389 FPS
32513 frames in 5.0 seconds = 6502.451 FPS

```

Sweet Jesus, that's a big jump. After upgrading, my glxgears result is comparable to your PRE-upgrade result!

Intel 855GM here.

---

### Post by ghindo on 2009-04-26
I'm using Intel graphics and I'm not sure how much of a difference this is making.  Compiz still doesn't work, but that's probably because my chipset is still blacklisted.> **Giant Speck said:**
> I don't actually see any packages on that website...Follow [these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") to enable the PPA.  Then, just check for updates and install said updates.

---

### Post by Zorael on 2009-04-26
glxgears numbers can be deceiving, since it's not benchmarking what you think it's doing. Even if one driver has twice the glxgears fps of another driver, the second one could still have better rendering performance. The only thing that tells you is that the first one writes to the screen faster; the actual animation (gears turning) is so simple it doesn't begin to tax your graphical processor. Even if the first one has twice the glxgears fps of the second one, the second one could still have twice the "real world" game fps of the first one.

It's not exactly like deciding which car runs faster by the time they can lower the windows, but it's not far off.

---

### Post by Giant Speck on 2009-04-27
Compiz still doesn't work 100%  :(

I was hoping this would help. :(

---

### Post by steeleyuk on 2009-04-27
> **Zorael said:**
> glxgears numbers can be deceiving, since it's not benchmarking what you think it's doing. Even if one driver has twice the glxgears fps of another driver, the second one could still have better rendering performance. The only thing that tells you is that the first one writes to the screen faster; the actual animation (gears turning) is so simple it doesn't begin to tax your graphical processor. Even if the first one has twice the glxgears fps of the second one, the second one could still have twice the "real world" game fps of the first one.

It's not exactly like deciding which car runs faster by the time they can lower the windows, but it's not far off.

I know that, someone else mentioned it in another thread. Its still a substantial enough difference though to suggest that there is something wrong somewhere, with the older drivers... from what I can tell anyway.

---

### Post by Jay_Bee on 2009-04-27
I installed drivers from this repo, enabled uxa acceleration, removed compiz blacklist and now everything works on my integrated intel x3100 (GM965), no freezing or anything :)

---

### Post by snd242 on 2009-05-02
Still "no-go" for movies with ATI R600 + compiz enabled! When effects are disabled i can watch movies but the quality of the playback is **worse** than the open ATI drivers (radeon). 
This release of fglrx driver is a litle bit better. Now i can minimize/maximize windows and adjust display properties. I even have played Unreal tournament 99, the performance is **inadequate.** My shitware is ATI 3650 HD on agp slot with 512 megs ddr2, works well under Uncle Bill's OS.


p.s. English is not my first language!

---

