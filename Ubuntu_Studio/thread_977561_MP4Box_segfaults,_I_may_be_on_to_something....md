---
title: "MP4Box segfaults, I may be on to something..."
date: 2008-11-10
forum: Ubuntu Studio
---

### Post by zackiv31 on 2008-11-10
So been screwing around with MP4Box in Intrepid, and I noticed some weird behavior. Don't know if its Ubuntu, or MP4Box...  but I run the following two commands:

```

me@ME:~/.makevids$ MP4Box -aviraw video /home/me/.makevids/ABC.mov -out /home/me/ABC.h264
Extracting AVI video (format h264) to /home/me/ABC_video.h264
me@ME:~/.makevids$ MP4Box -aviraw video /home/me/.makevids/ABC.mov -out /home/me/.makevids/ABC.h264
*** buffer overflow detected ***: MP4Box terminated

```


The first command works fine, but the second doesn't!  What doesn't Ubuntu/MP4Box like?  The directory is perfectly valid/writeable, so what's going on?

---

### Post by GordonZola on 2008-11-11
There's a problem with MP4Box 0.4.4 and files over a certain size (2GB I think).

---

### Post by DVS999 on 2008-11-11
May well be related to [https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/273075](https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/273075)

---

### Post by zackiv31 on 2008-11-11
I should have made it more obvious... but if I use a directory that doesn't start with a "." then it works fine... those two directories have the same permissions.

so 

"makevids"   works perfectly fine...
".makevids"  segfaults

---

### Post by Selur on 2008-11-18
doesn't work here even when not using a dot at,..
```
MP4Box -fps 25 -par 1=1:1 -add "/home/selur/Desktop/test.264"#video -add "/home/selur/Desktop/test.aac"#audio -sbr -brand avc1 -new "/home/selur/Desktop/test.mp4"
```
-> *** buffer overflow detected ***: MP4Box terminated     :cry:

It's probably related to aac sbr handling inside mp4box. :(

---

### Post by mocha on 2008-11-22
This bug just put a stop on the mencoder scripts I use.  Does anyone know if the gpac people are aware of this?  Is it an ubuntu only issue?

---

### Post by kxmas on 2009-01-25
> **mocha said:**
> This bug just put a stop on the mencoder scripts I use.  Does anyone know if the gpac people are aware of this?  Is it an ubuntu only issue?

It appears to be an ubuntu only issue.  :(

debian-multimedia.org has updated gpac recently.  Yet, their source package results in the same buffer overflow.  [http://www.debian-multimedia.org/dists/unstable/main/binary-amd64/package/gpac.php]("http://www.debian-multimedia.org/dists/unstable/main/binary-amd64/package/gpac.php") 

I've switched to the mpeg4ip packages.

---

### Post by kingmoffa on 2009-10-26
I've been trying to use a program from the gpac collection. 

MP4Box -hint xxxxx.mp4 

in a script - it has problems and errors. 

Using it through a proper shell via SSH and it works fine. 

This is with gpac on an intrepid box with the default version from the repos. (0.4.4 i think).

Tried building from source 0.4.5 and ran into problems.

---

