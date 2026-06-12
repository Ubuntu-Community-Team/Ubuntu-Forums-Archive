---
title: "Dynamic DNS Script"
date: 2009-06-06
forum: Server Platforms
---

### Post by trentscott4 on 2009-06-06
I'm using everyDNS.net for my domain and saw they have a Perl script that will update their records with your current IP.  Does anyone know how I would set this up using Webmin on Ubuntu Server 9.04?

I've read I need to install the 'libmime-perl' package -- what should I do from there?  Can I schedule a cronjob to run the script or is there a better way?

Thanks!

---

### Post by puppywhacker on 2009-06-07
I don't think you can do that from webmin, or I missed a whole evolution...

To install the libmime-perl packet you can run this from a terminal
```
sudo apt-get install libmime-perl
```

I uesd the ddclient program to update the dns records as soon as my ip-address changes, you can run it as a daemon so that it monitors the interface periodically and doesn't need cron to do so
```
sudo apt-get install ddclient
```

---

### Post by trentscott4 on 2009-06-07
Thanks!  Do you know if ddclient is compatible with everyDNS?

---

### Post by puppywhacker on 2009-06-07
yes it is compatible with at least

[www.dyndns.com](www.dyndns.com)
[www.easydns.com](www.easydns.com)
[www.dslreports.com](www.dslreports.com)
[www.zoneedit.com](www.zoneedit.com)

---

