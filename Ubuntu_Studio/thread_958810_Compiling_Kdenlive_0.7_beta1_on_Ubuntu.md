---
title: "Compiling Kdenlive 0.7 beta1 on Ubuntu"
date: 2008-10-25
forum: Ubuntu Studio
---

### Post by DarkDead on 2008-10-25
Hi guys,

The version of kdenlive in the ubuntu repositories is quite old and doesn't include many features of the recent version. I once tried hard to compile the version 0.6 of kdenlive but with no success. I had no problems compiling mlt, mlt++ or even ffmpeg but I never succeeded with the kdenlive.

Well, now that version 0.7 came out I decided to give it a try again using [_this guide_]("http://www.kdenlive.org/compile"). Again no problems with mlt, mlt++ or ffmpeg. But when I use the cmake command required before compiling kdenlive I get this:
```
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:35 (MESSAGE):
  ERROR: Could not find KDE4 kde4-config
```
It seems I need to install almost all components of KDE4. That's what happens in the step 2 of [_this other guide_]("https://help.ubuntu.com/community/KdenliveSVN"). That's a lot of packages and it could not even work after all.

So, my questions are:
Has anyone compiled kdenlive 0.7 successfully on Ubuntu?
Is there any way to avoid installing all KDE4 components?
When will the repositories be updated?

Thanks in advance for any help ;).

---

### Post by 1GENNADIY1 on 2008-10-26
Helo, @DarkDead!
I tried succesfull this tutorial: [http://www.kde-apps.org/content/show.php?content=85826&forumpage=0&PHPSESSID=22472764dbf079761a5aa374aa977cfd](http://www.kde-apps.org/content/show.php?content=85826&forumpage=0&PHPSESSID=22472764dbf079761a5aa374aa977cfd)
with KDE 4.1 and Ubuntu 8.04.
I have a problem with soundtransition - it is twisted. When I do swapping of two clips comes interruption, equal whether with 'fade in/fade out' or not.
Thank you!
Gennadiy

---

### Post by DarkDead on 2008-10-26
Thanks 1GENNADIY1 but to use that tutorial I would have to install KDE4 just as happens with the tutorials I've found.
My point was to see if anyone had already compiled kdenlive on Ubuntu just using some components of KDE4.

About your soundtransition problem I don't have any idea. Sorry.

---

### Post by cotcot on 2008-10-26
I followed the tutorial from the kdenlive wiki. You need kdebase and kdebase-dev.

---

### Post by bato on 2008-12-01
I had the same problem. I solved installing **kdelibs5-dev**, then I had to install **gettext** too.

In this moment I'm compiling kdenlive! 

Hope it helps you

---

### Post by cignale on 2008-12-14
i've made some deb packages too.

look at my blog post

[http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/](http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/)

---

### Post by DarkDead on 2008-12-14
Thanks a lot cignale.
It asks for a lot of dependencies which in their turn ask for even more. Basically it would install kde and right now I haven't got enough disk space. I'll give it a try latter and post the results.
Meanwhile if anyone tries the package please post the outcome.

---

### Post by argoo on 2008-12-31
If you follow the [guide]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/installing-source") on the kdenlive site, you only need to install libqt4-dev and kdelibs5-dev.  Then, you need to add kde4-config to your PATH as follows and compile using their instructions.

export PATH=/usr/lib/kde4/bin:$PATH

The only issue is that the application looks ugly without kdebase.

---

