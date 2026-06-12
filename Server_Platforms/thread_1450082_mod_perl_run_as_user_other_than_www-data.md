---
title: "mod_perl run as user other than www-data"
date: 2010-04-08
forum: Server Platforms
---

### Post by fang0654 on 2010-04-08
I am currently installing a billing system to play with called [FreeSide]("http://www.freeside.biz").  While going through their install instructions, they have one little small line that reads as the following:

> Ensure Apache has mod_perl enabled and is set to run as User freeside. If you have other things being served by Apache on this machine (hopefully internal things), it is recommended to run a separate iteration of Apache as the freeside user.

I'm building it in a VM all by its lonesome, so no worries about anything else using mod_perl.  From what I understood, mod_perl runs as the user that apache2 does, i.e. www-data.  Is this incorrect?  Is there a way of setting the user that mod_perl runs as?  Or do I need to change the user apache uses?

---

