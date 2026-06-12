---
title: "Trying Unsuccessfully to load PHP Module smbclient"
date: 2016-09-25
forum: Server Platforms
---

### Post by Robert_Boutin on 2016-09-25
Hi everyone, hope this is the right place for this question.  I am installing Nextcloud 10 on a virtual server running a fresh install of 16.04 Server.  I am trying to make sure I've met all the LAMP requirements prior to installing Nextcloud and I'm stumbling on a needed PHP module, smbclient.  I ran  [FONT=Courier New]php -m | grep -I smbclient[/FONT] to check to see if that module was already installed, it wasn't.  I can't find a good instruction on how to install this module.  Any ideas?

As always, thanks, you guys (and gals) are the best.


SORRY, disregard, I got it:

sudo apt-get install php-opcache

I was trying php7.0-opcache which wasn't working.

---

