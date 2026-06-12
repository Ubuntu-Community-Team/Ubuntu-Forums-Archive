---
title: "The latest version of Ktorrent"
date: 2007-11-17
forum: Repositories &amp; Backports
---

### Post by davidc502 on 2007-11-17
I'm new to Ubuntu, and I don't know if I'm in the right forum, but here's the question.

FYI- I'm new to Ubuntu, but not to Linux.

I went to Add/Remove and selected Ktorrent2.2.1. It installed, but there is a bug with this version. It eats CPU for lunch and tops out my processor at maintains it at 90%(This is a known bug). Anyway, I went ahead and uninstalled Ktorrent2.2.1, and downloaded Ktorrent2.2.3. I compiled it and installed successfully. This version _does not_ have the cpu bug that 2.2.1 has which is good news.

1. Now to the major question: How do I contribute the latest version of Ktorrent compiled on Ubuntu7.10? 

2. What forum could I go to, to ask how to create debian packages? I'm assuming this is the default packaging system Ubuntu uses.

Thanks,

David

---

### Post by stoeptegel on 2007-11-17
I do not understand question one, what do you mean by contributing? Might be me though, my english is not that good....

For what's question two concerned, Jdong makes debian packages for ubuntu which will be put on the ktorrent website. As for Version 2.2.3, it was already uploaded to hardy and will soon also be backported to gibbon, feist and edgy.

---

### Post by shad0w_walker on 2007-11-17
I believe there is a very small list of developers that are allowed to add to the official repos so odds are they won't accept the packages. However you can make debian packages using check install. 

[http://www.debian-administration.org/articles/147](http://www.debian-administration.org/articles/147) 

It's a pretty simple process and will give you the packages so you can put them in a public repo or just uplaod them to the forum if you want.

---

### Post by davidc502 on 2007-11-17
This information is exactly what I was searching for!

Thank you shad0w_walker and stoeptegel

Both questions have been answered.

---

### Post by zero-9376 on 2007-11-17
I don't think checkinstall is the proper method to make packages, its good for when you are installing from source but I don't think its as re-distributable. Check out this guide for proper methods:
[http://doc.ubuntu.com/ubuntu/packagingguide/C/](http://doc.ubuntu.com/ubuntu/packagingguide/C/)

Also if you want to add something to the ubuntu repos I think you need to be a MOTU: master of the universe (universe repo) or be sponsored maybe? The other thing you could do is to use the personal package archives which IIRC are small repos maintained by you for your own packages and you can simply tell people to add your repo.

---

### Post by pickarooney on 2007-11-25
So, does anyone know someone who has made working .deb files for Feisty for 2.2.3 (or even 2.2.4)? I can't get the source to compile.

---

### Post by FLCLFan on 2007-11-27
ktorrent 2.2.4 is in the gutsy backports. Im using it.

---

