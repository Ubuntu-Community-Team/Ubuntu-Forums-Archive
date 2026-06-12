---
title: "php-apc issues"
date: 2010-03-26
forum: Server Platforms
---

### Post by mattyh on 2010-03-26
I'll likely cross post this on an apc / php forum, but I thought I would start here in case the issue is known to be ubuntu specific.

I'm running an ubuntu 8.04 server that employs apc.  I noticed that when I install apc via pecl (i.e. pecl install apc) I am not able to get apc_store to work.  I was then made aware of the fact there is an actual php-apc package in the apt-get repositories, so I installed that and apc_store began to work.  I noted that the pecl install uses the last stable version, whereas the apt-get package installs the most updated). 

Upon install php-apc apc_store functionality began to work in my environment.  HOWEVER, while troubleshooting another issue related to php code and potentially apc, i unstinalled both versions completely (ran apt-get remove --purge php-apc) and then proceeded to only install the php-apc package.  To my dismay, my apc_store functionality no longer worked.  Sure enough, doing pecl install apc fixed my issue.

Anyone else dealt with issues related to this package?  I'm trying to figure out if perhaps the pecl install only install the compiled module, whlie the php-apc pckage installs the libraries for php to use.  But, if that's the case, why does the php-apc package not work on its own.

I'm going to keep digging, but I thought I'd see if anyone else had ideas.

---

