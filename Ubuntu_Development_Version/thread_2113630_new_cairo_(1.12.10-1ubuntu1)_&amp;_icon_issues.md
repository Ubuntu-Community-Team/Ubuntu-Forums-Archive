---
title: "new cairo (1.12.10-1ubuntu1) &amp; icon issues"
date: 2013-02-07
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-02-07
Can show up in both unity & gnome-shell though much more common here in Unity.
Fairly easy to cause, (at least here), took only a few min. on a new current image install.
Usually comes from using spread multiple times in a session on un-maxed nautilus windows with a key binding, by default super+w will pull all from current ws.

Can be fairly minor or quite extensive, gets worse if using any custom colors, icons ect, or enabling picking from a window group instead of all.
Attached to top of bug report is a vid showing middle of the road nonsense, attached below is 2 screens from  new install, 2 nautilus home folders with a few borked icons in upper window

[https://bugs.launchpad.net/libcairo/+bug/1108333](https://bugs.launchpad.net/libcairo/+bug/1108333)

---

### Post by Harry33 on 2013-02-08
The cairo drawing issues are very often due to graphics drivers incompatibility with cairo rules. I remember much more severe issues a while back with nvidia-current driver.

Are you using nvidia proprietary dirvers?
Which graphics card model you have?

---

### Post by mc4man on 2013-02-08
This is being seen on a 8400m with nouveau, may try nvidia drivers later to see. (being a aged somewhat crappy laptop adapter it actually works a bit better with nouveau than nvidia drivers unless I force nvidia to always use max perf which is default on nouveau.

The screens & vid are relatively minor, on an install with a modded theme & the 're-enabling' of window picker for window group from all workspaces it gets much worse.

(- I've a new laptop with much better hardware, (nvidia GTX660m) but haven't yet decided how to address the current partitioning. From a multimedia standpoint have no issue with win7 & optimus ect. so don't want to remove it yet or ever.

If it doesn't go away on this laptop will just use the previous cairo for 13.04 unless I find the cause but the upgrade contained a boatload of commits so that may not happen.

Edit: seemingly fixed with new upstream cairo 1.12.12

---

### Post by Harry33 on 2013-02-11
> **mc4man said:**
> This is being seen on a 8400m with nouveau, may try nvidia drivers later to see. (being a aged somewhat crappy laptop adapter it actually works a bit better with nouveau than nvidia drivers unless I force nvidia to always use max perf which is default on nouveau.

The screens & vid are relatively minor, on an install with a modded theme & the 're-enabling' of window picker for window group from all workspaces it gets much worse.

(- I've a new laptop with much better hardware, (nvidia GTX660m) but haven't yet decided how to address the current partitioning. From a multimedia standpoint have no issue with win7 & optimus ect. so don't want to remove it yet or ever.

If it doesn't go away on this laptop will just use the previous cairo for 13.04 unless I find the cause but the upgrade contained a boatload of commits so that may not happen.

Edit: seemingly fixed with new upstream cairo 1.12.12

There is a new upstream verion available in RR now.
> cairo (1.12.14-0ubuntu1) raring; urgency=low    * New upstream version, fix rendering issue introduced in previous     versions (lp: #1119304)

---

