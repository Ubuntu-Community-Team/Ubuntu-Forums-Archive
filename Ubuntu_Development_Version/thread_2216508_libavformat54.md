---
title: "libavformat54"
date: 2014-04-12
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2014-04-12
I have the moc ffmpeg installed for now.
Not being upgraded
```
The following packages have been kept back:
  libavformat54
```

---

### Post by QDR06VV9 on 2014-04-12
Sheese what an ordeal!! Finally just fed up and hand compiled fffmpeg by hand.
If you are as adventurous as I am, and know what you are getting yourself into Here is the the method I use,Before proceeding **be sure to remove the moc-ffmpeg pkg**, and install **nasm** and **yasm**.
[How to compile ffmpeg.]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide")
**Note:** When you get to the part of compiling ffmpeg <towards the bottom> it will look as if it is just hung be patient takes a while to populate.
Then when you are finally finished be sure to run ffmpeg in terminal.
Works very nice here, It Just Works Better.IMHO

---

### Post by monkeybrain20122 on 2014-04-12
I use ffmpeg from [https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=trusty](https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=trusty)
It is up to date (2.1.4) and is real ffmpeg rather than avconv. 

The compile guide only builds a local, static version of ffmpeg meant to be used as a standalone ffmpeg, but I need to build it as shared library, it is kind of messy and the system doesn't find the -dev files. Jon Severinsson's ppa is well known but it is horribly out of date because it replaces the system ffmpeg (avconv) and needs to be compatible. Samrog's is installed in /opt, I  then use galternative to make it the system default and compile media players with it. I can switch back to the system's if needed.

---

### Post by QDR06VV9 on 2014-04-12
That PPA is why I'm stuck.
I'm not sure what issues you are having with compiling from my suggested.
But Solved everything for me.

---

### Post by monkeybrain20122 on 2014-04-12
I don't know about trusty, I am using that ppa in 13.10 and have no problem. As trusty is still beta and ppas are not official I expect glitches at this stage, many ppas are not even set up so it will take time for things to settle down, no big deal (so I am not jumping on the 'early bird' bandwagon.)

I have no problem with compiling standalone ffmpeg with that guide but I have a problem when I try to compile other things against it (e.g vlc) since the compiler cannot find the developmental files and it will use the system ones instead so that kind of defeats the purpose. I don't use ffmpeg very much as a standalone application. I use it mostly as a shared library to compile other things.

---

### Post by QDR06VV9 on 2014-04-12
> **monkeybrain20122 said:**
> I don't know about trusty, I am using that ppa in 13.10 and have no problem. As trusty is still beta and ppa is not official I expect glitches at this stage, so no big deal (so I am not jumping on the 'early bird' bandwagon.)

I have no problem with compiling standalone ffmpeg with that guide but I have a problem when I try to compile other things against it (e.g vlc) since the compiler cannot find the developmental files and it will use the system ones instead so that kind of defeat the purpose. I don't use ffmpeg very much as a standalone application. I use it mostly as a shared library to compile other things.

Ok Understood!
But I have no problems with VLC **anymore**.
Files that would not work now work beautifully!

---

### Post by qyot27 on 2014-04-12
> **monkeybrain20122 said:**
> I have no problem with compiling standalone ffmpeg with that guide but I have a problem when I try to compile other things against it (e.g vlc) since the compiler cannot find the developmental files and it will use the system ones instead so that kind of defeats the purpose.
That's what the PKG_CONFIG_PATH and/or PKG_CONFIG_LIBDIR environment variables are for.

---

### Post by monkeybrain20122 on 2014-04-12
> **qyot27 said:**
> That's what the PKG_CONFIG_PATH and/or PKG_CONFIG_LIBDIR environment variables are for.

didn't work. Another problem is apt-get doesn't see them and still insists on installing the -dev files. Anyway my present setup works perfectly and I am not into experimenting with bleeding edge ffmpeg, just need things to work reasonably well and up to date.

---

### Post by andrew.46 on 2014-04-12
> **monkeybrain20122 said:**
> didn't work. Another problem is apt-get doesn't see them and still insists on installing the -dev files. 

If I had my Slackware hat on I would say that this is yet another demonstration of how dependency tracking + installation by a package management system is not freedom but actually a restrictive cage...

---

### Post by andrew.46 on 2014-04-18
> **monkeybrain20122 said:**
> I use ffmpeg from [https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=trusty](https://launchpad.net/~samrog131/+archive/ppa?field.series_filter=trusty)
It is up to date (2.1.4) and is real ffmpeg rather than avconv. 

Perhaps not so up to date, this 2.1 release version was actually taken from the development tree on *2013-10-28* with cherry-picked updates only since that time. The 2.2 release version however was cut from the development tree from *2014-03-01* so is a little more modern.

---

