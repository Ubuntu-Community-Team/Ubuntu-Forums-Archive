---
title: "Wine - no audio (possibly because of updated pkg)"
date: 2009-05-21
forum: Wine
---

### Post by supersonicdarky on 2009-05-21
I *think* some alsa lib was updated and that caused the breakage. I tried reinstalling wine (completely) to no avail. Here's the err:
```
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": /usr/bin/../lib/wine/winealsa.drv.so: symbol snd_pcm_forward, version ALSA_0.9.0rc8 not defined in file libasound.so.2 with link time reference
```
Both files exist (/usr/lib/wine/winealsa.drv.so and /usr/lib/libasound.so.2). When I try to go to the audio tab in winecfg, it gives me an error that alsa registry exists when there is no alsa device and asks me to remove, to which I click cancel.

Wine 1.1.21.
Sidux (Debian Sid).

Packages updated in the last 24h:
```
kernel@fission /var/cache/apt/archives $ find -mtime 0
.
./partial
./dpkg_1.15.1_amd64.deb
./dpkg-dev_1.15.1_all.deb
./infobash_3.22_all.deb
./libavutil50_5%3a0.5+svn20090521-0.0_amd64.deb
./libtasn1-3-dev_2.2-1_amd64.deb
./libtasn1-3_2.2-1_amd64.deb
./libpurple0_2.5.6-1_amd64.deb
./finch_2.5.6-1_amd64.deb
./libavcodec52_5%3a0.5+svn20090521-0.0_amd64.deb
./libavformat52_5%3a0.5+svn20090521-0.0_amd64.deb
./libpostproc51_5%3a0.5+svn20090521-0.0_amd64.deb
./libswscale0_5%3a0.5+svn20090521-0.0_amd64.deb
./mencoder_1%3a1.0.rc2svn20090521-0.0_amd64.deb
./mplayer_1%3a1.0.rc2svn20090521-0.0_amd64.deb
./pidgin-data_2.5.6-1_all.deb
./gparted_0.4.5-1_amd64.deb
./gstreamer0.10-plugins-good_0.10.15-1_amd64.deb
[color=red]./libasound2-dev_1.0.20-1_amd64.deb[/color]
[color=red]./lib32asound2_1.0.20-1_amd64.deb[/color]
[color=red]./libasound2_1.0.20-1_amd64.deb[/color]
./gstreamer0.10-plugins-bad_0.10.12-1_amd64.deb
./irqbalance_0.55-4_amd64.deb
./libcupsys2_1.3.10-2_all.deb
./libcupsys2-dev_1.3.10-2_all.deb
./libavdevice52_5%3a0.5+svn20090521-0.0_amd64.deb
./libavfilter0_5%3a0.5+svn20090521-0.0_amd64.deb
./ffmpeg_5%3a0.5+svn20090521-0.0_amd64.deb
./libtotem-plparser12_2.26.2-1_amd64.deb
```

Any help is appreciated.

---

### Post by cogadh on 2009-05-21
You might need the ALSA 32 bit libs instead of just the 64 bit ones.

---

### Post by supersonicdarky on 2009-05-21
> ./lib**32**asound2_1.0.20-1_amd64.deb
./libasound2_1.0.20-1_amd64.deb

Is there. As I said, this is breakage, not that it never worked.

---

### Post by cogadh on 2009-05-21
Ah, missed that one. Sorry about that.

---

### Post by YokoZar on 2009-05-22
[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/305860](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/305860)

---

### Post by dsstester on 2009-05-27
I am running debain sid/sidux and i noticed exactly the same problem.

i reverted to the older alsa file versions from debian testing (based on 1.0.19-x) :-

alsa-base
alsa-utils
lib32asound
libasound2
linux-sound-base
ia32-libs (version 2.7)


looks like the new 1.0.20 update throws some kind of spanner in the works.

Please can someone report back when this is fixed, so i can carry on upgrading this stuff!

Thanks in advance! :popcorn:

---

