---
title: "Differences between Ubuntu and Fedora"
date: 2008-08-23
forum: The Cafe
---

### Post by ubguess on 2008-08-23
what are the basic differences between Ubuntu and Fedora? Why would one person choose one over the other...?

Thanks.

---

### Post by Diabolis on 2008-08-23
Ubuntu is based in Debian and Fedora is based in Redhat. They used different formats for the installation of packages.

Redhat uses .rpm files and Debian uses .deb files.

You can read a lot about this topic by googleing "Redhat vs Debian"

---

### Post by ubguess on 2008-08-23
Any other reasons - like useability, functionality, applications...?

---

### Post by insane_alien on 2008-08-23
moslty minor. with enough tweaking you can make ubuntu run like fedora and fedora run like ubuntu. even down to the package managers.

a lot of the default configurations are changed and its really too long to list and pretty trivial differences.

---

### Post by Hilipatti on 2008-08-23
Fedora only has "free"-packages.. So you can't download codecs or the nvidia/ati blobs, which is a huge turnoff for me. Fedora has about 5000 packets and Ubuntu has 20000, if I remember right. I hate adding non-official repositories. Fedora is also very much bleeding edge. It also has a good customizable installer, the Ubuntu installer is somewhat simpler but it's like a Windows install. Every box ends up the same pretty much since you can't customize the packages etc.

And Fedora is more like a "real" distro, since it has proper runlevels and no sudo etc. It's also pretty security-focused.

The default theme in Fedora is awesome though, unlike Ubuntu's. And yes it actually does matter to people, I wouldn't change the theme in Fedora but I do in Ubuntu since it's so horrid. And I'd think that many people actually don't change their themes.

---

### Post by cardinals_fan on 2008-08-23
Fedora tends to be a bit more bleeding edge.  You'll get new stuff quicker, but at the risk of bugs.

---

### Post by SunnyRabbiera on 2008-08-23
yeh but I hate YUM and its front ends, apt needs to catch up on fedora as I cant stand YUM

---

### Post by cardinals_fan on 2008-08-23
> **SunnyRabbiera said:**
> yeh but I hate YUM and its front ends, apt needs to catch up on fedora as I cant stand YUM
[http://apt-rpm.org/](http://apt-rpm.org/)

---

### Post by mthei on 2008-08-23
I found that Fedora has better hardware support, at least on my machine. It ran quieter than Ubuntu (7.10) did, and a lot of things that didn't work well for me in Ubuntu (suspend/resume, and a handful of X-server issues) work flawlessly in Fedora. Yes, it's "bleeding edge", but a lot of bugs get fixed very quickly. It very well may be my favourite distro along with Debian and OpenSUSE, and recommend it over all else.
I also found that it uses less memory than Ubuntu, especially with certain aspects of Gnome, like Nautilus would rarely run higher than 10mb.

However, there are some downsides:
-Support cycle is 13 months, compared to Ubuntu 18 months for most releases, three years for LTS, and OpenSUSE has support for two years.

-After recently switching to Debian (because of the above), I can now say that YUM is inferior to APT, something that I didn't really notice when I first switched to Fedora. It brings in all dependencies as needed, much like APT, but when removing software, I've often found that I had to remove depencies myself, which can often be a hassle, especially if you accidentally remove something that's still in use by another program.

As mentioned, you need to add some other repositories, and I believe Livna is indeed supported by the Fedora team. However, I've found Livna's packages to be very buggy.

---

### Post by SunnyRabbiera on 2008-08-23
> **cardinals_fan said:**
> [http://apt-rpm.org/](http://apt-rpm.org/)

yes but I have used it and its not all that great as it is on debian systems.

---

### Post by stmiller on 2008-08-23
Fedora: no 'grey/sketchy' codecs provided by Fedora. So no mp3 playback. Though these things are provided by third party groups. Fedora is all about freedom and free formats.

...whereas Ubuntu comes 'free' likewise, but makes codecs easy to install (simply apt-get install ubuntu-restricted-codecs )

Fedora is more bleeding edge. There are tons of updates daily, and often things will break. New kernels come out, whereas Ubuntu does not update kernel versions- only patches same kernel with security updates.

Ubuntu has a large community which is very forum friendly (here). Fedora's community is largest on mailing lists (hosted on redhat.com). Lots of Redhat devs run Fedora desktop.

Ubuntu also has much more software than Fedora, as Ubuntu is based on Debian. However, most software on the net will often provide an .rpm for Fedora or Redhat users...

/my thoughts

---

