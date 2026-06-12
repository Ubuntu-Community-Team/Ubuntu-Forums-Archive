---
title: "How to compile PHP5 under Ubuntu with MySQLi and GD support?"
date: 2006-03-14
forum: Server Platforms
---

### Post by i-x on 2006-03-14
Hello,

I've been stuck for days with this problem. I've tried to apt-get install Apache2 and PHP5, but it won't give me MySQLi and GD support.

So I've been told to compile PHP myself. 

But I keep having problems, the compiling halt each time on different problems. I've spent hours on google but can't find any useful websites about this problem. 

Could anybode give me a hint?

Please, please, please

---

### Post by gmclachl on 2006-03-14
GD is supported you need to apt-get php5-gd 

 As for MySQLi support I am afraid it's not there. I have put in a feature request for it to be added, but as there is a freeze just now, it probbaly won't happen. 

[https://launchpad.net/malone/bugs/34734](https://launchpad.net/malone/bugs/34734)

I have a link at home which i can give you for an unofficial repos with it. Won't be able to do that until 5pm (GMT) 

I am sure someone will point it out before then. 

George

---

### Post by dudus on 2006-03-22
there is this topic that helps on compiling php5 with mysqli in the wiki.

[https://wiki.ubuntu.com/PHP5FromSource]("https://wiki.ubuntu.com/PHP5FromSource")

---

