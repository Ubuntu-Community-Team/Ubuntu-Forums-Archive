---
title: "Kdenlive 0.7 is out"
date: 2008-11-13
forum: The Cafe
---

### Post by daverich on 2008-11-13
[http://www.kdenlive.org](http://www.kdenlive.org)

does anyone know how to make a .deb? - or indeed whether this will be included in Kubuntu backports?

Kind regards

Dave Rich

---

### Post by dr_kabuto on 2008-11-13
Marillat have it packaged already. Some good soul could make a good job in repackaging those, since debian dependencies are a bit different from ubuntu. A dirty job indeed...

---

### Post by DeadSuperHero on 2008-11-13
There's a useful script on kde-apps.org, lemme see...

[https://help.ubuntu.com/community/KdenliveSVN](https://help.ubuntu.com/community/KdenliveSVN)

---

### Post by daverich on 2008-11-13
doesn't that builder wizard only work in KDE3 however?

Kind regards

Dave Rich

---

### Post by DeadSuperHero on 2008-11-13
No, it works fine in KDE4, it even built the KDE4 version for me.

---

### Post by Ubuntiac on 2008-11-22
> **dr_kabuto said:**
> Some good soul could make a good job in repackaging those, since debian dependencies are a bit different from ubuntu.

Aye. Especially given that there seems to be problems running the Debian versions if you don't have backports enabled on Ubuntu 8.10 (Ubuntu 8.04 / Kubuntu are fine).

The builder wizard is really nice though. I just wish we had us some native .deb's... (thus my signature ;))

---

### Post by 3rdalbum on 2008-11-22
If anyone is considering just taking the contents of the Kdenlive and MLT packages for Debian and just chucking them into the filesystem on Ubuntu, then don't bother :-)  I tried that and although the program started, it said that all my video files were invalid and couldn't be imported.

Back to square one!

---

### Post by daverich on 2008-11-22
I find it strange that they haven't made a .deb file yet.

does anyone know is it going to be put into the backports for Ibex?

Kind regards

Dave Rich

---

### Post by cignale on 2008-12-14
I made some deb packages for Intrepid.

Look at my blog 

[http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/](http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/)

---

### Post by tadcan on 2008-12-14
Could you post a version of that in english please.

---

### Post by Ubuntiac on 2008-12-14
Loose translation courtesy of Google Translate:
[http://translate.google.com/translate?hl=en&u=http%3A%2F%2Fblog.linux-fueled.com%2F2008%2F12%2F14%2Fdeb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi%2F&sl=it&tl=en](http://translate.google.com/translate?hl=en&u=http%3A%2F%2Fblog.linux-fueled.com%2F2008%2F12%2F14%2Fdeb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi%2F&sl=it&tl=en)


So far it seems to have worked for me...

---

### Post by SunnyRabbiera on 2008-12-14
> **Ubuntiac said:**
> Loose translation courtesy of Google Translate:
[http://translate.google.com/translate?hl=en&u=http%3A%2F%2Fblog.linux-fueled.com%2F2008%2F12%2F14%2Fdeb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi%2F&sl=it&tl=en](http://translate.google.com/translate?hl=en&u=http%3A%2F%2Fblog.linux-fueled.com%2F2008%2F12%2F14%2Fdeb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi%2F&sl=it&tl=en)


So far it seems to have worked for me...

I hope it works in hardy as I will not update to ibex... too many issues.

---

### Post by tadcan on 2008-12-14
Thanks. Was able to install via the package manager.

Opened it, says it cannot find the Mlt profiles. Back to google.

---

### Post by billgoldberg on 2008-12-14
pff. 

I just had a horrible experience with linux movie editors.

I installed Open Movie Editor, it segfaults constantly.

I installed Kino, it get stuck when importing a picture, the cli output told me it can't handle those formats. (wtf?)

Then I compiled Lives, well tried to, it gave errors during installing.

I then tried Avidemux, again errors while compiling.

Then I tried Cinerella. After symlinking 50000 libs, I got it to work. It gave errors when I was rendering the video.

I eventually just settled on not editing the video and adding a mp3 track to it using the cli. It took 20 seconds.

I guess I'll take a look at Kdenlive when I feel like editing another movie.

---

### Post by cowanh00 on 2008-12-14
> **tadcan said:**
> Thanks. Was able to install via the package manager.

Opened it, says it cannot find the Mlt profiles. Back to google.

The path for Mlt is: /usr/share/mlt/profiles or at least it is for me! (Version 0.5 in the repos is old, try this [PPA]("https://launchpad.net/~baudm/+archive").)

---

### Post by tadcan on 2008-12-14
It probably wasn't made when I installed it. I don't have it.

Maybe it was because I used the package manager and not the command line?

Never used PPA before is it a new release?

---

### Post by cowanh00 on 2008-12-14
> **tadcan said:**
> It probably wasn't made when I installed it. I don't have it.

A PPA is a Personal Package Archive. It is basically where someone builds a package that isn't included in Ubuntu yet. Make sure you install Kdenlive 0.7 for that Mlt path to work.

---

### Post by tadcan on 2008-12-14
I reinstalled it with the command line. Have got past that problem.

---

### Post by forrestcupp on 2008-12-14
> **billgoldberg said:**
> pff. 

I just had a horrible experience with linux movie editors.

I installed Open Movie Editor, it segfaults constantly.

I installed Kino, it get stuck when importing a picture, the cli output told me it can't handle those formats. (wtf?)

Then I compiled Lives, well tried to, it gave errors during installing.

I then tried Avidemux, again errors while compiling.

Then I tried Cinerella. After symlinking 50000 libs, I got it to work. It gave errors when I was rendering the video.

I eventually just settled on not editing the video and adding a mp3 track to it using the cli. It took 20 seconds.

I guess I'll take a look at Kdenlive when I feel like editing another movie.

Yeah, basically all of those you listed are useless, except Cinelerra.  Did you use the [Cinelerra **CV**](http://cinelerra.org/getting_cinelerra.php#ubuntu) repos?  It should be painless if you install it that way.  It's definitely worth it to use the CV version instead of the official version.  Cinelerra is pretty awesome.

But if you're doing fairly simple stuff, Kdenlive is pretty awesome, too.  Hopefully this new version has fixed some of the bugs.

---

### Post by Changturkey on 2008-12-14
There is a fork of Cinelerra called Lumiera I believe. Still in pre-alpha.

---

### Post by EdThaSlayer on 2008-12-14
You guys are making this all so difficult.

Just visit [https://help.ubuntu.com/community/KdenliveSVN](https://help.ubuntu.com/community/KdenliveSVN) and read.

Even a user like me installed it pretty quickly.

Enjoy!):P

---

### Post by shadowdude1794 on 2008-12-14
Lumiera (correct me if I'm wrong) is only for editing single movie files, not for making movies. Cinelerra and Kdenlive are the best, and I prefer Kdenlive because it's simpler.

---

### Post by Guruji on 2008-12-15
> **shadowdude1794 said:**
> Lumiera (correct me if I'm wrong) is only for editing single movie files, not for making movies. Cinelerra and Kdenlive are the best, and I prefer Kdenlive because it's simpler.

Lumiera is a fork of Cinelerra, so i guess it will have similar capabilities.

---

### Post by kpkeerthi on 2008-12-15
Great news. How stable/crashy is kdenlive now? 

(I'm waiting for a K3B KDE4 port.)

---

### Post by Ubuntiac on 2008-12-15
There's still some bugs being ironed out, but it is much, much more stable than the repo versions (the last of which were SVN grabs not meant to be used publicly). It's also quite a bit faster than it was and with a bunch of nice video screen capture stuff built in.

I never really got 0.5/0.6 to work properly for me, but 0.7 seems to be really nice (especially with DV / HDV / MPEG), and 0.7.1 is due out in the next couple of weeks.


I'm really looking forward to a KDE4 port of K3B, too. I've heard there is one somewhere around, but that there's still some polishing left to do before releasing it.

---

