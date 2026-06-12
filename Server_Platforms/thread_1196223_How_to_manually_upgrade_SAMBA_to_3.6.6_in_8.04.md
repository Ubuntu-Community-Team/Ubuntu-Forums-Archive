---
title: "How to manually upgrade SAMBA to 3.6.6 in 8.04"
date: 2009-06-24
forum: Server Platforms
---

### Post by HereSomeHow on 2009-06-24
I started to setup an old Compaq Proliant 3000 server to serve files in our lan with SAMBA (all XP clients), and find that just the 7.1 gutsy could install.

After several days of trying, I finally upgraded it to 8.04, but can't move it to 8.10, so decided to stay there. But, I need the latest SAMBA put there and can't find how to.

I tried by downloading the .tar.gz and converting it to deb with alien, but didn't work. All it does is uninstall the older samba but won't setup the newer.

Any help? thx

---

### Post by antikristian on 2009-06-26
you could try the packages from enterprisesamba

[ftp://ftp.sernet.de/pub/samba/recent/debian/dists/lenny/](ftp://ftp.sernet.de/pub/samba/recent/debian/dists/lenny/)

Although these are for debian, it _might_ work.

Why do you need the new samba version though? new features? Security updates are covered for the version form ubuntu until 2013, so the 8.04 release of ubuntu wasn't a bad choice.

---

