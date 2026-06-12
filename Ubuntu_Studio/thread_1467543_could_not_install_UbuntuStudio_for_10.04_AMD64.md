---
title: "could not install UbuntuStudio for 10.04 AMD64"
date: 2010-04-30
forum: Ubuntu Studio
---

### Post by uiberto on 2010-04-30
Hi,

I created a bootable USB disk with the DVD image for UbuntuStudio 10.04 AMD64.

I was able to initiate the installation process. However, it eventually failed reporting: "No installable kernel found in the defined APT sources." This error did not occur until after my main partition was erased as part of the installation process -- lovely!

I mucked around with this for a while. /var/log/syslog reported that "/cdrom/dists/lucid/<wherever>/Packages" did not exist. The folders did not exist, but they could be found in the specified directories as "Packages.gz".

Anyhow, the typical Ubuntu 64 installation is working without any problems. I'm going to try to install the realtime kernel manually and add the ubuntustudio-audio packages later.

All-in-all, this was a little disappointing since it's wasted ~5 hours of time. If anyone else has had this problem, I'd love to hear your ideas.

Thanks as always to the Ubuntu Studio team for supporting artists!

uiberto

---

### Post by themusicalduck on 2010-04-30
I had this problem before. The problem is that you can't install UbuntuStudio (or anything that uses the alternate installer I think) from a usb drive. It is possible by using scripts and things, which I found a link for, but I can't remember where it was now.

Anyway, if you burn a dvd and use that instead, it should work.

---

### Post by l0xin on 2010-05-01
I had this problem with 9.10 - a lot of packages couldn't be found and the only way to complete the installation process was to select only a minimal number of packages. Even then it didn't find any of them on the USB drive and had to download them all, nullifying any speed improvement of using USB in the first place.

I tried 10.04 earlier and it seems even more broken in this respect, but burning a DVD (luckily I still have one) had the installation going by flawlessly.

I hope this gets fixed in future versions, there are those on Netbooks with no optical drive.

---

### Post by cub on 2010-05-01
I couldn't even install from the DVD. But installing vanilla 10.04 and then add the stuff I need for Studio worked flawless.

---

