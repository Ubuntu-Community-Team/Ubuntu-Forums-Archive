---
title: "apt caching and ubuntuzilla repo"
date: 2010-02-27
forum: Ubuntuzilla
---

### Post by cong06 on 2010-02-27
I wanted to make a chage to the wikipedia: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) but it seems to be protected.

The repository:```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```is the default```
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```being the alternate for 8.10 or earlier.

If you're using a cacher like "apt-cacher" as a proxy, you need to us the alternate repository also, however.
At least until apt-cacher gets updated.

This explains the error:
```

Err http://downloads.sourceforge.net all/main Packages
  302  Moved Temporarily

```
or if wget'd (where wget gets directed to the apt-cacher proxy
```

root@phaff:~# wget http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz
--2010-02-27 15:52:16--  http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: unspecified
ERROR: Redirection (302) without location.

```

---

### Post by nanotube on 2010-02-28
hi
thanks for the heads-up. i'll make a note on the website about any apt tools not supporting 302 redirects.

---

