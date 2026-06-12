---
title: "Ubuntu + Apache + PHP output buffering"
date: 2014-01-01
forum: Server Platforms
---

### Post by jackiellowery on 2014-01-01
I'm about to pull my hair out i can't get a simple script to echo the numbers 1 to 10 with a short delay between counts.  My server always runs the entire script and outputs all the numbers at once.

What I've tried:

php setting:  output_buffering = Off

apache setting:  disabled mod_deflate and gzip

I have no clue what is still buffering the output at this point.

Please help!

---

### Post by jackiellowery on 2014-01-01
Finally! For anyone else, here is the fix:

Edit php.ini and add:

default_charset = "utf-8";


No idea why this causes the buffering, but that's it!  Man!

---

