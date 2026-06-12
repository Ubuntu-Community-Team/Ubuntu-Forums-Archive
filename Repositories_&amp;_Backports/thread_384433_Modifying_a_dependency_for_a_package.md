---
title: "Modifying a dependency for a package"
date: 2007-03-14
forum: Repositories &amp; Backports
---

### Post by andrewski on 2007-03-14
I'm trying to update a dependency for the dragon-watch package: [http://ccdw.org/~cjj/prog/dragon-watch]("http://ccdw.org/%7Ecjj/prog/dragon-watch"). There are debs available []("http://ccdw.org/%7Ecjj/files/debs%29")([http://ccdw.org/~cjj/files/debs]("http://ccdw.org/%7Ecjj/files/debs")), but they don't seem to list the dependencies I'm expecting.

Specifically, I'm looking to update libgnomemm-2.6-1c2 to the libgnomemm-2.6-1c2_**a**_ listed in Ubuntu. 

I know I need to update the debian/control file in the .tar.gz, but it only seems to list build-deps, which makes me think it's working for a source deb.

Can anyone help me?

---

