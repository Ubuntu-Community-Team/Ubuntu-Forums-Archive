---
title: "Request: Rhythmbox 0.9.0"
date: 2005-08-10
forum: Requests
---

### Post by vvlist on 2005-08-10
It's finally here, after a 10 month wait! This can't be hard to backport. It says it has better memory usage and stability though.

---

### Post by SKLP on 2005-08-10
With the official backports it IIRC won't be backported before it has hit breezy...

and it hasn't.

---

### Post by vvlist on 2005-08-10
That's too bad :( I wanted it to hold me over until the new Sonance release, oh well muine will have to do for now.

---

### Post by SKLP on 2005-08-10
Sonance is progressing nicely :)

tried yesterdays CVS

and it's no longer called Sonance -- It's called Banshee.

It looked VERY nice. However it was very buggy/incomplete.

1.0 is going to be nice :)

---

### Post by pulp on 2005-08-10
loving rhythmbox. seconding this request

---

### Post by vvlist on 2005-08-10
Yeah I'm excited about Sonance err Banshee, hows the iPod support? I've been waiting for a stable release for months.

---

### Post by charlieg on 2005-08-10
[QUOTE=SKLP]With the official backports it IIRC won't be backported before it has hit breezy...

and it hasn't.[/QUOTE]
Corey begs to differ:
[http://www.ubuntuforums.org/showpost.php?p=295899&postcount=29](http://www.ubuntuforums.org/showpost.php?p=295899&postcount=29)

---

### Post by vvlist on 2005-08-10
So.......Does anyone think it could be backported? I'd love to give it a try.

---

### Post by SKLP on 2005-08-10
Corey probably meant 0.8.99 is in breezy. 
I just did an apt-get update and no new rhythmbox...

---

### Post by SKLP on 2005-08-10
[QUOTE=vvlist]Yeah I'm excited about Sonance err Banshee, hows the iPod support? I've been waiting for a stable release for months.[/QUOTE]Well, the iPod support seems to be a big priority for Banshee. However, as of current CVS, you cant even play songs :)

---

### Post by RastaMahata on 2005-08-10
Well, I tried to make a deb package (I didnt try to compile), but it needed some unavailable libraries, so I guess we'll have to wait for breezy :/

---

### Post by vvlist on 2005-08-11
[QUOTE=SKLP]Well, the iPod support seems to be a big priority for Banshee. However, as of current CVS, you cant even play songs :)[/QUOTE]

Have they changed the website? Because they haven't updated the name on Aaron's site to Banshee yet.

---

### Post by pulp on 2005-08-11
[ftp://ftp.ubuntu.com/ubuntu/pool/main/r/rhythmbox/](ftp://ftp.ubuntu.com/ubuntu/pool/main/r/rhythmbox/)

The .deb hit breezy.

---

### Post by ntd on 2005-08-11
[QUOTE=pulp][ftp://ftp.ubuntu.com/ubuntu/pool/main/r/rhythmbox/](ftp://ftp.ubuntu.com/ubuntu/pool/main/r/rhythmbox/)

The .deb hit breezy.[/QUOTE]
 Yet another person hoping for a backport :)

Edit: the totem-plparser that configure wants is in the libtotem-plparser (IIRC) package that has already been backported...so it looks like everything required to build it is available...I'm going through a build now and will edit if it works

Edit: Yup, works very well actually :D...seems much more responsive than previous versions...if you want it to build, just do a `sudo apt-get install libtotem-*` and that'll take care of the totem-plparser dependenct

---

### Post by Gnobody on 2005-08-11
[QUOTE=ntd]Yet another person hoping for a backport :)

Edit: the totem-plparser that configure wants is in the libtotem-plparser (IIRC) package that has already been backported...so it looks like everything required to build it is available...I'm going through a build now and will edit if it works

Edit: Yup, works very well actually :D...seems much more responsive than previous versions...if you want it to build, just do a `sudo apt-get install libtotem-*` and that'll take care of the totem-plparser dependenct[/QUOTE]
 I'm not finding anything with libtotem-, and yes I have backports!

---

### Post by RastaMahata on 2005-08-12
[QUOTE=Gnobody]I'm not finding anything with libtotem-, and yes I have backports![/QUOTE]
 no libtotem here neither

---

### Post by drummer on 2005-08-13
[QUOTE=RastaMahata]no libtotem here neither[/QUOTE]
 I get this:```
$ apt-cache search libtotem
libtotem-plparser-dev - Totem Playlist Parser library - development version
```but can't install that because there is no libtotem-plparser on which it depends (a little pointless). I also can't install the deb from Breezy, far too many dependancy issues. Can't compile either, also dep issues for debs I can't find in apt:```
checking for              gtk+-2.0 >= 2.5.4  libgnomeui-2.0                                   libglade-2.0  gnome-vfs-2.0 >= 2.6                     gnome-vfs-module-2.0  totem-plparser >= 1.1.3                  ... Requested 'totem-plparser >= 1.1.3' but version of totem-plparser is 1.1.1

configure: error: Library requirements (                  gtk+-2.0 >= 2.5.4  libgnomeui-2.0                                   libglade-2.0  gnome-vfs-2.0 >= 2.6                     gnome-vfs-module-2.0  totem-plparser >= 1.1.3                  ) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```
Another funny thing is totem-plparser, it wants 1.1.3, and says I have 1.1.1 ... I can't see either in apt ?!?

---

### Post by doclivingston on 2005-08-13
totem-plparser gets built as a part of totem, although in breezy, and I think backports as well, it's in its own package.

I've just checked and it appears that totem 1.1.1 is the latest version in backports, you'll have to wait until totem 1.1.3 (or 1.1.4) is included before you can get Rhythmbox 0.9.0. The newer version of totem is the only extra requirement over a Gnome 2.10 desktop.

---

### Post by SKLP on 2005-08-16
[QUOTE=SKLP]However, as of current CVS, you cant even play songs :)[/QUOTE]
With Banshee from current cvs, I'm happy to report I can play songs (even AACs)  ;-)

---

### Post by drummer on 2005-08-16
[QUOTE=SKLP]With Banshee from current cvs, I'm happy to report I can play songs (even AACs)  ;-)[/QUOTE]
 How did you compile the Banshee CVS? I tried to but it needed mono 1.1.8, whereas Hoary has 1.1.7 ... I also downloaded the latest mono and it installed into my home directory, but I don't know how to compile CVS using that version.

---

### Post by SKLP on 2005-08-16
[QUOTE=drummer]How did you compile the Banshee CVS? I tried to but it needed mono 1.1.8, whereas Hoary has 1.1.7 ... I also downloaded the latest mono and it installed into my home directory, but I don't know how to compile CVS using that version.[/QUOTE]I'm on Breezy :)

---

### Post by drummer on 2005-08-17
[QUOTE=SKLP]I'm on Breezy :)[/QUOTE]
 :( .. I guess I'll just wait :P

---

### Post by jbo on 2005-08-24
Waiting for the breezy release is kind of a fun experience. I feel like I am 10 years old and waiting for christmas to finally come. Not to often you have something fun to look forward to these days.. :P

---

### Post by drummer on 2005-08-24
[QUOTE=jbo]Waiting for the breezy release is kind of a fun experience. I feel like I am 10 years old and waiting for christmas to finally come. Not to often you have something fun to look forward to these days.. :P[/QUOTE]
 I know exactly what you mean, I'm practically jumping out of my skin in anticipation.. only 2 months to go now :D

---

