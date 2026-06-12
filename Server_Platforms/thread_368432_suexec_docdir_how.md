---
title: "suexec docdir how?"
date: 2007-02-23
forum: Server Platforms
---

### Post by Claudiof on 2007-02-23
Hi,

I pretend to change the suexec docdir to /home/ because i don't have any sites in the /var/www

I've read that i need do rebuild the apache package from source but... how? and how can i change this value?

---

### Post by Strider on 2007-02-23
This should point you in the right direction:

[http://httpd.apache.org/docs/2.0/suexec.html](http://httpd.apache.org/docs/2.0/suexec.html)

-Mike

---

### Post by marmi on 2007-02-26
Is there anything other method to change the AP_DOC_ROOT in suexec than get deb-source package, change source's docroot to in example /home, build package and install it with dpkg ([like here]("http://ubuntuforums.org/showthread.php?t=227551&highlight=suexec+docroot"))?
And after that apt-get update & apt-get upgrade will update your own created package and the docroot is again /var/www..Bad.

Building and compiling from sources isn't the alternative (imo). apt-get is just too great for maintain..

[This]("http://www.howtoforge.com/forums/showthread.php?t=4606") method doesn't worked for me (in feisty, a lot of errors..).

Any comments or solutions?

---

