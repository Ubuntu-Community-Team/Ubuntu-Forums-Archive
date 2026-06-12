---
title: "Building apache from source"
date: 2012-02-07
forum: Server Platforms
---

### Post by kerryhall on 2012-02-07
If I'm building apache from source, (and installing to /usr/local/) the httpd.conf is in /usr/local/apache2/conf/ but where would conf.d go? And are there any other config files or folders I gotta worry about? 

Thanks!

---

### Post by Mosome on 2012-02-07
There's quite a few extra commands you have to do, besides just the ./Configure .. make install ones.  Check out the README instructions and it should tell you the extra steps to take.  I believe there is a script to build the conf directories that has be executed, but it's been awhile since I made a build.

Try this link, which includes a full Linux-Apache-MySQL-PHP build:

[http://www.lamphowto.com/](http://www.lamphowto.com/)

---

