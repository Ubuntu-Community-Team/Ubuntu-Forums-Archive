---
title: "Warning re: Mesa 8.0 r600g vs ATI HD3200 M"
date: 2012-01-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ibidem on 2012-01-14
I see that Mesa 8.0 has been branched, that that's the plan for Precise, and that packages have already hit xorg-edgers.
I have one install of Precise (using fglrx-updates), and one install of Debian Squeeze with an updated kernel (3.0.x) and a custom build of Mesa, straight from git HEAD.
Somewhere around August, a patch involved in adding Evergreen support broke GL with Mesa on this card.  Ever since then, trunk Mesa has shown different variations of snow when using glxgears or Google Earth.  There is a bug report upstream ([https://bugs.freedesktop.org/show_bug.cgi?id=43405](https://bugs.freedesktop.org/show_bug.cgi?id=43405)), but it's awaiting tests on Evergreen which currently seem unlikely to ever occur.  I'm hoping that Precise will force the issue, though.

So if you update Mesa to 8.0 and have ATI HD3xxx/RS780M graphics, be sure that you have a way to recover.  Specifically, you may want to use a 2-D window manager until you have verified that OpenGL is semi-functional; if you don't do this, be prepared to recover from text mode or another install.
Also, be sure to link to the upstream bug on launchpad.

---

### Post by Harry33 on 2012-01-14
> **Ibidem said:**
> I see that Mesa 8.0 has been branched, that that's the plan for Precise, and that packages have already hit xorg-edgers.
I have one install of Precise (using fglrx-updates), and one install of Debian Squeeze with an updated kernel (3.0.x) and a custom build of Mesa, straight from git HEAD.
Somewhere around August, a patch involved in adding Evergreen support broke GL with Mesa on this card.  Ever since then, trunk Mesa has shown different variations of snow when using glxgears or Google Earth.  There is a bug report upstream ([https://bugs.freedesktop.org/show_bug.cgi?id=43405](https://bugs.freedesktop.org/show_bug.cgi?id=43405)), but it's awaiting tests on Evergreen which currently seem unlikely to ever occur.  I'm hoping that Precise will force the issue, though.

So if you update Mesa to 8.0 and have ATI HD3xxx/RS780M graphics, be sure that you have a way to recover.  Specifically, you may want to use a 2-D window manager until you have verified that OpenGL is semi-functional; if you don't do this, be prepared to recover from text mode or another install.
Also, be sure to link to the upstream bug on launchpad.

Actually the mesa 8.0 is not at all published yet. The branch (git version) you find in xorg-edgers for example, is still far from being mesa 8.0 (or 7.12). It is just an early git version on the road towards 8.0.

---

### Post by Ibidem on 2012-01-14
When I say "8.0", I don't mean "the official 8.0 release"; I'm using the versioning that Mesa reports (currently should be 8.0; was 7.12 until recently).
This refers to the version which is in progress.
Assuming that it represents the upstream code,  it's about 1 month from final, and has all the features.

By saying that 8.0 has been branched, I mean that the branch which will contain all 8.0.x releases has been branched.

But yes, the version in xorg-edgers, and the one planned for Precise, should be affected by this bug until/unless it gets fixed.

---

### Post by Harry33 on 2012-01-14
> **Ibidem said:**
> When I say "8.0", I don't mean "the official 8.0 release"; I'm using the versioning that Mesa reports (currently should be 8.0; was 7.12 until recently).
This refers to the version which is in progress.
Assuming that it represents the upstream code,  it's about 1 month from final, and has all the features.

By saying that 8.0 has been branched, I mean that the branch which will contain all 8.0.x releases has been branched.

But yes, the version in xorg-edgers, and the one planned for Precise, should be affected by this bug until/unless it gets fixed.

Right,
the bug is an upstream one.

---

