---
title: "The enemies of Wayland"
date: 2019-05-20
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-05-20
Top bar is missing running mpv in Ubuntu Wayland.
I opened a bug: [https://bugs.launchpad.net/ubuntu/+source/mpv/+bug/1829712](https://bugs.launchpad.net/ubuntu/+source/mpv/+bug/1829712)
and a developer replied: mpv in Wayland is a pure native Wayland app. This means it has no "top bar" 
If this is the attitude of the developers Wayland will never be adopted

---

### Post by Frogs Hair on 2019-05-20
Bug Report refers to 19.10, moved to *Ubuntu Development Version*.

---

### Post by amano on 2019-05-21
Well, one possibility would be to use gnome-mpv which draws a client
-side decoration. Mpv itself is cross platform and wants to stick to the Windows style server-side concept.

---

### Post by corradoventu on 2019-05-22
In fact to bypass the problem I use gnome-mpv  or as suggested by mc4man 
>  For 19.04/19.10 to get deco for mpv in a wayland session you'd need to use
--gpu-context=x11egl
The above can also provide vaapi hwdec but only vaapi-copy
but my post was about Wayland and I think that as long as there are similar problems wayland will find it hard to succeed

---

### Post by cruzer001 on 2019-05-22
Wayland will one day shine like it needs to and when it does I think we will know by it being default in the LTS releases.

---

### Post by hk42 on 2019-07-13
Hi
I'm a happy user of Ubuntu 19.04 on a Beelink BT3 mini PC 4 G ram 64 G emmc  dual boot with W10
May be I'm lucky but I have yet to see any difference when choosing wayland at login.
Any link to teach me the differences is welcome.

---

### Post by cariboo on 2019-07-13
Thread Closed.

---

