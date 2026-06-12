---
title: "[SOLVED] Firefox attempts to download php files after LAMP install"
date: 2008-11-12
forum: Server Platforms
---

### Post by glacialfury on 2008-11-12
Running Ubuntu 8.10 64bit.

1) I installed the LAMP package/task, Webmin, and phpMyAdmin.
Webmin shows apache etc running appropriately.
2) I tested the apache install by going to localhost in my browser (Firefox); it confirms apache is working ("Yep! It Works! page loaded)
3) I downloaded e107 (a php-based CMS) and deposited it, per the instructions, in the appropriate folder (/var/www/).
4) I navigate to localhost/install.php in Firefox to initiate the e107 installation script.
5) Firefox pops up a dialog saying basically, "This is a php file, what should I do with it?"

From searches on the forums, the proposed solutions were:
 - restart apache (yes, that's all I could find)

I restarted apache without issues but it didn't change the problem; when I try to access a php file locally through the browser, it doesn't get parsed.

Any help?

---

### Post by rustutzman on 2008-11-12
Sounds like php isn't running. Can you look at the php logs?

Russ

---

### Post by mbeach on 2008-11-12
it sounds as if php may not be installed correctly.

a similar problem described at:
[http://ubuntuforums.org/showthread.php?t=926692](http://ubuntuforums.org/showthread.php?t=926692)

Does that assist at all?

also see:
[http://ubuntuforums.org/showthread.php?t=954075](http://ubuntuforums.org/showthread.php?t=954075)

as a side note, if you are evaluating php based cms's you might want to give concrete5 a look:
[http://www.concrete5.org/](http://www.concrete5.org/)

---

### Post by glacialfury on 2008-11-12
The post that advocated running ```
sudo aptitude install php5 libapache2-mod-php5
``` fixed it - thanks!

It ought to have worked without that, given it was a bundled task, but whatever works, works for me.

---

