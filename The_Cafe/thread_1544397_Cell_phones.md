---
title: "Cell phones"
date: 2010-08-02
forum: The Cafe
---

### Post by JrHoratio on 2010-08-02
I work in telecommunications, i have heard that some of the newer smart phones run a version of Linux and or Unix, how true is this?
 
                                                      Thanks,
                                                               L.Rosser

---

### Post by Jazzy_Jeff on 2010-08-02
The Android platform is based on Linux as well as Palm. There may be others.

---

### Post by mcduck on 2010-08-02
Android, Bada (Samsung), WebOS (Palm), Maemo (Nokia) and MeeGo (Nokia, Intel & others) all run on top of the Linux kernel.

iOS (Apple) is also based on the same Darwin kernel that is used in OSX, and that's Unix-certified which makes iPhone an Unix system as well.

So you could really say that *most* of the smartphone operating systems are Linux- or Unix-based... :D

---

### Post by TheNerdAL on 2010-08-02
> **mcduck said:**
> Android, Bada (Samsung), WebOS (Palm), Maemo (Nokia) and MeeGo (Nokia, Intel & others) all run on top of the Linux kernel.

IOS (Apple) is also based on the same Darwin kernel that is used in OSX, and that's Unix-certified which makes iPhone an Unix system as well.

So you could really say that *most* of the smartphone operating systems are Linux- or Unix-based... :D

I think you mean all Except Windows phones? Lol. :p

---

### Post by mcduck on 2010-08-02
> **TheNerdAL said:**
> I think you mean all Except Windows phones? Lol. :p

well, Windows Mobile, Symbian and BlackBerry OS. :D

---

### Post by gamblor01 on 2010-08-02
> **JrHoratio said:**
> I work in telecommunications, i have heard that some of the newer smart phones run a version of Linux and or Unix, how true is this?
 
                                                      Thanks,
                                                               L.Rosser
Indeed, as others have mentioned there are many smart phones out there running some Linux/Unix kernel.  Note the keyword however: kernel.

When people think about Linux, they commonly think of a particular Linux distribution such as Ubuntu, SuSE, Redhat, etc.  These distributions however are "bloated" with packages that can require gigabytes of space to install.  The actual kernel itself however is at the heart of each of these distributions and defines the core functions necessary to run.  The kernel alone is quite small -- for example my kernel image (well, compressed anyway) is a little over 4 megabytes:

```

-rw-r--r-- 1 root root 4167616 2010-07-05 09:39 vmlinuz-2.6.32-24-generic-pae

```
Once you have the kernel though, you can start adding the packages on top of it that you wish to supply to your user.  So the Android OS for example probably isn't going to include gnome and KDE by default, it's not going to include development tools, or the tex-live package, and so on.  It does contain a Linux kernel however, and then all of the tools that the Android team finds necessary to power a smart phone though (GPS drivers, bluetooth drivers, touch screen drivers, etc.).  All of this is considerably smaller than a desktop version of Linux (such as Ubuntu) which will require several gigabytes of space.

For more info on Android check out [http://www.android.com](http://www.android.com) or [http://source.android.com](http://source.android.com)

---

### Post by Elfy on 2010-08-02
moved

---

### Post by JrHoratio on 2010-08-18
Thanks for all your replies, they were very informative and a great help...
 
                                  L.Rosser

---

