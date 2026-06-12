---
title: "Yakkety Proposed up and running"
date: 2016-04-27
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2016-04-27
Greetings,
FYI

```
The following packages will be REMOVED:
  indicator-session
The following NEW packages will be installed:
  libntfs-3g871 libqmi-glib5 libsndio6.1
The following packages have been kept back:
  usb-modeswitch-data
The following packages will be upgraded:
  alsa-utils apt apt-transport-https apt-utils autoconf bind9-host cups
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common dconf-cli dconf-gsettings-backend dconf-service debconf
  debconf-i18n dmsetup dnsutils gir1.2-atk-1.0 gir1.2-gstreamer-1.0
  gir1.2-gudev-1.0 gir1.2-pango-1.0 gir1.2-soup-2.4 gnome-session-canberra
  info install-info iso-codes libapt-inst2.0 libapt-pkg5.0 libarchive-zip-perl
  libasound2 libasound2-data libasound2-plugins libass5 libatk1.0-0
  libatk1.0-data libbasicusageenvironment1 libbind9-140 libcanberra-gtk-module
  libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module
  libcanberra-pulse libcanberra0 libclutter-1.0-0 libclutter-1.0-common
  libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libdconf1
  libdevmapper1.02.1 libdirectfb-1.2-9 libdns-export162 libdns162 libexempi3
  libexpat1 libfreetype6 libgcrypt20 libglibmm-2.4-1v5 libgpg-error0
  libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port12 libgroupsock8
  libgstreamer1.0-0 libgudev-1.0-0 libical1a libisc-export160 libisc160
  libisccc140 libisccfg140 liblwres141 libopenal-data libopenal1
  libpam-systemd libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0
  libpangoft2-1.0-0 libpangomm-1.4-1v5 libpangoxft-1.0-0 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libpython3.5 libpython3.5-minimal libpython3.5-stdlib
  libqmi-proxy libqt4-dbus libqt4-declarative libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtdbus4 libqtgui4 librsvg2-2 librsvg2-common libsasl2-2
  libsasl2-modules libsasl2-modules-db libsdl1.2debian libselinux1
  libsemanage-common libsemanage1 libsigc++-2.0-0v5 libslang2 libsnappy1v5
  libsodium18 libsoup-gnome2.4-1 libsoup2.4-1 libssh2-1 libsystemd0 libtalloc2
  libtasn1-6 libtevent0 libudev1 libusageenvironment3 libv4l-0 libv4lconvert0
  libvlc5 libvlccore8 libwavpack1 libwayland-client0 libwayland-cursor0
  libwayland-server0 libwxbase3.0-0v5 libwxgtk3.0-0v5 libxapian22v5 make
  ntfs-3g ocl-icd-libopencl1 openjdk-8-jre openjdk-8-jre-headless policykit-1
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11
  pulseaudio-utils python-cryptography python-dbus python-idna python-imaging
  python-lxml python-openssl python-pil python-pkg-resources python-sip
  python-talloc python-twisted-bin python-twisted-core python-twisted-web
  python-xapian python3-cryptography python3-dbus python3-idna python3-lxml
  python3-pkg-resources python3.5 python3.5-minimal qdbus qtcore4-l10n sed
  shared-mime-info systemd systemd-sysv udev virtualbox virtualbox-qt vlc
  vlc-data vlc-nox vlc-plugin-notify vlc-plugin-samba
192 upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 124 MB of archives.
After this operation, 21.0 MB of additional disk space will be used.
```

---

### Post by rrnbtter on 2016-04-28
Greetings,
Still getting more proposed than anything else.
```
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libquadmath0 i386 6.1.1-0ubuntu12 [204 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libitm1 i386 6.1.1-0ubuntu12 [31.2 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 gcc-6-base i386 6.1.1-0ubuntu12 [16.0 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libstdc++6 i386 6.1.1-0ubuntu12 [433 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libubsan0 i386 6.1.1-0ubuntu12 [120 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libcilkrts5 i386 6.1.1-0ubuntu12 [45.8 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libcc1-0 i386 6.1.1-0ubuntu12 [33.0 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libatomic1 i386 6.1.1-0ubuntu12 [9,918 B]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libgomp1 i386 6.1.1-0ubuntu12 [79.9 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libgcc1 i386 1:6.1.1-0ubuntu12 [46.9 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 libcgmanager0 i386 0.41-2 [32.4 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/main i386 cgmanager i386 0.41-2 [80.3 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/universe i386 libgsoap9 i386 2.8.30-1 [240 kB]                        
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/multiverse i386 virtualbox-qt i386 5.0.18-dfsg-3build1 [7,284 kB]    s
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed/multiverse i386 virtualbox i386 5.0.18-dfsg-3build1 [14.2 MB]
```

---

### Post by izznogooood on 2016-04-29
Does it function well enough for daily use at this point?

---

### Post by rrnbtter on 2016-04-29
Greetings,
I have all updates installed on an Intel system up to now. April 29 11:30AM USA Eastern Time. No problems so far and a very robust system. I guess it will be ok as long as we post problems promptly. And keep an updated ISO on the back burner just in case. Being a reinstaller from the 80's, thats my plan.

---

### Post by dino99 on 2016-04-29
> **izznogooood said:**
> Does it function well enough for daily use at this point?

The 4.4.0-22 kernel fails to build nvidia driver & virtualbox on amd64+nvidia gpu; works well in the other cases.

---

### Post by grahammechanical on 2016-04-29
> Does it function well enough for daily use at this point?

I am using it as my daily driver just like I did with Xenial Xerus. I do keep all my important data on a separate partition. And I also have more than one install of Ubuntu that I can use if the development branch breaks and "down will come baby, cradle and all."  :)

Regards

---

### Post by ventrical on 2016-04-29
I am using it here daily. No real problems  but then I am not exactly doing detailed tests and analysis atm. When I get  extra up_time accumulated I then set out to  experiment more in depth and try to complete  a given experiment. I am somewhat like grahamechanical. I have multiple installs across several formfactors networked to  physical kvm.

uhh... a few cycles back there were discussions about "rolling releases" and so basically I have been adopting this template in my approach to my current  testing methods. There has been very little breakage over all. As for nVidia and weird hardware issues I usually use the Linus Torvalds  approach <snicker> :) but .. no .. there are times when I do actually test the nVidia driver and it works .. or it completely breaks.  So I am here .. testing. I am not always reporting in.. but I am testing, lurking and learning.

Long story short - rolling release has been a success.  First steps of convergence look promising. Can't wait for snappy personal desktop:)

regards..

---

### Post by cariboo on 2016-04-29
I'm running Yakkety on my laptop and main desktop system, I use both daily, and except for a couple of crash reports after initial install, things have been running just great. My laptop is running with proposed enabled, while the desktop system is running without proposed enabled.

---

### Post by izznogooood on 2016-04-29
I´ve been looking for an hour but I cant find how to join the fun... I´d like to upgrade my 16.04...

---

### Post by QDR06VV9 on 2016-04-29
This to get to Yakkety


```
 sudo sed -i 's/xenial/yakkety/g' /etc/apt/sources.list
```

update and dist-upgrade
```
sudo apt update
sudo apt full-upgrade
```
Reboot
Now your there

---

### Post by izznogooood on 2016-04-29
I've joined the fun :)
```

anders@lenox:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety
```

---

### Post by v3.xx on 2016-04-30
This is day 4 for me, running Mate.  And yes, its stable enough for daily use.

---

### Post by P-I H on 2016-04-30
I will follow the development of Yakkety on a system with the amdgpu-pro graphic driver. Just updated a Xenial system.

---

### Post by izznogooood on 2016-04-30
I cant say i notice any difference, except my boot up time increased slightly.

Everything works, which is nice :) 

I had the Developer option (proposed) set to on in Xenial. Does it really matter in Yakety, or is everything bleeding anyway?

---

### Post by rrnbtter on 2016-04-30
Greetings,
If you check off "Proposed" in the Software and Updates section you will get a few hundred Meg of updates. That is what the word "proposed" refers to in the title of this thread. "Proposed up and running" (in Yakkety). FYI

---

### Post by sgage on 2016-05-02
For several days now, among the other updates coming through, there have been 11 packages held back. These are 9 *-heimdal packages, plus gnome-shell-extensions and usb-modeswitch-data. 

Is anyone else seing this? I only bring it up because I haven't seen it mentioned, and it has been several days now, which is longer than usual for things to get caught up.

---

### Post by izznogooood on 2016-05-02
I have one: [COLOR=#000000]usb-modeswitch-data
[/COLOR]
I tried to force it but it complaints that I will brake other dependencies... 

I Must say I have second thoughts about joining so early... This is my Desktop (With all my media and servers)... Would this be considered bleeding or testing?
(And yes, i have backup :) )

---

### Post by sgage on 2016-05-02
I take it you are not running Gnome Shell, or you'd see the others.

Just wait, and the packages will get in sync and dependencies solved.

But you probably shouldn't be running with the 'proposed' repo enabled, and perhaps not running yakkety at all, if all your stuff is on it... the whole thing could break at any time :-)

---

### Post by grahammechanical on 2016-05-02
> Would this be considered bleeding or testing?

The development release is considered the bleeding edge with proposed being the blood red colour of the edge. It is all meant for testing but the Ubuntu Quality Assurance team runs many automated tests on each daily image built. As a result the development release has not been as risky as it once was.

Regards

---

### Post by izznogooood on 2016-05-02
> **sgage said:**
> I take it you are not running Gnome Shell

No, I actually like Unity ;) (With some compiz-tweaks).
All my media is on a separate disk. Thanks for the tip, I´ll disable the proposed.

---

### Post by Smask on 2016-05-04
> **izznogooood said:**
> I have one: [COLOR=#000000]usb-modeswitch-data[/COLOR])

That's the usual held back package that normally gets installed a couple of weeks before the release date, when they update the binary. They didn't update usb-modeswitch for xenial...

---

### Post by izznogooood on 2016-05-04
I'm out (for now). I reinstalled 16.04 and am going to stay with this for a while, as this is my main Desktop/Server (and freezes of servers, small bugs etc with my main server is not comfortable). I'm sure going to miss this part of the forum ;). Good luck to you!

---

### Post by ventrical on 2016-05-04
Thanks for your interest and contributions.

---

### Post by QDR06VV9 on 2016-05-04
> **izznogooood said:**
> I'm out (for now). I reinstalled 16.04 and am going to stay with this for a while, as this is my main Desktop/Server (and freezes of servers, small bugs etc with my main server is not comfortable). I'm sure going to miss this part of the forum ;). Good luck to you!
Don't be a stranger..
> **ventrical said:**
> Thanks for your interest and contributions.
+1 But i have to add it gets better with time.:)

---

### Post by ventrical on 2016-05-04
> **runrickus said:**
> Don't be stranger..

+1 But i have to add it gets better with time.:)

Absolutely ! +1 :)

---

### Post by izznogooood on 2016-05-04
> **runrickus said:**
> Don't be a stranger..

I've been here since early 16.04. This is where "I" belong ;).

---

### Post by jerrylamos on 2016-05-04
Installed O.K.
Won't access home wired network printer on Windows 10 or on Windows XP.
Xenial on this pc, different partition, can access both.
When I get organized I'll write an ubuntu-bug  :(

---

