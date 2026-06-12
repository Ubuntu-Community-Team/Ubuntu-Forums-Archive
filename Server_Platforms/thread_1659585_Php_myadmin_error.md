---
title: "Php myadmin error"
date: 2011-01-04
forum: Server Platforms
---

### Post by abhisheksag7 on 2011-01-04
I am a newbie to linux, i installed XAMPP for linux on my machine.
Whenever i want to enter in to >> tools>> phpmyadmin i get this error 
Wrong permissions on configuration file, should not be world writable!

can any 1 faced the same problem before.
thanks in advance!!

---

### Post by NIN101 on 2011-01-04
Hi,

> Wrong permissions on configuration file, should not be world writable!

This says everything. The configuration file shouldn't be world writeable.

I don't know which file is the configuration file in phpmyadmin. I assume it is config.inc.php. But anyway, probably this could solve it:

**chmod o-w config.inc.php** 

This takes away the write permissions from "others". You maybe want to learn the unix permission concept.

---

