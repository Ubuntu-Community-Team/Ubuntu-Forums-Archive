---
title: "Meerkat Ion - No sound with HDMI"
date: 2010-04-06
forum: System76 Support
---

### Post by edlyk on 2010-04-06
Hello All,

I just bought a Meerkat Ion and connected to my TV via HDMI.  I am not getting any sound over HDMI. I did go to System->Pref->Sound and switch the sound output to HDMI.

If I try connecting to the TV via normal RGB with audio cable the sound works fine. I am also get sound via headphone jack.  Just not via HDMI cable.

The HDMI cable and TV input work fine when connected to Asus O!Play and WDTV, so I am pretty sure problem is in Meerkat.

Any ideas?

Thanks,
Ed

---

### Post by thomasaaron on 2010-04-06
Please have a look at this post...

[http://ubuntuforums.org/showthread.php?t=1335841&highlight=meerkat+ion](http://ubuntuforums.org/showthread.php?t=1335841&highlight=meerkat+ion)

---

### Post by edlyk on 2010-04-06
Yes, that fixed it!  :P

Now if I can get it to stay in 720p after reboot instead of switching back to 1080i I will be a truly happy camper!  I have XBMC installed on this little jewel connected to a 42" Vizio and it is quite impressive.

---

### Post by edlyk on 2010-04-08
BTW - In case anyone cares, I found the solution to the screen resolution not saving:

1- Run: cd /etc/X11 
2- Run: sudo mv xorg.conf xorg.conf.backup 
4- Run: sudo nvidia-xconfig
5- Run: gksu nvidia-settings
6- Setup some video parameters like resolution 
7-  click on [Save to X configuration file] buttom


Everything is now PERFECT!  I really love this machine!

---

