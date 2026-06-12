---
title: "share htdocs between lampp and xampp on usb"
date: 2010-02-17
forum: Server Platforms
---

### Post by crebilis on 2010-02-17
Hi all,

I recently switched from windows to ubuntu (9.10). I have an usb stick with on that a windows xampp installation. Now I want to install lampp on it, so that both installations share the same htdocs and database.

So what I want is:
- I have on an usb stick a xampp installation
- I also have lampp installed in /opt/lampp
- Now I want the lampp installation to use the htdocs and database that are located on the usb stick.

I tried:
- Changing httpd.conf so that DocumentRoot pointed at /media/JACKO/xampp/htdocs (JACKO being the name of the usb stick) -> did not work
- mounting the the usb stick to a folder in my home folder and changing DocumentRoot to that folder -> no permissions when going to localhost.

I searched google for answers and the things I tried are basically what I found there. Nothing worked. Anyone got an idea what I could do to make this work?

---

### Post by crebilis on 2010-02-24
anyone?

---

