---
title: "Optimal Squid repo"
date: 2013-02-14
forum: Server Platforms
---

### Post by freakalad on 2013-02-14
Hi guys,

[Been a while since last post]

I've been using apt-cacher-ng quite successfully for a number of years now, as I have a number of Ubuntu & Debian (*.deb) systems on my network - baremetal & VM's.

So far, so good, but it fails to address the RedHat (*.rpm @ yum) & other distro's quite as well.

I've now provisioned a VM running Squid3 & it seems to be holding pretty well so far, based largely on the work found [here]("http://archive09.linux.com/feature/153221") & [here]("http://itkia.com/using-squid-to-cache-apt-updates-for-debian-and-ubuntu/").

What I'd really like to do is not filter/cache *all* my traffic, but dedicate the instance to only do so for POSIX packages & images (.deb, .rpm, .img, .iso, etc), and in doing so also sort then into some appropriate mounted NFS shares & to store those files indefinately, unless there are newer versions of same files: ie. ISO @ nas:/mnt/iso , DEB @ nas:/mnt/apt , RPM @ nas:/mnt/yum

What's nice re apt-cacher-ng, is that it'll store (& expire) packages that have passed through it indefinitely, & has some very handy tools to check if those files are still cool, and if not, allows me to purge unreferenced, damaged or bogus .deb's 

Could anyone with ninja squid-fu skills please offer some advice on how to achieve such an outcome?

---

