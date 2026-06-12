---
title: "Fastest Install Break You Have Made"
date: 2012-03-13
forum: The Cafe
---

### Post by Jaybyrrd on 2012-03-13
Post your fastest install break/major mistake you have ever made. For example, I decided to reinstall Ubuntu 11.10 today, and like an idiot I clicked out of a terminal box in the middle of apt-get. It said that I couldn't take control of dpkg, so I brilliant (without thinking or research) went with my gut...
sudo rm -r /var/lib/dpkg .... 

Oops, I forgot the /lock part. Guess who might just resort to reinstalling Ubuntu if it doesn't work after this apt-get update. :)

Post yours.

---

### Post by julioneander on 2012-03-14
Don't know if this counts, but anyway:

I once broke my system at install time. Yeah, I decided to specify the partitions and mount points without letting Ubuntu do it for me.

Result: no bootloader and no swap partition. I thought to myself: "Alright, maybe I can fix this with the livecd session", but somehow I managed to break the system even more! After some reboots and a few kernel panics, I gave up and formatted the disk to do it all again from scratch.

Regards.

---

### Post by QIII on 2012-03-14
Back in the "roll your own" days just trying to install was breaking it sometimes.

---

### Post by winh8r on 2012-03-14
Fastest ever breakage of a system was when I got dd if= and dd of= mixed up and wrote 80GB of zeros to a hard drive I was trying to clone.

---

### Post by odiseo77 on 2012-03-14
Once I was installing Gentoo and the installer crashed while partitioning. As a result, the partition table got wiped and the disk got messed up. I had to use testdisk to recover my data.

---

