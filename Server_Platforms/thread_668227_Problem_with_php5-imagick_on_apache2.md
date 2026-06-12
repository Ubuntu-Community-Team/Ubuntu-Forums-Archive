---
title: "Problem with php5-imagick on apache2"
date: 2008-01-15
forum: Server Platforms
---

### Post by userfriendly on 2008-01-15
i know this probably isn't the right forum to be asking this, and usually i tend to quickly find what i need with google... but... not this time. right now i'm rather desperate and i don't find anything about it on the web.

i've installed ImageMagick & php5-imagick. seems to work okay so far, i've made a small test script that uses an Imagick object to simply resize an image and store it again.

however, lots of other functions (important ones, for that matter) kill the apache child process. this is from the apache2 error log:

> apache2: wand/pixel-wand.c:971: PixelGetMagickColor: Assertion `wand != (const PixelWand *) ((void *)0)' failed.
[Tue Jan 15 14:13:34 2008] [notice] child pid 8638 exit signal Aborted (6)

where "PixelGetMagickColor" of course changes depending on which method i'm calling. the result is that i get a "save as" dialog offering me the php script.

any help would be _*hugely*_ appreciated!

---

### Post by userfriendly on 2008-01-15
never mind, this post provided a solution: [http://ubuntuforums.org/showpost.php?p=3647123&postcount=13](http://ubuntuforums.org/showpost.php?p=3647123&postcount=13)

i love this forum :)

---

