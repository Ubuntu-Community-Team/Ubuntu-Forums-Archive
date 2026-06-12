---
title: "music question?"
date: 2008-08-02
forum: Ubuntu Studio
---

### Post by jooking on 2008-08-02
what kinds of files do the music files have to be to be able to play them? i have mp3's. but i dont think they work because amarok and the other music program arent playing them. my sound works though, i can go on other sites and listen to them. what type of file does the song have to be?

---

### Post by pytheas22 on 2008-08-02
By default, for legal and philosophical reasons, Ubuntu doesn't come with codecs installed for playing mp3's and other proprietary kinds of media (you can only play .ogg files, which is a free format).  But it's easy to install all the codecs you need:

First, go to System>Administration>Software Sources and under the "Ubuntu Software" tab, make sure that all of the repositories in the list are enabled (the source-code one is optional).

Then type in a terminal:
```

sudo apt-get install ubuntu-restricted-extras
```

and you should be able to play mp3's.

Also, if you try to open an mp3 using "Movie Player" (aka "totem"), I think it will prompt you to download mp3 support automatically if you don't have it.

---

### Post by K2712 on 2008-08-02
> Also, if you try to open an mp3 using "Movie Player" (aka "totem"), I think it will prompt you to download mp3 support automatically if you don't have it.

I can confirm that, I just installed a fresh copy of Xubuntu and went to play a music file and was prompted to download codecs.  Took about 15 seconds and I was all set.

It's amazing how far Ubuntu has come since 5.04.:)

---

### Post by jooking on 2008-08-02
i dled all the extras and i have the packages, i dont get asked to install any codecs, so how do u get it to do that? could there be another way to get it>? i used totem and it wouldnt ask me for the codecs. i have no muuuuusicc!! really need help.

---

### Post by K2712 on 2008-08-02
Do you have the following installed?

gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly

---

### Post by jooking on 2008-08-02
do u use sudo apt-get install (***) to get them?

---

### Post by K2712 on 2008-08-02
You could do that, it would just tell you they were installed already.

You can also check to see if a package is installed with:

```
dpkg -s gstreamer0.10-plugins-base
```

---

### Post by jooking on 2008-08-02
how do u check if u have it?

---

### Post by K2712 on 2008-08-02
Check my last post---the dpkg -s command will tell you if a package is installed or not.  If it isn't installed the first line of output will tell you so.  If it is, then it will spit out all kinds of information about the package, like dependencies, developers, etc...

---

### Post by jooking on 2008-08-02
its installed,

---

### Post by pytheas22 on 2008-08-03
Dumb question, but just to check: did you restart your media player after installing the codecs via the apt-get command?  It probably won't work till you restart Totem or whatever you're using.  Restarting the computer might also help, although really it shouldn't be necessary (but I don't have any better ideas right now).

You could also try using mplayer, which you can install with:
```

sudo apt-get install gmplayer
```

Then to play a file, type:
```

gmplayer /path/to/file.mp3
```

mplayer can play a lot of stuff that other players can't...although Totem and everything else should be able to handle mp3's as long as the codecs are installed...but it can't hurt to try.

---

### Post by jooking on 2008-08-03
its fixed, i looked at another forum. thanks for the help

---

### Post by pytheas22 on 2008-08-03
I'm glad it's fixed.  Would you mind writing what exactly you did to solve the problem, please, in case anyone else with the same issue reads this thread?

---

### Post by K2712 on 2008-08-03
> **pytheas22 said:**
> i'm glad it's fixed.  Would you mind writing what exactly you did to solve the problem, please, in case anyone else with the same issue reads this thread?

+1

---

