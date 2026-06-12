---
title: "Webmin, Cpanel, SSL"
date: 2011-07-10
forum: The Cafe
---

### Post by lovinglinux on 2011-07-10
I didn't know where to post this thread, so I guess the Cafe will be fine.

I am considering migrating my web sites to a VPS server, so I can offer SSL and better performance. 

Currently I am using CPanel and I am very comfortable with it. The VPS on the other hand, offers Webmin, which I never used. How hard would be to manage the web sites and databases with it?

---

### Post by steinerd on 2011-07-10
Hi, my websites are running on my in-home webserver.  I use webmin for most server administration tasks and it is pretty straight forward.  I had some trouble with multiple vhosts, it is definately capable of the task but is not as easy or intuitive as cpanel.  I opted to additionally install EHCP on my server to manage my vhosts.  It is a cpanel like hosting solution that has made things easier for me.  The module that webmin uses for vhosting multiple sites is virtualmin.  The GPL version of this is a bit stripped down and does not include resellers or install script support.  Another reason a gravitated towards EHCP.

Some links... [EHCP info and install]("http://shallows.bounceme.net/tiki-index.php?page=EHCP&structure=Ubuntu+Help&page_ref_id=7") and [Webmin 1.550]("http://shallows.bounceme.net/tiki-index.php?page=Webmin&structure=Ubuntu+Help&page_ref_id=8")

Hope this helps out a bit.  the long and short of it is that webmin IS capable of managing your sites but it will not be as simple in my opinion as CPANEL.  EHCP in addition gets it there.

---

### Post by lovinglinux on 2011-07-10
> **steinerd said:**
> Hi, my websites are running on my in-home webserver.  I use webmin for most server administration tasks and it is pretty straight forward.  I had some trouble with multiple vhosts, it is definately capable of the task but is not as easy or intuitive as cpanel.  I opted to additionally install EHCP on my server to manage my vhosts.  It is a cpanel like hosting solution that has made things easier for me.

Some links... [EHCP info and install]("http://shallows.bounceme.net/tiki-index.php?page=EHCP&structure=Ubuntu+Help&page_ref_id=7") and [Webmin 1.550]("http://shallows.bounceme.net/tiki-index.php?page=Webmin&structure=Ubuntu+Help&page_ref_id=8")

Hope this helps out a bit.  the long and short of it is that webmin IS capable of managing your sites but it will not be as simple in my opinion as CPANEL.  EHCP in addition gets it there.

Thanks. I am thinking a VPS maybe too much for my needs. I am also considering a Business plan with SSL support, since it has Cpanel.

---

