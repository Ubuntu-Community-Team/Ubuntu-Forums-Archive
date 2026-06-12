---
title: "[SOLVED] Decrypt DVD's"
date: 2007-10-20
forum: The Cafe
---

### Post by ninja_in_pajamas on 2007-10-20
I'm trying to decrypt a dvd, more precisely Transofrmers because I am setting up a video/music server for my home.  Someone mentioned Mencoder but that process is WAY too complicated for me.  DVD Decrypter through wine doesn't see my dvd drive (on a laptop).  Is there any easy way to do this?

---

### Post by Incense on 2007-10-20
> **ninja_in_pajamas said:**
> I'm trying to decrypt a dvd, more precisely Transofrmers because I am setting up a video/music server for my home.  Someone mentioned Mencoder but that process is WAY too complicated for me.  DVD Decrypter through wine doesn't see my dvd drive (on a laptop).  Is there any easy way to do this?

```
sudo apt-get install k9copy
```

you can rip the dvd to an mpeg file, or an iso for "backup". Cheers.

---

### Post by saulgoode on 2007-10-20
[http://thoggen.net/](http://thoggen.net/)

---

### Post by Spr0k3t on 2007-10-20
Isn't Xformers on a Sony disc?  If so, good luck.

---

### Post by sloggerkhan on 2007-10-20
I am a big thoggen fan, too.

---

### Post by Incense on 2007-10-21
> **Spr0k3t said:**
> Isn't Xformers on a Sony disc?  If so, good luck.

k9copy is the only program I've seen that will get the newer sony titles. Worked for 007 at least. . . .

---

### Post by Spr0k3t on 2007-10-21
> **Incense said:**
> k9copy is the only program I've seen that will get the newer sony titles. Worked for 007 at least. . . .

So noted... I'll be testing a few tomorrow.  For the MCE of course.

---

### Post by ninja_in_pajamas on 2007-10-23
Have tried K9Copy and it crashes a few seconds after it starts up (using Gutsy). I'll try thoggen though and see what happens.

---

### Post by ninja_in_pajamas on 2007-10-30
Figured it out.  needed the libcss files.

---

### Post by Ciego on 2007-11-29
What packages did you install to fix the problem?

---

### Post by Polygon on 2007-11-30
the package is libdvdcss2 but it is only available in the medibuntu repos, due to legal reasons.

this package pretty much enables dvd playback (along with libdvdread and libdvdnav) for all linux media players, except for vlc, which just has it built in ;)

---

### Post by Meson on 2008-06-21
> **ninja_in_pajamas said:**
> DVD Decrypter through wine doesn't see my dvd drive (on a laptop).

You need to tell Wine to run DVD Decrypter in Windows NT mode.

---

### Post by Skipster on 2012-07-08
see this thread:
[http://ubuntuforums.org/showthread.php?t=1737727](http://ubuntuforums.org/showthread.php?t=1737727)

---

### Post by Primefalcon on 2012-07-08
dvd shrink under wine works good, also acid rip is great..

disclaimer: only rip dvd's that you lgally have the righ to, under fair use or.. that you legally have the right to...

---

### Post by coffeecat on 2012-07-08
Back to sleep, very old thread.

---

