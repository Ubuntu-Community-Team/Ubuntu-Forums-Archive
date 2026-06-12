---
title: "Apache Forbiiden after update"
date: 2008-07-30
forum: Server Platforms
---

### Post by jdbg on 2008-07-30
Hi,

I'm using the 8.04 distro.
Yesterday I did the regular apt-get update & upgrade and after that my webserver is down. All pages come with the Error: 403 Forbidden. I haven't changed anything in the configs or anywhere else, only did the apt-get upgrade.

Any ideas how to fix this?

Thanks in advance!

---

### Post by ChumleyEX on 2008-07-30
check your rights in your /var/log/www folder. Maybe something was rewritten and now has just root right or something.

---

### Post by jdbg on 2008-07-30
I haven't used any rewrites.
Other speaking of permissions - the www root folder is chmod 777

---

### Post by ChumleyEX on 2008-07-30
what if you do ls -l are the webpages like that as well? 


Don't you want 755?

---

### Post by jdbg on 2008-08-11
I do, but with neither 777 or 755 it works :(
Very very strange problem.

---

