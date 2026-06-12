---
title: "What I Learned In School Today About Aisleriot"
date: 2022-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by iamjiwjr on 2022-04-22
For all you Aisleriot junkies out there, I accidentally found (the best way to find things) the following file to add during/after installing aisleriot: gnome-cards-data. With this file the graphics of my favorite mindless solitaire game appear noticeably more polished and clear.

For me, 22.04 is a real pearl! I'm loving it.

---

### Post by QIII on 2022-04-22
Neither a support request nor a response to one.  Moved to ULOSC

---

### Post by robdavidson2 on 2022-05-01
> **iamjiwjr said:**
> For all you Aisleriot junkies out there, I accidentally found (the best way to find things) the following file to add during/after installing aisleriot: gnome-cards-data. With this file the graphics of my favorite mindless solitaire game appear noticeably more polished and clear.

For me, 22.04 is a real pearl! I'm loving it.

Thanks for the tip!  :)

---

### Post by VMC on 2022-05-01
> **iamjiwjr said:**
> For all you Aisleriot junkies out there, I accidentally found (the best way to find things) the following file to add during/after installing aisleriot: gnome-cards-data. With this file the graphics of my favorite mindless solitaire game appear noticeably more polished and clear.

For me, 22.04 is a real pearl! I'm loving it.Not sure what you trying to say. Using both file and/or directory. Found nothing.
```
$ sudo find / -name gnome-cards-data 2>/dev/null
$ sudo find / -type d -name gnome-cards-data 2>/dev/null
```

---

### Post by yetimon_64 on 2022-05-01
> **VMC said:**
> Not sure what you trying to say. Using both file and/or directory. Found nothing...
It is a package in the repositories...```
yetiman :~   $   apt-cache policy gnome-cards-data
gnome-cards-data:
  Installed: 1:3.22.22-1
  Candidate: 1:3.22.22-1
  Version table:
 *** 1:3.22.22-1 500
        500 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status
```
It is not a dependency of aisleriot but it is a suggested package...```
yetiman :~   $   apt depends aisleriot
aisleriot
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
<snipped list of "Depends" for brevity>
  Recommends: yelp
  Suggests: gnome-cards-data
```

The OP's meaning may have been a bit clearer by using the word "package" instead of "file".

> For me, 22.04 is a real pearl! I'm loving it.
@OP, I agree. It's doing well here (on Xubuntu 22.04); including all the time spent playing solitaire :). Aisleriot is my favourite of the gnome games collection.

---

### Post by VMC on 2022-05-02
> Aisleriot is my favourite of the gnome games collection.It's the only games I play on Linux.

---

