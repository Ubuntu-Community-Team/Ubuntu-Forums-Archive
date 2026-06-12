---
title: "Software sources, Trusty or devel?"
date: 2014-01-29
forum: Ubuntu Development Version
---

### Post by philinux on 2014-01-29
Which one are you guys currently using. I'm on trusty at the moment. 

I seem to remember some discussion a long while back on this, what's the current feeling on this?

---

### Post by QDR06VV9 on 2014-01-29
I just did a check And as I thought all mine are Trusty.
I have no devel entries now.
Hope that helps.
Regards

---

### Post by ventrical on 2014-01-29
> **philinux said:**
> Which one are you guys currently using. I'm on trusty at the moment. 

I seem to remember some discussion a long while back on this, what's the current feeling on this?

 I have multiple installs on several different boxes with both trusty and devel in sources list. The only error I get with devel is duplicate entries warnings but I just ignore it as it does actually nothing to harm the release. I'll get to cleaning it up ... but lately .. here in Central North America we have been dealing with a phenomenon called a 'polar vortex' and Iv'e been doing a lot of snow lately. :) lol ... nd it's been really cold around here:) lol

---

### Post by Hazzabin on 2014-01-29
I'm the same as [COLOR=#000000]ventrical, except for the polar vortex and snow[/COLOR]

---

### Post by grahammechanical on 2014-01-29
Ubuntu Trusty + devel repositories

devel-release (expected devel got trusty)
devel-security (expected devel got trusty)
devel-updates (expected devel devel got trusty)
devel-backports (expected devel got trusty)

It is an improvement over getting saucy or a mixture of both for those four repositories. I do not see this as a problem but as a work around. I am not sure if this will change over the next 4 months unless the change in May becomes "got Ucode name." I do suspect that the devel repositories are a little out of sync with the Trusty repositories. But then the important work is going on in the trusty repositories.

Regards.

---

### Post by philinux on 2014-01-29
Righto guys but which is recommended.  I got told on #ubuntu+1 that devel is not a release.  But I remember the info that devel was the rolling release?

---

### Post by grahammechanical on 2014-01-29
It is my expectation based upon reading the tea leaves and the coffee grounds that the devel repositories will come into their own during the period of the change over from the Trusty development cycle and the Uname development cycle. Then the development release will be, in effect, a rolling release with snapshots of the code being taken (daily/weekly/monthly?) which become the daily/weekly/monthly ISO images.

Ubuntu Touch is already having image updates. That could come to the desktop. The term Ubuntu is being used to apply to the one code base for the Ubuntu mobile platform and the Ubuntu desktop platform. 

Regards.

---

### Post by seeker5528 on 2014-01-29
devel is an alias.

If you want to stick with trusty once it's released, use trusty in your sources.list.
If you want to stick with the development stuff without having to update your sources.list every time there is a release, use devel in your sources.list.

Later, Seeker

---

### Post by ventrical on 2014-01-30
> **philinux said:**
> Which one are you guys currently using. I'm on trusty at the moment. 

I seem to remember some discussion a long while back on this, what's the current feeling on this?

Here is an example still from /devel/

```



ventrical@ventrical-beta:~$ sudo apt-get update
[sudo] password for ventrical: 
Ign http://ca.archive.ubuntu.com devel InRelease
Ign http://ca.archive.ubuntu.com devel-updates InRelease                       
Ign http://ca.archive.ubuntu.com devel-backports InRelease                     
Hit http://ca.archive.ubuntu.com devel Release.gpg           
Ign http://extras.ubuntu.com devel InRelease                 
Hit http://ca.archive.ubuntu.com devel-updates Release.gpg   
Hit http://ca.archive.ubuntu.com devel-backports Release.gpg 
Ign http://extras.ubuntu.com devel Release.gpg               
Hit http://ca.archive.ubuntu.com devel Release               
Hit http://ca.archive.ubuntu.com devel-updates Release                         
Hit http://ca.archive.ubuntu.com devel-backports Release                       
Ign http://extras.ubuntu.com devel Release                                     
Hit http://ca.archive.ubuntu.com devel/main Sources                            
Hit http://ca.archive.ubuntu.com devel/restricted Sources                      
Hit http://ca.archive.ubuntu.com devel/universe Sources                        
Hit http://ca.archive.ubuntu.com devel/multiverse Sources                      
Hit http://ca.archive.ubuntu.com devel/main i386 Packages    
Hit http://ca.archive.ubuntu.com devel/restricted i386 Packages
Hit http://ca.archive.ubuntu.com devel/universe i386 Packages
Hit http://ca.archive.ubuntu.com devel/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com devel/main Translation-en_CA
Hit http://ca.archive.ubuntu.com devel/main Translation-en                     
Hit http://ca.archive.ubuntu.com devel/multiverse Translation-en               
Hit http://ca.archive.ubuntu.com devel/restricted Translation-en               
Hit http://ca.archive.ubuntu.com devel/universe Translation-en_CA              
Hit http://ca.archive.ubuntu.com devel/universe Translation-en                 
Hit http://ca.archive.ubuntu.com devel-updates/main Sources                    
Hit http://ca.archive.ubuntu.com devel-updates/restricted Sources
Hit http://ca.archive.ubuntu.com devel-updates/universe Sources
Hit http://ca.archive.ubuntu.com devel-updates/multiverse Sources              
Hit http://ca.archive.ubuntu.com devel-updates/main i386 Packages              
Hit http://ca.archive.ubuntu.com devel-updates/restricted i386 Packages        
Hit http://ca.archive.ubuntu.com devel-updates/universe i386 Packages
Hit http://ca.archive.ubuntu.com devel-updates/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com devel-updates/main Translation-en             
Hit http://ca.archive.ubuntu.com devel-updates/multiverse Translation-en       
Hit http://ca.archive.ubuntu.com devel-updates/restricted Translation-en       
Hit http://ca.archive.ubuntu.com devel-updates/universe Translation-en         
Hit http://ca.archive.ubuntu.com devel-backports/main Sources                  
Hit http://ca.archive.ubuntu.com devel-backports/restricted Sources            
Hit http://ca.archive.ubuntu.com devel-backports/universe Sources
Hit http://ca.archive.ubuntu.com devel-backports/multiverse Sources            
Err http://extras.ubuntu.com devel/main Sources                                
  404  Not Found
Hit http://ca.archive.ubuntu.com devel-backports/main i386 Packages
Hit http://ca.archive.ubuntu.com devel-backports/restricted i386 Packages
Err http://extras.ubuntu.com devel/main i386 Packages                          
  404  Not Found
Hit http://ca.archive.ubuntu.com devel-backports/universe i386 Packages        
Hit http://ca.archive.ubuntu.com devel-backports/multiverse i386 Packages
Ign http://extras.ubuntu.com devel/main Translation-en_CA                      
Hit http://ca.archive.ubuntu.com devel-backports/main Translation-en           
Ign http://extras.ubuntu.com devel/main Translation-en                         
Hit http://ca.archive.ubuntu.com devel-backports/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com devel-backports/restricted Translation-en
Hit http://ca.archive.ubuntu.com devel-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com devel/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com devel/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com devel-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com devel-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com devel-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com devel-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com devel-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com devel-backports/multiverse Translation-en_CA
Ign http://security.ubuntu.com devel-security InRelease
Ign http://ca.archive.ubuntu.com devel-backports/restricted Translation-en_CA
Hit http://security.ubuntu.com devel-security Release.gpg
Ign http://ca.archive.ubuntu.com devel-backports/universe Translation-en_CA
Hit http://security.ubuntu.com devel-security Release
Hit http://security.ubuntu.com devel-security/main Sources
Hit http://security.ubuntu.com devel-security/restricted Sources
Hit http://security.ubuntu.com devel-security/universe Sources
Hit http://security.ubuntu.com devel-security/multiverse Sources
Hit http://security.ubuntu.com devel-security/main i386 Packages
Hit http://security.ubuntu.com devel-security/restricted i386 Packages
Hit http://security.ubuntu.com devel-security/universe i386 Packages
Hit http://security.ubuntu.com devel-security/multiverse i386 Packages
Hit http://security.ubuntu.com devel-security/main Translation-en
Hit http://security.ubuntu.com devel-security/multiverse Translation-en
Hit http://security.ubuntu.com devel-security/restricted Translation-en
Hit http://security.ubuntu.com devel-security/universe Translation-en
Ign http://security.ubuntu.com devel-security/main Translation-en_CA
Ign http://security.ubuntu.com devel-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com devel-security/restricted Translation-en_CA
Ign http://security.ubuntu.com devel-security/universe Translation-en_CA
W: Conflicting distribution: http://ca.archive.ubuntu.com devel Release (expected devel but got trusty)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-updates Release (expected devel-updates but got trusty)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-backports Release (expected devel-backports but got trusty)
W: Conflicting distribution: http://security.ubuntu.com devel-security Release (expected devel-security but got trusty)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

but I still get ...

```

ventrical@ventrical-beta:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb libboost-program-options1.53.0 libboost-system1.53.0
  libcolamd2.7.1 libllvm3.3 libmirclient2 libmirclient3 libprocps1
  linux-headers-3.10.0-2 linux-headers-3.10.0-2-generic
  linux-headers-3.11.0-11 linux-headers-3.11.0-11-generic
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-headers-3.11.0-4 linux-headers-3.11.0-4-generic linux-headers-3.11.0-7
  linux-headers-3.11.0-7-generic linux-headers-3.11.0-8
  linux-headers-3.11.0-8-generic linux-headers-3.12.0-2
  linux-headers-3.12.0-2-generic linux-headers-3.13.0-1
  linux-headers-3.13.0-1-generic linux-image-3.10.0-2-generic
  linux-image-3.11.0-11-generic linux-image-3.11.0-12-generic
  linux-image-3.11.0-4-generic linux-image-3.11.0-7-generic
  linux-image-3.11.0-8-generic linux-image-3.12.0-2-generic
  linux-image-3.13.0-1-generic linux-image-extra-3.10.0-2-generic
  linux-image-extra-3.11.0-11-generic linux-image-extra-3.11.0-12-generic
  linux-image-extra-3.11.0-4-generic linux-image-extra-3.11.0-7-generic
  linux-image-extra-3.11.0-8-generic linux-image-extra-3.12.0-2-generic
  linux-image-extra-3.13.0-1-generic python3.4 python3.4-minimal tcl-lib
  tk-lib xserver-xorg-xmir
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-glamoregl
The following NEW packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor content-hub
  libcontent-hub0 libdee-qt5-3 libgsettings-qt1 libgweather-3-6
  liblttng-ust-ctl2 liblttng-ust0 libmbim-glib0 libmm-glib0 libnss3-nssdb
  libqmi-glib0 libunityvoice1 libupstart-app-launch2 liburcu1 libwebp5
  libwebpmux1 linux-headers-3.13.0-5 linux-headers-3.13.0-5-generic
  linux-image-3.13.0-5-generic linux-image-extra-3.13.0-5-generic
  python3-apparmor-click python3-click qtdeclarative5-accounts-plugin
  qtdeclarative5-ubuntu-content0.1 unity-voice-service upstart-app-launch
  upstart-app-launch-tools webapp-container xserver-xorg-video-glamoregl
The following packages will be upgraded:
  accountsservice activity-log-manager activity-log-manager-control-center
  alsa-utils apparmor apport apport-gtk at-spi2-core base-passwd binutils
  bsdutils checkbox checkbox-qt console-setup cpp-4.8 cups cups-bsd
  cups-client cups-common cups-daemon cups-ppdc cups-server-common dbus
  dbus-x11 dmz-cursor-theme dosfstools dpkg espeak-data ethtool
  evolution-data-server evolution-data-server-common evolution-data-server-goa
  folks-common fontconfig fontconfig-config fonts-droid gcc-4.8 gcc-4.8-base
  gedit gedit-common gir1.2-atspi-2.0 gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-gtk-3.0
  gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-pango-1.0
  gir1.2-soup-2.4 gir1.2-webkit-3.0 glib-networking glib-networking-common
  glib-networking-services gnome-control-center-datetime
  gnome-control-center-unity gnome-media gnome-panel gnome-panel-data
  gnome-session-fallback gnome-session-flashback gnome-sudoku gnupg gpgv grep
  groff-base grub-common grub-pc grub-pc-bin grub2-common hplip hplip-data hud
  im-config indicator-application indicator-bluetooth indicator-datetime
  indicator-messages indicator-power indicator-session indicator-sound
  kate-data katepart kde-runtime kde-runtime-data keyboard-configuration
  landscape-client-ui-install language-pack-en language-pack-gnome-en
  language-selector-common language-selector-gnome libaccountsservice0
  libapparmor-perl libapparmor1 libasan0 libatomic1 libatspi2.0-0
  libautodie-perl libblkid1 libcamel-1.2-45 libcolumbus1 libcolumbus1-common
  libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libdb5.1
  libdbus-1-3 libdjvulibre-text libdjvulibre21 libdlrestrictions1 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libebackend-1.2-7
  libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libenca0 libespeak1 libffi6
  libfolks-eds25 libfolks-telepathy25 libfolks25 libfontconfig1 libgail-3-0
  libgcc-4.8-dev libgcc1 libglamor0 libglib2.0-0 libglib2.0-bin
  libglib2.0-data libglibmm-2.4-1c2a libgmime-2.6-0 libgomp1 libgpgme++2
  libgpod-common libgpod4 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgudev-1.0-0 libgusb2 libgweather-common libharfbuzz-icu0 libharfbuzz0b
  libhpmud0 libhud-client2 libhud2 libindicator3-7 libindicator7
  libio-socket-ssl-perl libitm1 libjavascriptcoregtk-3.0-0 libjs-sphinxdoc
  libkactivities-bin libkactivities-models1 libkactivities6
  libkatepartinterfaces4 libkxmlrpcclient4 liblightdm-gobject-1-0
  libmessaging-menu0 libmount1 libnautilus-extension1a libnepomukcleaner4
  libnepomukcore4abi1 libnet-ssleay-perl libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnss3 libnss3-1d libopencv-core2.4
  libopencv-imgproc2.4 libpam-modules libpam-modules-bin libpam-runtime
  libpam-systemd libpam0g libpanel-applet-4-0 libpango-1.0-0 libpango1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libpcap0.8 libpci3
  libpython3.3 libpython3.3-minimal libpython3.3-stdlib libpython3.4
  libpython3.4-minimal libpython3.4-stdlib libqmobipocket1 libquadmath0
  librasqal3 librsvg2-2 librsvg2-common libsamplerate0 libsane-hpaio
  libselinux1 libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspeexdsp1
  libstdc++6 libsystemd-daemon0 libsystemd-journal0 libsystemd-login0
  libts-0.0-0 libudev1 libunity-control-center1 libunity-webapps0 libupstart1
  libuuid1 libwayland-client0 libwayland-cursor0 libwayland-server0
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwhoopsie0 libxaw7 libxfont1
  libxrandr2 libxv1 light-themes lightdm linux-firmware linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev login logrotate
  man-db modemmanager mount nautilus nautilus-data nepomuk-core-data
  nepomuk-core-runtime network-manager network-manager-gnome notify-osd passwd
  pciutils plasma-scriptengine-javascript printer-driver-hpcups
  printer-driver-postscript-hp python-crypto python-imaging
  python-imaging-compat python-oauthlib python-pexpect python-pexpect-doc
  python-pil python-piston-mini-client python-pkg-resources python-pycurl
  python-ubuntuone-control-panel python-xdg python3-apport python3-crypto
  python3-distupgrade python3-oauthlib python3-piston-mini-client
  python3-pkg-resources python3-problem-report python3-pycurl python3-xdg
  python3.3 python3.3-minimal python3.4 python3.4-minimal qtchooser
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets sudo systemd-services
  telepathy-idle tsconf ubuntu-artwork ubuntu-desktop ubuntu-minimal
  ubuntu-mono ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  ubuntu-settings ubuntu-standard ubuntuone-control-panel
  ubuntuone-control-panel-qt udev unity-system-compositor unity-webapps-common
  unity-webapps-qml unity-webapps-service upstart util-linux uuid-runtime
  webaccounts-extension-common webbrowser-app whoopsie x11-common xinput xorg
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-mga xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-vmware xul-ext-webaccounts
324 upgraded, 33 newly installed, 1 to remove and 0 not upgraded.
Need to get 184 MB of archives.
After this operation, 236 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by seeker5528 on 2014-02-02
> **ventrical said:**
> Here is an example still from /devel/

```

W: Conflicting distribution: http://ca.archive.ubuntu.com devel Release (expected devel but got trusty)


```

That would be a bug on one end or the other.

In theory it should be the same as when you use testing or unstable in your Debian sources.list, and I've never had those kind of messages with Debian.

I did comment some stuff out in my Ubuntu sources.list to cut down on the noise

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel main restricted

## Major bug fix updates produced after the final release of the
## distribution.

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-updates restricted main multiverse universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security main restricted
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security universe
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security multiverse

```

Later, Seeker

---

### Post by ventrical on 2014-02-04
> **seeker5528 said:**
> That would be a bug on one end or the other.

In theory it should be the same as when you use testing or unstable in your Debian sources.list, and I've never had those kind of messages with Debian.

I did comment some stuff out in my Ubuntu sources.list to cut down on the noise

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel main restricted

## Major bug fix updates produced after the final release of the
## distribution.

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-updates restricted main multiverse universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security main restricted
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security universe
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security multiverse

```

Later, Seeker

  Like you mentioned in your earlier post , it is an alias. You can use anything (word) in replacement of /devel/ and it will still come up with the development branch. The only reason I am keeping it is to see how far it will  send me verbose noise to the nearing of the release day. It is probably not important at all, but I am just curious.

---

### Post by QDR06VV9 on 2014-02-04
@Ventrical Thanks I completely removed These about 2 weeks ago.
```
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security main restricted
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security universe
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security multiverse  
```
Just added them back now commented out.;)

---

### Post by ventrical on 2014-02-04
> **runrickus said:**
> @Ventrical Thanks I completely removed These about 2 weeks ago.
```
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse

# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security main restricted
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security universe
# deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ devel-security multiverse  
```
Just added them back now commented out.;)

And thank you also! . I'll keep that in my pocket as  a memory peg for sure. :)

---

