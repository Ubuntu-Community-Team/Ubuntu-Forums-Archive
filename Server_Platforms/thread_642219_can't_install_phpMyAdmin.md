---
title: "can't install phpMyAdmin"
date: 2007-12-16
forum: Server Platforms
---

### Post by MalphasWats on 2007-12-16
Hi,

  I'm trying to set up a webserver to act as a backup and development server.

I've installed 7.10 and php and mysql and everything seems to be working fine.

when I try to install phpmyadmin, it asks me to put the installation CD in, if I put the CD in, I just get "99% [Working]" and that's where it stays.

My intention is to set all this stuff up on a machine I won't have physical access to, which obviously I can't put a CD in.

What other options do I have for installing this? Why is it not working in the first place?

EDIT: I've also just tried to install the php4-gd library, and it does the same thing. What can I do?

EDIT 2: I've solved it, after spending all day trying to find a solution, checking my repositories settings over and over, I finally found an entry at the top that I hadn't even noticed that was pointing it at the CD, I killed that line and it all worked fine. Hope this helps someone else!

Thanks
-Mal

---

### Post by sweetmax on 2007-12-24
Well, why you just dont install Lampp (Xampp), it has all installed for you, easy to use and enough powerful.

---

