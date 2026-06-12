---
title: "Problems starting apache (apache2_threaded_dev)"
date: 2006-02-08
forum: Server Platforms
---

### Post by rt702 on 2006-02-08
Hi all,

I had my server working fine on some older hardware but when I had a hd fail on me I used it as an excuse to get some new hardware and start anew.

Long story short; old server (ubuntu 5.10) was working fine with apache2-prefork-dev as my front end for tomcat via mod_jk.  However, I saw that there was now a threaded apache deb, so I figured I'd give that a shot.  Operating of a clean build (server install with openssh-server, and an apt-get upgrade having been run so far), I got it via apt-get and proceeded to run /etc/init.d/apache2 start....nothing....tried running it as root, sudo'ing it, etc.  I can't really see amiss in the startup script.  

Other differences:

I'm running a 64 bit build now, old server was 32.

Any advice?

---

### Post by LordHunter317 on 2006-02-08
-dev packages are devlopment packages, and don't have anything to do with running Apache.

What MPM package do you have installed?

---

### Post by rt702 on 2006-02-09
*sigh*

Thanks for pointing that out for me.  I was so hung up on getting the headers for compliling mod_jk that I forgot to get the apache2 mpm itself.  

Thanks for the heads up.


Ryan

---

