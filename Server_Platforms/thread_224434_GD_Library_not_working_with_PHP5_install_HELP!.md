---
title: "GD Library not working with PHP5 install HELP!"
date: 2006-07-28
forum: Server Platforms
---

### Post by jscrilla on 2006-07-28
Hi everyone,

I need the GD library working right on my system, been working on getting it going all night, but am at a loss as to what is wrong. 

My server says everything is installed but it still won't work. 

Here's the the GD test to tell what the version supports:

[GD Output Page]("http://www.jasonfrye.com")

and a test image create code at [URL="http://www.jasonfrye.com/test.php"]Test Page
[/URL]

I've linked to the extension directory, and uncommented the gd.so in the php.ini file, but still cannot get the GD functions to create images. Please, can someone point me in the right direction? 

thanks!

---

### Post by dtfinch on 2006-07-28
Oddly there are 4 spaces at the beginning of the png. If I delete them, I get an image with "My first Program with GD". GD itself it working fine as far as I can tell. Gotta watch out for that extra whitespace.

---

### Post by jscrilla on 2006-07-28
OK...hmmm. i'm still not seeing it. what why space did you remove?

---

### Post by jscrilla on 2006-07-28
Ok i figured it out. Thanks for telling me about that. geez, what a minor error. lol.

---

