---
title: "(U)(K)ubuntu 8.04 64 bit the perfect OS for DELL VOSTRO 1400"
date: 2008-09-18
forum: Testimonials &amp; Experiences
---

### Post by ukripper on 2008-09-18
Unbelievably, KUBUNTU 8.04 the best 64bit distro I’ve ever used. Just installed 2 days ago on my Dell Vostro 1400 alongside with Ubuntu 7.10 32bit. Performance jump and usability are just incredible.

My sincere thanks to Ubuntu/Kubuntu(kde3.5 not KDE4) 64 bit developers for providing such a robust distro. Even compiz works fine.

Only thing I needed to add was > options snd-hda-intel model=dell-3stack to /etc/modprobe.d/alsa-base to make the sound work in vostro 1400.

And it being the KDE I had to get used to it and sort transparency issue for conky using the following command:
```
$ feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`
```

On conky I have noticed temperatures remain under 37 degree C average usage while under 32-bit 7.10 it was over 44 degree C average, the kernel has also been so much improved from 2.6.22.

Although the HDD bug on SATA [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) still remains, but there is a fix to it –

Only for affected SATA drives mainly on Dell laptops. Power saving mode is enabled by default on 
laptop drives which may cause high frequency load and unload cycles.

To check how often your drive is load cycling:
```
$ smartctl -d ata -a /dev/sda
```
(This command is for SATA drive; you'll need to install the
smartmontools package first.)


Fix worked on ubuntu Gutsy and Hardy and should work on other distros as well:

 downloaded this file,
[http://launchpadlibrarian.net/12024037/90-hdparm.sh](http://launchpadlibrarian.net/12024037/90-hdparm.sh)

and copied it to these four directories:
/etc/acpi/ac.d
/etc/acpi/battery.d
/etc/acpi/resume.d
/etc/acpi/start.d


Installed using following commands:

```
$ sudo install 90-hdparm.sh /etc/acpi/resume.d/
$ sudo install 90-hdparm.sh /etc/acpi/start.d/
$ sudo install 90-hdparm.sh /etc/acpi/ac.d/
$ sudo install 90-hdparm.sh /etc/acpi/battery.d/
```

This will change default to 254 in adaptor mode
and 150 to battery mode.

All nonfree codecs were easily downloaded as usual:
```
$ sudo apt-get install kubuntu-restricted-extras
```

Finally, fully loaded 64-bit Buntu ready to be driven!!!!!!:popcorn:

---

