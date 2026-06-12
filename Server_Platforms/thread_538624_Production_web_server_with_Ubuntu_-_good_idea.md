---
title: "Production web server with Ubuntu - good idea?"
date: 2007-08-30
forum: Server Platforms
---

### Post by helzer on 2007-08-30
Hi,

Do you think it's a good idea to have a production web server running Ubuntu? I would like to use 7.04, as it includes packages that are required for my application.

I'm using Ubuntu on the development machines and am very happy and comfortable with the setup.

My concerns are mostly with administration. Where can I find a technically competent administrator to correctly configure and secure the services?

Any hosting company you would recommend to properly handle a Ubuntu based server?

Thanks,
Helzer

---

### Post by HermanAB on 2007-08-30
Yes it will work.  You can configure Apache with Webmin and Virtualmin.  For ultra cheap hosting, try CiHost - look for the 'crazy deals' on their web site.

For security, turn off everything you don't need and enable rate limiting with iptables to prevent Slashdottings and exceeding your bandwidth limits.  Configure SSH to run on a non-standard port, don't use FTP and do use very long pseudo-random passwords (I use 16 character passwords). That is pretty much all you need to do.

Cheers,

Herman

PS.  Don't bother with running services 'chroot'.  It doesn't really help anymore and it makes the machine much more difficult to administer.

---

### Post by helzer on 2007-09-03
Hi Herman,

Thanks for the great advice!

Amir

---

