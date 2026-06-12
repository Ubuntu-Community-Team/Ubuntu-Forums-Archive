---
title: "How to install FireBird on Ubuntu 12.04"
date: 2013-05-29
forum: Server Platforms
---

### Post by kamrava on 2013-05-29
I would like intall FireBird on ubuntu 12.04 32bit.  I've downloaded it from [here]("http://www.firebirdsql.org/en/firebird-2-5-2-upd1/#Linux_x86").
  There is a `.rpm` file in `~/Downloads/FirebirdSS-2.5.2.26540-0.i686.rpm`.

  I've seen [this link]("http://www.firebirdsql.org/manual/qsg2-installing.html") for how to install it, But i don't understand !
  What i must to do with that `.rpm` file ? 

Regards

---

### Post by slickymaster on 2013-05-29
The package you downloaded it's a Red Hat package, not a Debian one.
rpm packages are primarily meant to be used in Red Hat, Fedora and CentOS operating systems, even though they can be used in many GNU/Linux distributions.

All you have to do is to download the correct package for Ubuntu, this one: [FirebirdCS-2.5.2.26540-0.i686.tar.gz]("http://sourceforge.net/projects/firebird/files/firebird-linux-i386/2.5.2-Release/FirebirdCS-2.5.2.26540-0.i686.tar.gz/download").
Afterwards just follow these instructions: [How to install a .tar.gz (or .tar.bz2) file?]("http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file")

---

