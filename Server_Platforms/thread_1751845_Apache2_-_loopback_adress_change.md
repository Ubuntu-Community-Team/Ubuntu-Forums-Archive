---
title: "Apache2 - loopback adress change ?"
date: 2011-05-07
forum: Server Platforms
---

### Post by syngress on 2011-05-07
Hi. I have a small problem.
Yesterday i try to make a fresh instalation of Ubuntu and LAMP.
After that - i try test my configuration type in browser 127.0.0.1

Streange thing is that once 127.0.0.1 was correct adress, few second later 127.0.0.1 not respond but 127.0.0.10 works, few second later 127.0.0.11 !! :o

I have configured new alias for my home catalog (public_html) in /etc/apache2/sites-available/default

so i put in one file to test my php configuration, and big suprise here !!

When i go to adres 127.0.0.1/mypage/:

127.0.0.1/mypage/ - serwer works but file don't show's up
127.0.0.10/mypage/ - serwer works and i see my test *.php file

What is this Trickery ?? :confused:
Please help

---

### Post by DAcre on 2011-05-07
Tried changing the Apache binding address?

---

### Post by syngress on 2011-05-07
> **DAcre said:**
> Tried changing the Apache binding address?

No, i don't touch Virtual Host.

---

