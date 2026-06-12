---
title: "Ubuntu Kylin"
date: 2013-03-30
forum: Ubuntu Development Version
---

### Post by sammiev on 2013-03-30
I folks, I have been using raring for some time now and did a fresh install of the beta lastnight. I now have Ubuntu Kylin after selecting the raring beta1 download. How do I get rid of Kylin and just have raring?

Thanks
sammiev

---

### Post by ping-wu on 2013-03-30
I have been told that if you install the ubuntukylin-default-settings package, you can convert a regular Raring to Kylin, although I have never tried it myself.  I suppose (?) if you remove this package it should cause your Kylin to be reverted back to Raring.  At least give this a try before you re-install Raring.

---

### Post by sammiev on 2013-03-30
I guess I should have marked this as soved. I deleted the packages "ubuntukylin-theme" and "chinese-calendar" and all was OK. :)

Thanks
sammiev

---

### Post by ping-wu on 2013-03-30
The Kylin iso is 1G vs. 800M for Raring.  There are probably a number of other packages that you don't need.  But as long as they do not adversely affect the performance, I guess it is OK.

---

### Post by mikewhatever on 2013-03-31
If you add ubuntukylin-default-settings on a clean install or Raring, here are the dependencies:

> 
The following NEW packages will be installed:
  cheese cheese-common chinese-calendar fcitx fcitx-bin fcitx-config-common fcitx-config-gtk fcitx-data fcitx-frontend-all fcitx-frontend-gtk2
  fcitx-frontend-gtk3 fcitx-frontend-qt4 fcitx-googlepinyin fcitx-libs fcitx-libs-gclient fcitx-libs-qt fcitx-module-dbus fcitx-module-kimpanel
  fcitx-module-lua fcitx-module-x11 fcitx-modules fcitx-pinyin fcitx-sunpinyin fcitx-table fcitx-table-all fcitx-table-bingchan
  fcitx-table-cangjie fcitx-table-dianbaoma fcitx-table-erbi fcitx-table-wanfeng fcitx-table-wbpy fcitx-table-wubi fcitx-table-ziranma
  fcitx-ui-classic firefox-locale-zh-hans fonts-arphic-ukai fonts-arphic-uming gir1.2-gconf-2.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
  gnome-tweak-tool gnome-video-effects gstreamer1.0-plugins-bad gwibber-service-sina gwibber-service-sohu indicator-china-weather libaacs0
  libass4 libavcodec53 libavformat53 libavutil51 libbluray1 libcheese-gtk23 libcheese7 libdca0 libdirectfb-1.2-9 libdvdnav4 libdvdread4
  libenca0 libfaad2 libflite1 libgif4 libgme0 libgooglepinyin0 libgsm1 libgstreamer-plugins-bad1.0-0 liblua5.2-0 libmimic0 libmms0 libmodplug1
  libmpg123-0 libopus0 libpostproc52 libreoffice-help-zh-cn libreoffice-l10n-zh-cn libschroedinger-1.0-0 libsdl1.2debian libsoundtouch0
  libspandsp2 libsunpinyin3 libswscale2 libts-0.0-0 libva1 libvdpau1 libvo-aacenc0 libvo-amrwbenc0 libxvidcore4 libzbar0 mplayer2 python-apport
  python-problem-report smplayer smplayer-themes smplayer-translations sunpinyin-data thunderbird-locale-zh-cn thunderbird-locale-zh-hans
  tsconf ttf-arphic-ukai ttf-wqy-zenhei ubuntukylin-default-settings ubuntukylin-theme unity-china-music-scope
0 upgraded, 103 newly installed, 0 to remove and 4 not upgraded.
Need to get 111 MB of archives.
After this operation, 267 MB of additional disk space will be used.



---

### Post by ping-wu on 2013-03-31
Thanks for playing with ubuntukylin-default-settings.  I wanted to take a look at this package myself but there are so many things I would like to do but with just so little extra time available.  

I have a Raring notebook and a Kylin notebook laying side-by-side on my desk.  They are identical notebooks. By selecting English-US locale for both systems, these two machines also (at least appear to) behave identically (except the Chinese calendar and the Kylin theme which I don't mind). 

Kylin has the potential to reach 1.4 billion users.  This number is so mind-boggling that it cannot be taken lightly--at least to me :-) .

---

