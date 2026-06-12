---
title: "Virtual hosting - how to name the index.htlm file of 2nd domain"
date: 2011-04-13
forum: Server Platforms
---

### Post by satimis on 2011-04-13
Hi folks,

Ubuntu 1010 server 64bit
lighttpd

For the 1st domain,say domain1

I name the index file as:
/var/www/index.html
/home/lighttpd/default/http/index.html
/home/lighttpd/domain1/http/index.html

3 identical files. It works seamlessly. On browser its webpage can be evoked.

Now I add another domain, say domain2. How shall I name its index files?

/var/www/index.domain2.html ?
/home/lighttpd/default/http/index.domain2.html ?
/home/lighttpd/domain2/http/index.domain2.html ?

TIA

B.R.
satimis

---

### Post by falko on 2011-04-14
The file name is the same (index.html), but you must use a different document root for the second virtual host.

---

### Post by satimis on 2011-04-14
> **falko said:**
> The file name is the same (index.html), but you must use a different document root for the second virtual host.

Hi falko,

Thanks for your advice.

I followed following how-to to install lighttpd and setup name-based virtual hosting;

[http://www.cyberciti.biz/faq/howto-lighttpd-virtualhost-configuration/](http://www.cyberciti.biz/faq/howto-lighttpd-virtualhost-configuration/)

I have no problem on setting up domain1.  Now coming to domain2 I'm in complete lost.

I already setup document-root for domain1.  Please advise how to setup document-root for domain2.  Then there are 2 document-roots?  How to separate them?  Is the link followed by me being correct?

TIA

B.R.
satimis

---

### Post by Iker Etxebarria on 2011-04-14
Document root means a new folder to store all the domain2.

---

### Post by satimis on 2011-04-14
> **Iker Etxebarria said:**
> Document root means a new folder to store all the domain2.

Hi,

Could you please explain in more detail.

For domain1 there are 3 folders;
/var/www/index.html
/home/lighttpd/default/http/index.html
/home/lighttpd/domain1/http/index.html

to store its webpage "index.html".  Which folder I have to create for domain2?  How to identify domain2's folder from domain1's?

I just found following links;
multiple vhosts
[http://forum.lighttpd.net/topic/296](http://forum.lighttpd.net/topic/296)

It seems the steps are different.

B.R.
satimis

---

