---
title: "Can I still use Ubuntu 6 lts??"
date: 2010-05-11
forum: The Cafe
---

### Post by clgy15 on 2010-05-11
Hey everybody,
I installed ubuntu 6 on my Sparc Sublade 1000 because it was the only one that would install. I was just wondering if ubuntu still has its repositeries that will work with 6.

Its a sweet classic by the way. =)

---

### Post by WinterRain on 2010-05-11
Yes, I believe you can, but you will have to manually change your sources.list 

Perhaps someone else can give you the details.

---

### Post by clgy15 on 2010-05-11
Oh that would be great because im turning into a server and Ubuntu 6 still runs extremly smooth and I want to you know install server apps

---

### Post by WinterRain on 2010-05-11
Found it from here: [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

1. Edit /etc/apt/sources.list
2. Replace all occurrences of archive.ubuntu.com with old-releases.ubuntu.com
3. sudo apt-get update
4. sudo apt-get install <package name>

---

### Post by clgy15 on 2010-05-11
Sweet you just made my day! Thanks so much

---

