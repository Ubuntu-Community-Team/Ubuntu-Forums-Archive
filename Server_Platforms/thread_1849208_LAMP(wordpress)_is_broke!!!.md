---
title: "LAMP(wordpress) is broke!!!"
date: 2011-09-24
forum: Server Platforms
---

### Post by Murphy-10332 on 2011-09-24
I have been up for two days and have fought for almost three weeks to do anything with Ubuntu LAMP. 
Start by checking out my site, click on the broken links [www.ripples-book.tk](www.ripples-book.tk) . Also I can not access Wordpress dashboard from localhost/wordpress.   
  ubuntu 10.?? wordpress 3.2.1    Apache 2.2 
   Forgive the lack of data I will post what every you need. I am strung out over this!!!!!!!!!!! I have been through close to a thousand post and a small college campus worth of IT professions to try and get this project of the ground. 
   Will some one please walk me through this?
Thank You
Joshua

---

### Post by Ryan Dwyer on 2011-09-24
It looks like you have some Wordpress config that sets the hostname to 127.0.0.1. Find it and change it to [www.ripples-book.tk](www.ripples-book.tk).

Note that you probably won't be able to access it internally unless you set up a local DNS server or make modifications to your hosts file.

---

### Post by Murphy-10332 on 2011-09-24
Thank you for your fast reply I will get to changing that.

---

