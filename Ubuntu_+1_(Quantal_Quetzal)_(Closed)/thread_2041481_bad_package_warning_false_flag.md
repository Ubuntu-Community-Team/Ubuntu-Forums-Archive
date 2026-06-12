---
title: "bad package warning false flag?"
date: 2012-08-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-12
Is this package warning a false flag? I installed through software center.

---

### Post by mc4man on 2012-08-12
I wouldn't say false flag - the package failed a lintian check.
It should have had a conffile file in it's Debian that had something like - 
```
etc/cron.daily/google-earth
```
Whether this matters much probably not...
(don't think the cron.daily file is of much value either

---

### Post by ventrical on 2012-08-12
Thanks mac4man.

At this stage I'll put that one on the shelf for now.

---

### Post by effenberg0x0 on 2012-08-12
There are some instructions for bulding a package / installing Google Earth here: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I'm not sure if it's right or up-to-date, but it's worth a read / try.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-12
Ouch... ia32-libs, ia32-libs-multiarch depends... It will ask you to remove a lot of stuff:i386, reinstall them again, I never really got it, I'm ignorant about multiarch vs ia32 and never had the will to study it a little. But in my experience, whenever apt says anything about apt-get install ia32/ia32-multiarch I know it's a install destroyer. 

Regards,
Effenberg

---

### Post by mc4man on 2012-08-12
I think the best way for g-e, at least on 64 bit  is to just use a prebuilt package.
There are 2 avail., whether any different not sure - 
google-earth-stable_6.0.3.2197-r0_amd64.deb
google-earth-stable_current_amd64.deb

Probably both the same - the former shows a later mod date when looked at thru file-roller

(which does bring up that the current file-roller cannot open .deb or .gz, you have to revert 2 ubuntu releases back.

In any event, just to see, did repair the package though hardly worth the effort
(has to be extracted, a conffile added & repacked, this should be totally done as root to keep permissions correct.

---

### Post by effenberg0x0 on 2012-08-12
> **mc4man said:**
> I think the best way for g-e, at least on 64 bit  is to just use a prebuilt package.
There are 2 avail., whether any different not sure - 
google-earth-stable_6.0.3.2197-r0_amd64.deb
google-earth-stable_current_amd64.deb

Probably both the same - the former shows a later mod date when looked at thru file-roller

(which does bring up that the current file-roller cannot open .deb or .gz, you have to revert 2 ubuntu releases back.

In any event, just to see, did repair the package though hardly worth the effort
(has to be extracted, a conffile added & repacked, this should be totally done as root to keep permissions correct.

```
sudo dpkg -i googleearth_6.0.3.2197+0.7.0-1_amd64.deb
```
...
```
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on libfreeimage3; however:
  Package libfreeimage3 is not installed.
 googleearth depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.

dpkg: error processing googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for mime-support ...
Processing triggers for menu ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...

```

Then:
```


sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bluez-alsa:i386 esound-common glib-networking:i386 gstreamer0.10-plugins-base:i386 gvfs:i386 gvfs-libs:i386
  libaa1:i386 libacl1:i386 libaio1:i386 libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2:i386 libaudiofile1:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libbz2-1.0:i386 libc6:i386 libcaca0:i386
  libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386 libcomerr2:i386 libcroco3:i386 libcups2:i386
  libcupsimage2:i386 libcurl3:i386 libdatrie1:i386 libdb5.1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386
  libdv4:i386 libesd0:i386 libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreeimage3 libfreetype6:i386 libgcc1:i386 libgconf-2-4:i386 libgcrypt11:i386 libgd2-xpm:i386 libgdbm3:i386
  libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libglib2.0-0:i386 libgnome-bluetooth10 libgnome-keyring0:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgudev-1.0-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386
  libibus-1.0-0:i386 libice6:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386
  libllvm3.0:i386 libltdl7:i386 liblzma5:i386 libmad0:i386 libmikmod2:i386 libmng1:i386 libmpg123-0:i386
  libmysqlclient18:i386 libncurses5:i386 libncursesw5:i386 libnspr4:i386 libnss3:i386 libodbc1:i386 libogg0:i386
  libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386
  libpng12-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386 libqt4-dbus:i386
  libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386 libqt4-qt3support:i386 libqt4-script:i386
  libqt4-scripttools:i386 libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386
  libselinux1:i386 libshout3:i386 libslang2:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386
  libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386
  libstdc++5:i386 libstdc++6:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3:i386 libtdb1:i386 libthai0:i386
  libtheora0:i386 libtiff4:i386 libtiff5:i386 libtinfo5:i386 libudev0:i386 libunistring0:i386 libusb-0.1-4:i386
  libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libwavpack1:i386 libwebp2:i386 libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxaw7:i386 libxcb-glx0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxft2:i386
  libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxslt1.1:i386 libxss1:i386 libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386
  odbcinst1debian2:i386 xaw3dg:i386 zlib1g:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libfreeimage3
The following packages will be REMOVED:
  googleearth intel-gpu-tools libdrm-nouveau2 libgl1-mesa-dri libva-x11-1 vlc xdiagnose xorg
  xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-radeon xserver-xorg-video-vmware
The following NEW packages will be installed:
  libfreeimage3
0 upgraded, 1 newly installed, 14 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 812 kB of archives.
After this operation, 96.2 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

It's silly and I can't explain why but whenever I see ":arch" after apt stdout I know I'll have to read about ia32 vs multiarch in order to not do something stupid. For some reason I immediately lose the will to continue, do something decent, learn about it once and for all. My fingers automatically ctrl+c.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-12
The ia32-libs is just a transitional to the ia32-libs-multiarch package

---

### Post by ventrical on 2012-08-13
> **effenberg0x0 said:**
> There are some instructions for bulding a package / installing Google Earth here: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I'm not sure if it's right or up-to-date, but it's worth a read / try.

Regards,
Effenberg

Thanks you guys.I was just trying an experiment. I have a few dumb-terminals that I may try it on later.

---

### Post by ventrical on 2012-08-13
What I did was download:

google-earth-stable_current_i386.deb

from google website:

then I used Qapt and it downloaded some depends first, then installed it flawlessly.

What an awesome program! :)


Works good on faster systems.

---

