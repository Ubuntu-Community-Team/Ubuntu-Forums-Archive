---
title: "php5-imap installed with apt-get but does not show"
date: 2009-02-28
forum: Server Platforms
---

### Post by PlaHPoy on 2009-02-28
I installed php5-imap extension (apt-get install php5-imap) which says it installed fine.  

I have restarted apache2 many times, and the imap extension is not found.

I have looked at the apache2 error logs and see nothing regarding imap.  the imap extension is not being shown as loaded either in my phpinfo();

info is located at [www.brightononline.com](www.brightononline.com)

Thanks in advance to whomever helps out! :)

Best,

-Z-

---

### Post by maniaq on 2009-04-01
I've had some trouble with apache no being able to find php modules (in my case the mysql extension) - I had to change the default extensions directory from "./" to (in my case) "/usr/lib/php5/20060613+lfs/"

you might try checking that setting in your /etc/php5/apache2/php.ini file - although check your directories under /usr/lib/php5 - yours might have a different date...


good luck!

---

### Post by hyper_ch on 2009-04-02
is php5 enabled?

---

