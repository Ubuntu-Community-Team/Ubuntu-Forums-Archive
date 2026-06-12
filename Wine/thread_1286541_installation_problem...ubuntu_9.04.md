---
title: "installation problem...ubuntu 9.04"
date: 2009-10-09
forum: Wine
---

### Post by piyush.neo on 2009-10-09
UBUNTU 9.04 while trying to install JAVA i am getting this error message...every time...
i am using a proxy server..and had given these two commands..
$ export http_proxy="http//:gram:gram1508@172.31.100.29:3128"
$ sudo apt-get install sun-java6-jre

[B]Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-bin 6-16-0ubuntu1.9.04
  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/B]

PLZ HELP...:confused:

---

### Post by hikaricore on 2009-10-09
You may or may not be aware that this isn't a WINE related issue..

You'll need to edit your sources.list file and switch from the local mirrors to another.

---

### Post by piyush.neo on 2009-10-09
sory for posting in this thread...will post it in appropriate thread...

---

