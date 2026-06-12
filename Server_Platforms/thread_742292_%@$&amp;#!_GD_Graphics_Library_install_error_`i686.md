---
title: "%@$&amp;#! GD Graphics Library install error: `i686-pc-linux' not recognized"
date: 2008-04-01
forum: Server Platforms
---

### Post by luvit on 2008-04-01
I'm installing SMF Forum Software and this is to install the GD Graphics Library Package. This is Ubuntu Server, so my command line skills are... well... I have limited command line skills.

> ~$ wget [http://www.libgd.org/releases/gd-2.0.35.tar.bz2](http://www.libgd.org/releases/gd-2.0.35.tar.bz2)
--14:30:56--  [http://www.libgd.org/releases/gd-2.0.35.tar.bz2](http://www.libgd.org/releases/gd-2.0.35.tar.bz2)
           => `gd-2.0.35.tar.bz2.2'
Resolving [www.libgd.org](www.libgd.org)... 213.251.181.15
Connecting to www.libgd.org|213.251.181.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,212,730 (1.2M) [application/x-bzip]

100%[====================================>] 1,212,730    470.63K/s             

14:30:59 (469.65 KB/s) - `gd-2.0.35.tar.bz2.2' saved [1212730/1212730]

looks good, right?

> ~$ tar xvjf gd-2.0.35.tar.bz2
output was w/o errors...

> ~$ cd gd-2.0.35
ok the next step has me lost:

> ~/gd-2.0.35$ ./configure
checking build system type... Invalid configuration `i686-pc-linux-oldld': machine `i686-pc-linux' not recognized
configure: error: /bin/bash config/config.sub i686-pc-linux-oldld failed
~/gd-2.0.35$ 


What to do? I get the same error with older packages...

---

### Post by BillGod on 2008-04-01
apt-get install php5-gd should install all the packages you need without compiling.

---

### Post by luvit on 2008-04-01
will that file interfere with my LAMP install? ...prolly a silly question..

---

