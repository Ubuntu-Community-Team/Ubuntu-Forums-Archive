---
title: "Gazelle Soundchip with alsa, how?"
date: 2006-12-19
forum: System76 Support
---

### Post by gaspedalo on 2006-12-19
Hi, I understand that the Gazelle notebook uses the Generic 14f1 ID 5045 Chipset, and  following the posting in [http://ubuntuforums.org/archive/index.php/t-274462.html]("http://ubuntuforums.org/archive/index.php/t-274462.html") it's working just fine with Edgy.
I have a HP Paliion nx6100 (6155) Notebook, which incorporates the same chip. Sound from the internal speakers worked right out of the box, unfortunately the headphones and the mic didn't. I guess it's the entries in /etc/modprobe.d/alsa-base. i heard I should add the entry 'options snd-hda-intel model=hp', but no luck.
Could someone with a running Gazelle please paste its alsa-base contents, maybe this would help.

---

### Post by crichell on 2006-12-20
Hi gaspedalo - first try to download and install the latest alsa release from alsa.org.  If that doesn't fix the problem the you can use our patch to get it working.

Directions:

download and extract alsa
extract and save the file attached to this post to alsa-kernel/pci/hda
```
sudo apt-get install linux-headers-`uname -r`
./configure --with-oss=yes --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-`uname -r`
make && sudo make install
```

This will install alsa with the appropriate patch for your mic (headphones worked for us so I'm not sure on that one.)

---

