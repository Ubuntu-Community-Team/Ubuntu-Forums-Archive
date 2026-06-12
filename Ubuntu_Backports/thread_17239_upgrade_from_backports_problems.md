---
title: "upgrade from backports problems"
date: 2005-02-27
forum: Ubuntu Backports
---

### Post by Demiurgo on 2005-02-27
I'm having problems with the apt-get upgrade from the backports repository.  
In my sources.list I have:

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

The upgrade stops because the download speed goes to zero. If I remove that line from my sources.list the upgrade works, but I can't get the packages from the backports repository.

I'm on Warty.

Any ideas?

---

### Post by mindfuse on 2005-02-27
Same problem here... both in Synaptic PM and using apt-get. Here's some info from the terminal window:

> Get:8 [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main synaptic 0.56+cvs20041119-1ubuntu4-warty+backportedfrom-ubuntu-hoary1 [1527kB]
Get:9 [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main xchat 2.4.1-0.1ubuntu1-warty+backportedfrom-ubuntu-hoary1 [266kB]
Err [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main xchat 2.4.1-0.1ubuntu1-warty+backportedfrom-ubuntu-hoary1
  Error reading from server Remote end closed connection
Get:10 [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main xchat-common 2.4.1-0.1ubuntu1-warty+backportedfrom-ubuntu-hoary1 [971kB]
Fetched 26.1MB in 4m11s (104kB/s)
Failed to fetch [http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/gimp-python_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/gimp-python_2.2.0+rel-2ubuntu1-4.10ubp1_i386.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/xchat_2.4.1-0.1ubuntu1-warty+backportedfrom-ubuntu-hoary1_i386.deb](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/xchat_2.4.1-0.1ubuntu1-warty+backportedfrom-ubuntu-hoary1_i386.deb)  Error reading from server Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Demiurgo on 2005-02-27
Ok! So I guess it does not depend on my system.  Probably they are experiencing some problems with their server or whatever the repository is on.

---

### Post by rufius on 2005-02-27
[QUOTE=Demiurgo]Ok! So I guess it does not depend on my system.  Probably they are experiencing some problems with their server or whatever the repository is on.[/QUOTE]
 Thats not the repository anymore thats why :). Check [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) for the correct one or you can use my sources.list at [http://physika.org/temp/sources.list](http://physika.org/temp/sources.list).

---

### Post by jdong on 2005-02-27
That ubuntu-bp.sourceforge.net server has been a pain in the you-know-what from day 1. I'm shutting it down for good when Hoary is released. Please switch over.

---

