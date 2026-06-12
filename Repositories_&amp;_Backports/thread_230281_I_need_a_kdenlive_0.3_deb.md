---
title: "I need a kdenlive 0.3 deb"
date: 2006-08-05
forum: Repositories &amp; Backports
---

### Post by insulae on 2006-08-05
first: sorry for my english =)
i use ubuntu Dapper

i need a package of kdenlive 0.3 ([http://kdenlive.sourceforge.net/](http://kdenlive.sourceforge.net/)) i try using a sid repository from Christian Marillat (deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main) but i have the next unresolved dependences:
```

  kdenlive: 
     Depende: kdelibs4c2a (>= 4:3.5.4-1) pero 4:3.5.4-0ubuntu2~dapper1 
     Depende: libc6 (>= 2.3.6-6) pero 2.3.6-0ubuntu20 
     Depende: libfreetype6 (>= 2.2) pero 2.1.10-1ubuntu2.2
     Depende: libgcc1 (>= 1:4.1.0) pero 1:4.0.3-1ubuntu5
     Depende: libiec61883-0 pero no va a instalarse
     Depende: libmlt++0 (>= 0.2.0) pero no va a instalarse
     Depende: libmlt0 (>= 0.2.0) pero no va a instalarse
     Depende: libraw1394-8 pero no va a instalarse
     Depende: libstdc++6 (>= 4.1.0) pero 4.0.3-1ubuntu5

```
where i can find a kdenlive deb for dapper, i search in google but i dont have luck =(.

Thanks!

---

### Post by zeekoe on 2006-08-11
Perhaps not exactly what you want, but there's more in the world than Kino:
[http://www.ohloh.net/opensource/directory/non-linear_editor](http://www.ohloh.net/opensource/directory/non-linear_editor)
* kdenlive, has no debs
* lives, has an ubuntu deb, but don't have it to work yet (someone suggested it might be something with jack and that I need to use OSS and that ~/.lives and ~/.jackdrc have something to do with it, but they are overwritten after each lives run)

I found these after quite a bit of googling; now some keywords so that others who want to do the same thing can find it earlier:
I wanted to use Kino with an MJPEG file, couldn't get ffmpeg to convert to DV, tried Cinelerra which has some debs but crashed often (segfault) and then found above mentioned URL.

---

