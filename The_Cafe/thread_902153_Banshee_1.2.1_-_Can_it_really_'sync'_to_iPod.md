---
title: "Banshee 1.2.1 - Can it really 'sync' to iPod?"
date: 2008-08-27
forum: The Cafe
---

### Post by kpkeerthi on 2008-08-27
> 
Rock out with Banshee 1.2

Play your music and videos. Stay entertained and up to date with podcasts and video podcasts. Discover new music with Last.fm radio. **[COLOR="Red"]Sync your iPod and other devices. [/COLOR]**We think you'll love the new Banshee!
... from [http://banshee-project.org/](http://banshee-project.org/)

I searched endlessly through all the available options. Can't find an option to sync my iPod. 

Can banshee 1.2.1 really 'sync' iPods? 

sync != transfer files manually by drag & drop.

---

### Post by RiceMonster on 2008-08-27
I see you're using arch (according to your avatar, anyway). I went through the pain of trying to compile banshee 1.2.1, and after adding the millions of deps, one of them wasn't in the repos (or at least it was named differently). If you're going to try it on  Arch, I'd reccomend you use the version in the repos (1.0, or something) or wait until it gets updated.

---

### Post by kpkeerthi on 2008-08-27
RiceMonster, I just grabbed the PKGBUILD from ABS. Changed the 'source' location to point it to 1.2.1 and added 'boo' to dependency and did **makepkg -cs**. It was this easy!

---

### Post by RiceMonster on 2008-08-27
Eck, why didn't I do that ](*,)

---

### Post by zachtib on 2008-08-27
I'm in the same boat. Transfer works fine, but I haven't yet figured out how to actually sync.

---

### Post by Tomosaur on 2008-08-27
I use a Creative Zen Vision:M, and although MTP support is generally fairly weak in Linux programs anyway, normal 'one at a time' transfers usually work fine. Banshee lets me do drag and drop, but I couldn't find any support for syncing either.

---

### Post by Changturkey on 2008-08-27
Try Songbird?

---

### Post by tdrusk on 2008-08-27
I could never figure out how to send songs to my ipod without transcoding.

---

