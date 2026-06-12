---
title: "Minimal Slackware"
date: 2008-03-21
forum: Slackware and derivatives
---

### Post by kevCast on 2008-03-21
I recently performed a minimal Slackware install, installing package series A, AP, D, F, K, L, and N. I would like to get X installed now, but the only option in seeing is downloading and compiling every tar.gz from xorgs site. However, I like my inner child, so I want to avoid that. How would I go about doing this? I've tried pkgtool and mounting the Slack CD, but it's yielded nothing.

---

### Post by saulgoode on 2008-03-21
You should be able to install all the packages you need with the following commands:

***installpkg -infobox -tagfile /mnt/cdrom/slackware-12.0/slackware/x/tagfile /mnt/cdrom/slackware-12.0/slackware/x/*.tgz***

***installpkg -infobox -tagfile /mnt/cdrom/slackware-12.0/slackware/xap/tagfile /mnt/cdrom/slackware-12.0/slackware/xap/*.tgz***

---

### Post by niethslim on 2008-03-29
You can download and install slackpkg (only 1 package), configure it and then do:
> 
slackpkg install x
 

---

### Post by Whiffle on 2008-03-29
The packages are also compiled and ready to use, available on the second cd and various mirrors.

---

