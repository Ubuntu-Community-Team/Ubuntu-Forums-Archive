---
title: "Startup Apache2"
date: 2007-01-21
forum: Server Platforms
---

### Post by Martin_Blank on 2007-01-21
Somewhere between installing Apache, MySQL, and PHP, somehow both Apache 1.3 and Apache 2 were installed on my system. That's fine, but currently Apache 1.3 starts at boot, when instead, I need Apache 2 to start at boot. However, I can't figure out how to accomplish this. I've tried playing with update-rc.d but that hasn't helped. I was hoping someone might be able to shed some light on this issue. Thanks.

---

### Post by niekko on 2007-01-21
Would this be of help: [[COLOR="Blue"]https://help.ubuntu.com/community/UbuntuBootupHowto[/COLOR]]("https://help.ubuntu.com/community/UbuntuBootupHowto")

---

### Post by Martin_Blank on 2007-01-21
That did help quite a bit. I was able to remove 1.3 from startup. 

In order to get Apache 2 running, however, I had to modify /etc/default/apache2 and change the NO_START flag to 1. Now everything appears to be working correctly. :) 

Thanks for the tip!

---

### Post by joebobfrank on 2007-07-10
I misread this and got hung up for hours.  In case anyone else has the issue, the file in question is:

/etc/DEFAULTS/apache2 (defaults not all caps in the real world)

AND DEFINETLY NOT UNDER ANY CIRCUMSTANCES

/etc/apache2/apache2.conf

Don't know why I kept thinking that was where I needed to go, especially when the right file was referred to in the /etc/init.d/apache2 script, but whatever...

---

### Post by CyDharttha on 2007-07-27
Thanks, this did it for me. I made the mistake of installing apache, then realized my error, removed it and installed apache2. To note, the correct fiile is /etc/default/apache2 :)

---

### Post by felipeim on 2007-09-02
Hi,

I had the same problem.

I tried with sucess these steps below:

Create a "apache2" file on /etc/init.d/ with:

sudo gedit /etc/init.d/apache2

and put these two lines below:

[COLOR="DarkRed"]#!/bin/sh
/etc/apache2/bin/apachectl start[/COLOR]

Change the path to "apachectl" if necessary.

Then:

chmod +x /etc/init.d/apache2

And at last:

sudo update-rc.d apache2 defaults

---

