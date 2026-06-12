---
title: "AWStats and GeoIP"
date: 2010-04-04
forum: Server Platforms
---

### Post by jordon on 2010-04-04
I'm trying to install the GeoIP plugin for AWStats. I've installed the packages geoip-database, libgeoip1, and libgeo-ip-perl. geoip-database installs the database file at /usr/share/GeoIP/GeoIP.dat, so that's the path I'm using in my AWStats config file. When I try to run AWStats on my logs, it hangs without generating any files. No debug messages about this are printed when I enable them. I've also tried installing libgeo-ipfree-perl and uncommenting the geoipfree line in my conf file, but that didn't work either.

Possibly useful detail: I previously tried installing the GeoIP C library and Perl module manually, which didn't work, and then I tried installing the Pure Perl module manually, which also didn't work. I simply deleted them all, which I'm not sure was a good idea. I don't know anything about this stuff.

---

### Post by Wingthor on 2010-04-09
Try this tutorial [http://www.antezeta.com/awstats/geoip.html#geolin](http://www.antezeta.com/awstats/geoip.html#geolin). I am not sure what kind of system you have got, but this is for both windows and linux. You also need to install PERL.

Regards

---

### Post by jordon on 2010-04-09
Those were the directions I used for the manual installations that didn't work.

---

