---
title: "Tascam US-600 audio interface"
date: 2012-12-29
forum: Ubuntu Studio
---

### Post by Luksion Knight on 2012-12-29
Has anyone had any luck with the US-600 under Ubuntu or ubuntu studio? 

I already have the medibuntu repos and installed alsa-tools, alsa-firmwareloader and libasound2

The interface doesn't show up when I issue the command. ```
cat /proc/asound/modules
```

Thanks in advance and happy new year

---

### Post by CrocoDuck on 2012-12-31
Hi! I never tried a Tascam device, but I found a lot of infos about Tascam US-122. I was wondering if something  similar could be tried with US-600  too, when I found this page, it looks more general: [http://alsa.opensrc.org/Tascam_US-428](http://alsa.opensrc.org/Tascam_US-428) . Here the other infos I found searching for drivers, scripts, firmware,  .asoundrc and similar stuff for your soundcard (I repost even if I'm quite sure you have already found it): [http://ubuntuforums.org/showpost.php?p=6272809&postcount=3](http://ubuntuforums.org/showpost.php?p=6272809&postcount=3) , [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122) , [http://alsa.opensrc.org/Tascam_US-224](http://alsa.opensrc.org/Tascam_US-224) , (this one is in italian) [http://marcomarana.altervista.org/scheda-audio-tascam-us122l-su-ubuntu-e-mint/](http://marcomarana.altervista.org/scheda-audio-tascam-us122l-su-ubuntu-e-mint/) . Hope there is something useful for you.

---

### Post by Luksion Knight on 2012-12-31
The US-122 and [US-428]("http://homerecording.com/bbs/user-forums-brand/tascam-user-forum/us-428-usb-2-0-compatibility-72715/") both operate on USB 1(.1?) whereas the US-600 is a USB 2.0 interface. 

Likewise I have not found any material providing support for tascam's other USB 2.0 interfaces such as the US-122 and 144 mkII models. 

Are there any USB 2.0 interface drivers working under Ubuntu?

---

### Post by Knocks on 2013-01-15
Have you tried asking at [TASCAM forums]("http://www.tascamforums.com")?  Those guys are a great resource on TASCAM gear and sound recording in general.

---

