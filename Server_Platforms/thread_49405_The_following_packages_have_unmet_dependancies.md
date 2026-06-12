---
title: "The following packages have unmet dependancies"
date: 2005-07-16
forum: Server Platforms
---

### Post by DaZjorz on 2005-07-16
When I was installing the minimal base for Ubuntu Linux, it said on console 3:

The following packages have unmet dependancies:
linux-386: Depends: linux-image-386 but it is not installable
           Depends: linux-restricted-modules-386 but it is not going to be installed
E: Broken packages

I already reported this as a bug... But does someone have a solution already? I'm currently retrying the installation.

---

### Post by DaZjorz on 2005-07-16
i have restarted the pc and am now retrying install. I'll edit this post with the result.

Edit 1: The network wasn't working. Maybe that was the problem. Its working now. I typed 
modprobe 3c509
in the console BEFORE it started to check network settings and not AFTER  ](*,)


Edit 2: STILL THE SAME PROBLEM :'( but this time another error, it said:
/usr/bin/dpkg returned status 1..?

---

### Post by DaZjorz on 2005-07-16
I did the following:

I opened console 2 and typed
cd /usr/bin
ln -s udpkg dpkg
then went to console 1 and it asked me what kernel to install, I chose linux-image-2.6.10-5-386. And after a little while it finished :D:D

Strange thingy but maybe this'll be done automatically in one of the next releases of Ubuntu. :)

---

