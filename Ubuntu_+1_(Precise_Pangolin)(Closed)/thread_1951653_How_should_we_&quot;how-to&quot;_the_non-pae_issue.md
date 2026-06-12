---
title: "How should we &quot;how-to&quot; the non-pae issue?"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-04-02
I'm struggling here :(

I think I pretty much know how to provide the options to install a non-pae Precise system:

#1: Both Lubuntu and Xubuntu are non-pae.

But the Lubuntu life-cycle will only be 18 months:

verification link needed

And Xubuntu's life cycle will only be 3 years:

[http://osdir.com/ml/xubuntu-users/2012-02/msg00024.html](http://osdir.com/ml/xubuntu-users/2012-02/msg00024.html)

#2: The non-pae mini.iso:

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

#3: David Henningsson created an Ubuntu Beta 1 (yes Beta 1) image:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)

#4: I hope to work out a conversion from either Lubuntu or Xubuntu to other DE's but I really need to wait until we hit the final release  so I don't have to rinse and repeat too many times.

My biggest problem is finding an appropriate title. This is too long:

If you see, "This kernel requires the following features not present on the CPU: pae. Unable to boot - please use a kernel appropriate for you CPU."

What would a good search-able title be?

---

### Post by jbicha on 2012-04-02
And of course, there's the option of installing 11.10 and then upgrading.

I believe 12.04 is planned to be the last release to support non-PAE so that should be mentioned too in the sticky.

---

### Post by QIII on 2012-04-02
How to: "Unable to boot, PAE kernel warning"?

---

### Post by cariboo on 2012-04-03
We usually create a current release issues and work around thread on the day of release, perhaps a post informing members that the non-pae kernel isn't included on the Live CD install, and that they either have to do an upgrade to Precise in order to be able to use it, or use Lubuntu or Xubuntu instead.

Using the mini.iso is to much for the Ubuntu target user, but I'd suggest a howto in Installations  & Upgrades, for those that are willing enough to give it a try.

---

### Post by jerrylamos on 2012-04-03
The message that says "this kernel won't work on your pc" should list the URL for Ubuntu "how to" instructions, as in Wiki etc.

My opinion, by far the best would in the Wiki a pointer to a version of 
Beta 1 or whatever that will run generic.  

This happens to be lubuntu.  Runs fine, great actually, but does not show off "Unity Feetures" that ubuntu management is promoting.

Haven't tried installing Unity-2D on lubuntu.

mini.iso on my speed internet, just fine for youtube videos, takes forever and a day to install the stuff needed for a usable desktop.

Do note, if it were possible for install to recognize it needed a different kernel, go ahead and download it from the internet.  Way way less of a download than updating from 11.10.

Oh, well, I test whatever ubuntu throws over the wall on whatever pc's that have the ultra latest feetures high speed and large memory and flags that ubuntu (compiz) demands and write launchpad bugs.  64 bit?  128 bit??

Have fun.

Jerry

---

### Post by kansasnoob on 2012-04-03
> **jbicha said:**
> And of course, there's the option of installing 11.10 and then upgrading.

I believe 12.04 is planned to be the last release to support non-PAE so that should be mentioned too in the sticky.

Good points, I'll be sure to include that.

---

### Post by kansasnoob on 2012-04-03
> **QIII said:**
> How to: "Unable to boot, PAE kernel warning"?

I like that.

---

### Post by kansasnoob on 2012-04-03
> **cariboo907 said:**
> We usually create a current release issues and work around thread on the day of release, perhaps a post informing members that the non-pae kernel isn't included on the Live CD install, and that they either have to do an upgrade to Precise in order to be able to use it, or use Lubuntu or Xubuntu instead.

Using the mini.iso is to much for the Ubuntu target user, but I'd suggest a howto in Installations  & Upgrades, for those that are willing enough to give it a try.

This all makes great sense, thanks.

---

### Post by kansasnoob on 2012-04-03
> **jerrylamos said:**
> The message that says "this kernel won't work on your pc" should list the URL for Ubuntu "how to" instructions, as in Wiki etc.

My opinion, by far the best would in the Wiki a pointer to a version of 
Beta 1 or whatever that will run generic.  

This happens to be lubuntu.  Runs fine, great actually, but does not show off "Unity Feetures" that ubuntu management is promoting.

Haven't tried installing Unity-2D on lubuntu.

mini.iso on my speed internet, just fine for youtube videos, takes forever and a day to install the stuff needed for a usable desktop.

Do note, if it were possible for install to recognize it needed a different kernel, go ahead and download it from the internet.  Way way less of a download than updating from 11.10.

Oh, well, I test whatever ubuntu throws over the wall on whatever pc's that have the ultra latest feetures high speed and large memory and flags that ubuntu (compiz) demands and write launchpad bugs.  64 bit?  128 bit??

Have fun.

Jerry

Since you have a Pentium M I'm going to pester you for some testing in the next couple of weeks.

---

### Post by NHclimber on 2012-04-03
Every suggestion I have is not PG...

---

### Post by jerrylamos on 2012-04-03
> **kansasnoob said:**
> Since you have a Pentium M I'm going to pester you for some testing in the next couple of weeks.

O.K., but do note I've got a "strange" pentium M that will run ubuntu generic-pae.  I've seen a couple posts from other people that haven't been able to get past the boot check for pae flag.

Way back when mine used to fail the pae test but doesn't lately, maybe they changed the code on testing so mine slips by the test.

I don't know if it's because it has 768 MB memory, which is a 256 and a 512.  I'd expect many Thinkpad T40's to be topped out at 1 GB.

I'm on another pc at the moment, when I get back on the Pentium M I'll post the flag set.

My even older laptop is a Thinkpad R31, circa 2005, which has a Celeron which does have the pae flag.  Runs lubuntu O.K. video jerky likely the integrated Intel video chip.  Will run Ubuntu-2D slowly.

Jerry

---

### Post by jerrylamos on 2012-04-04
Here's the non-pae cpuinfo
```
jerry@Thinkpad-T40:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1500MHz
stepping	: 5
cpu MHz		: 1500.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips	: 2990.47
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:
```

Is there any way to test the code that CD Live uses to determine non-pae capability?  I think I've seen posts somewhere on this forum from someone with a T41 who couldn't boot CD Live.

I've been happily running Lubuntu Beta 2.  I could try an ubuntu Unity-2D if it were of any use to anyone.

Jerry

---

### Post by jerrylamos on 2012-04-04
I do have a partition with Pangolin Beta 1 generic-pae. Just booted it for this post. I haven't updated it lately having too much fun with lubuntu.  I could zsync ubuntu-pae just to see if CD Live still boots or not.

For some reason, cpuinfo on lubuntu Beta 2 this morning reported 600 cpu MHz.  Runs fine.

Booted ubunt-pae for cpuinfo and meminfo: 

jerry@ThinkPad-T40:~$ ./lsb
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux ThinkPad-T40 3.2.0-19-generic-pae #30-Ubuntu SMP Fri Mar 16 18:34:15 UTC 2012 i686 i686 i386 GNU/Linux

```
jerry@ThinkPad-T40:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1500MHz
stepping	: 5
microcode	: 0x7
cpu MHz		: 1500.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips	: 2990.38
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 32 bits virtual
power management:

jerry@ThinkPad-T40:~$ cat /proc/meminfo
MemTotal:         765636 kB
MemFree:           51524 kB
Buffers:           45376 kB
Cached:           294812 kB
SwapCached:           68 kB
Active:           266784 kB
Inactive:         378840 kB
Active(anon):     154868 kB
Inactive(anon):   154668 kB
Active(file):     111916 kB
Inactive(file):   224172 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         765636 kB
LowFree:           51524 kB
SwapTotal:       2040216 kB
SwapFree:        2039896 kB
Dirty:               716 kB
Writeback:             0 kB
AnonPages:        305380 kB
Mapped:           100020 kB
Shmem:              4100 kB
Slab:              36416 kB
SReclaimable:      24984 kB
SUnreclaim:        11432 kB
KernelStack:        2752 kB
PageTables:        10340 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2423032 kB
Committed_AS:    2129832 kB
VmallocTotal:     250488 kB
VmallocUsed:        8128 kB
VmallocChunk:     241396 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       54656 kB
DirectMap2M:      731136 kB 

```

Jerry

---

### Post by kansasnoob on 2012-04-05
> **jerrylamos said:**
> Here's the non-pae cpuinfo
```
jerry@Thinkpad-T40:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1500MHz
stepping	: 5
cpu MHz		: 1500.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips	: 2990.47
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:
```

Is there any way to test the code that CD Live uses to determine non-pae capability?  I think I've seen posts somewhere on this forum from someone with a T41 who couldn't boot CD Live.

I've been happily running Lubuntu Beta 2.  I could try an ubuntu Unity-2D if it were of any use to anyone.

Jerry

No need to test anything ATM that I know of. However, what I'm curious to see is how conversion from either Lubuntu or Xubuntu to Ubuntu or Kubuntu works kernel-wise.

But we're not ready to test that yet .............. at least I'm not ;)

---

### Post by kansasnoob on 2012-04-05
Note to self:

I (or we) need to include Edubuntu in the conversation. Have I missed any other official derivative?

---

### Post by cariboo on 2012-04-05
> **kansasnoob said:**
> Note to self:

I (or we) need to include Edubuntu in the conversation. Have I missed any other official derivative?

Mythbuntu is also an official version, although it is a bit of a niche project, and also the server version. :)

---

### Post by kansasnoob on 2012-04-05
> **cariboo907 said:**
> Mythbuntu is also an official version, although it is a bit of a niche project, and also the server version. :)

Thanks, I'd somehow always thought that Myth was just an "add-on" but I see there is a daily build, and both it and Edubuntu appear to be using the PAE kernel.

Some time next week I should have time to hammer out a pre-release "how-to" of sorts.

---

### Post by jerrylamos on 2012-04-05
> **kansasnoob said:**
> No need to test anything ATM that I know of. However, what I'm curious to see is how conversion from either Lubuntu or Xubuntu to Ubuntu or Kubuntu works kernel-wise.

But we're not ready to test that yet .............. at least I'm not ;)

Right now I've got a massive update to 3.2.0-22 going on in the background.

When I get bored I could give a whirl on the Thinkpad T40 going from lubuntu to ubuntu-2D.  Do I just select the ubuntu desktop from synaptic?

Lubuntu Beta 2 ubiquity won't install on my Thinkpad R31.  Ubiquity vanishes shortly after starting copying files.  Grub2 is blasted.  That requires a messy re-install of Grub2 to boot the other partitions.  Yes I entered a launchpad bug. Alpha installed fine.

Somewhat out of topic, the R31 has a pae flag even though it's older than the T40, I could try installing unity-2D - a bit slow on 512 MB 1 GHz with the sluggish intel integrated graphics - is there a way to install lubuntu from unity-2D ??  Mini takes eons with my internet service.

Jerry

---

### Post by kansasnoob on 2012-04-05
Well, I am going to need someone with a non-pae Lubuntu or Xubuntu machine to run the command "sudo apt-get install ubuntu-desktop". When I do it on a pae supported machine I get:

```
lance@lance-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-21-generic linux-headers-3.2.0-21 libgarcon-1-0
  libgarcon-common exo-utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acpi-support acpid activity-log-manager-common
  activity-log-manager-control-center adium-theme-ubuntu aisleriot apg
  app-install-data-partner appmenu-gtk appmenu-gtk3 appmenu-qt apturl
  apturl-common at-spi2-core avahi-autoipd bamfdaemon baobab binutils
  bluez-alsa bluez-cups bluez-gstreamer branding-ubuntu brasero brasero-cdrkit
  brasero-common brltty checkbox checkbox-qt cmap-adobe-japan2 compiz
  compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default
  compizconfig-backend-gconf cups-bsd dc deja-dup doc-base docbook-xml
  duplicity dvd+rw-tools empathy empathy-common eog espeak espeak-data
  evolution-data-server evolution-data-server-common example-content
  firefox-gnome-support folks-common fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-opensymbol fonts-takao-pgothic
  fonts-thai-tlwg fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma
  fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee
  fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush
  fonts-tlwg-waree foomatic-db-engine gcalctool gcc gcc-4.6 gedit gedit-common
  geoclue geoclue-ubuntu-geoip ginn gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dee-1.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-indicate-0.7
  gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0
  gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-soup-2.4 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gnome-accessibility-themes gnome-bluetooth
  gnome-control-center gnome-control-center-data gnome-desktop3-data
  gnome-font-viewer gnome-games-data gnome-icon-theme-symbolic gnome-media
  gnome-menus gnome-nettool gnome-online-accounts gnome-orca
  gnome-power-manager gnome-screensaver gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-share gnomine
  growisofs gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x guile-1.8-libs gvfs-bin gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hwdata ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-pinyin-db-open-phrase ibus-table indicator-application
  indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-printers indicator-session indicator-sound
  indicator-status-provider-mc5 intel-gpu-tools kerneloops-daemon
  landscape-client-ui-install laptop-detect launchpad-integration
  libatk-adaptor libatk-adaptor-schemas libatkmm-1.6-1 libatspi2.0-0
  libavahi-gobject0 libbamf0 libbamf3-0 libboost-serialization1.46.1
  libbrasero-media3-1 libbrlapi0.5 libc-dev-bin libc6-dev libcairo-perl
  libcairomm-1.0-1 libcamel-1.2-29 libcanberra-gtk-module libcanberra-gtk0
  libcanberra-pulse libcmis-0.2-0 libcompizconfig0 libcrypt-passwdmd5-perl
  libcupsdriver1 libcurl3 libcurl3-nss libdbusmenu-qt2 libdconf-dbus-1-0
  libdconf-qt0 libdecoration0 libdee-1.0-4 libdmapsharing-3.0-2 libdotconf1.0
  libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10 libedata-book-1.2-11
  libedata-cal-1.2-13 libedataserver-1.2-15 libedataserverui-3.0-1 libespeak1
  libexempi3 libexiv2-11 libexttextcat-data libexttextcat0 libfolks-eds25
  libfolks-telepathy25 libfolks25 libfreerdp-plugins-standard libfreerdp1
  libgail-common libgdata-common libgdata13 libgee2 libgexiv2-1 libglew1.6
  libglewmx1.6 libglib-perl libglibmm-2.4-1c2a libgmime-2.6-0
  libgnome-control-center1 libgnome-desktop-3-2 libgnome-media-profiles-3.0-0
  libgnome-menu-3-0 libgnome-menu2 libgnome2-common libgnomekbd-common
  libgnomekbd7 libgoa-1.0-0 libgoa-1.0-common libgomp1 libgtk2-perl
  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libgtkspell-3-0 libgweather-3-0 libgweather-common libgwibber-gtk2
  libgwibber2 libhyphen0 libidl-common libidl0 libido3-0.1-0 libindicate-gtk3
  libindicate5 libindicator-messages-status-provider1
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 liblouis-data liblouis2
  liblua5.1-0 libmetacity-private0 libmission-control-plugins0 libmng1
  libmysqlclient18 libmythes-1.2-0 libnotify-bin libnux-2.0-0
  libnux-2.0-common liboauth0 libopencc1 liborbit2 liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libpackagekit-glib2-14 libpam-gnome-keyring
  libpango-perl libpangomm-1.4-1 libpeas-1.0-0 libpeas-common libprotobuf7
  libprotoc7 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulsedsp libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1
  libqtgui4 libquadmath0 libquvi-scripts libquvi7 librarian0 libraw5
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  librest-0.7-0 librhythmbox-core5 librsync1 libsonic0 libspeechd2 libssh-4
  libstlport4.6ldbl libsyncdaemon-1.0-1 libtelepathy-farstream2
  libtelepathy-logger2 libtimezonemap1 libtotem-plparser17 libtotem0
  libubuntuoneui-3.0-1 libunity-2d-private0 libunity-core-5.0-5 libunity-misc4
  libunity9 libuuid-perl libvncserver0 libwacom-common libwacom2
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwmf0.2-7-gtk libwnck-3-0
  libwnck-3-common libyaml-tiny-perl libyelp0 libzeitgeist-1.0-1 light-themes
  linux-headers-3.2.0-22-generic-pae linux-headers-generic-pae linux-libc-dev
  mahjongg make manpages-dev media-player-info metacity metacity-common
  mousetweaks mscompress mtools mysql-common nautilus nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager-pptp
  network-manager-pptp-gnome notify-osd notify-osd-icons nux-tools
  obexd-client onboard oneconf overlay-scrollbar pcmciautils pinyin-database
  pkg-config plymouth-theme-ubuntu-logo policykit-desktop-privileges
  pptp-linux printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-min12xxw printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix protobuf-compiler pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-aptdaemon.pkcompat python-brlapi python-configglue
  python-dateutil python-debtagshw python-dirspec python-egenix-mxdatetime
  python-egenix-mxtools python-gconf python-gi-cairo python-gst0.10
  python-libproxy python-louis python-mako python-markupsafe python-openssl
  python-packagekit python-pam python-piston-mini-client python-protobuf
  python-pyatspi2 python-pyinotify python-serial python-speechd
  python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python-virtkey python-zeitgeist qdbus qt-at-spi radeontool rarian-compat
  remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone rtkit seahorse sessioninstaller sgml-data shotwell
  sni-qt software-center software-center-aptdaemon-plugins speech-dispatcher
  ssh-askpass-gnome syslinux syslinux-common telepathy-gabble telepathy-haze
  telepathy-idle telepathy-indicator telepathy-logger
  telepathy-mission-control-5 telepathy-salut thunderbird
  thunderbird-globalmenu thunderbird-gnome-support toshset totem totem-common
  totem-mozilla totem-plugins ttf-indic-fonts-core ttf-punjabi-fonts
  ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-sso-client
  ubuntu-sso-client-gtk ubuntu-system-service ubuntu-wallpapers
  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-couch ubuntuone-installer unity unity-2d unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool unity-common
  unity-greeter unity-lens-applications unity-lens-files unity-lens-music
  unity-lens-video unity-scope-musicstores unity-scope-video-remote
  unity-services uno-libs3 ure usb-creator-common usb-creator-gtk vino whois
  whoopsie wodim xcursor-themes xdg-user-dirs-gtk xdiagnose xfonts-mathml yelp
  yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common
Suggested packages:
  gnome-cards-data binutils-doc vcdimager libdvdcss2 dvdauthor readom
  brltty-speechd brltty-x11 console-braille checkbox-cli checkbox-gtk bonnie++
  bootchart bzr cvs ethtool flex fwts git-core nmap smartmontools sox stress
  compizconfig-settings-manager gnome-themes python-boto
  python-rackspace-cloudfiles docbook docbook-dsssl docbook-xsl
  docbook-defguide ncftp ssh python-paramiko cdrskin empathy-call evolution
  evolution-data-server-dbg foomatic-db-gutenprint gcc-multilib autoconf
  automake1.9 libtool bison gdb gcc-doc gcc-4.6-multilib libmudflap0-4.6-dev
  gcc-4.6-doc gcc-4.6-locales libgcc1-dbg libgomp1-dbg libquadmath0-dbg
  libmudflap0-dbg binutils-gold desktop-base gnome-session-fallback
  apache2.2-bin libapache2-mod-dnssd gwibber-service-flickr
  gwibber-service-digg gwibber-service-statusnet gwibber-service-foursquare
  gwibber-service-friendfeed gwibber-service-pingfm gwibber-service-qaiku
  unity-lens-gwibber libgnome2-0 konqueror cdrdao glibc-doc
  libfont-freetype-perl exiv2 xfreerdp glew-utils libgtk2-perl-doc
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev qt4-qtconfig libreoffice-base libreoffice-style-hicontrast
  libreoffice-style-crystal libreoffice-style-oxygen libreoffice-evolution
  libreoffice-java-common kde-icons-crystal crystalcursors tango-icon-theme
  libreoffice-gcj libreoffice-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre openjdk-7-jre sun-java5-jre sun-java6-jre
  java5-runtime jre ubuntuone-client-dbg libvncserver0-dbg
  gnome-games-extra-data make-doc gnome-themes-standard floppyd gnome-sushi
  samba psutils hannah-foo2zjs tk8.4 tix pavumeter paman paprefs
  pulseaudio-module-raop pulseaudio-esound-compat python-egenix-mxdatetime-dbg
  python-egenix-mxdatetime-doc python-egenix-mxtools-dbg
  python-egenix-mxtools-doc python-gnome2-doc python-gst0.10-dev
  python-gst0.10-dbg python-beaker python-mako-doc python-openssl-doc
  python-openssl-dbg python-pam-dbg python-pyinotify-doc python-wxgtk2.8
  python-wxgtk2.6 python-wxgtk python-twisted-bin-dbg python-tk python-glade2
  python-qt3 gnome-codec-install seahorse-plugins perlsgml doc-html-w3 opensp
  libxml2-utils speech-dispatcher-festival speech-dispatcher-doc-cs
  libttspico-utils speech-dispatcher-flite latex-xft-fonts gromit
  x-ttcidfont-conf ubuntuone-client-proxy ubuntuone-client-gnome-dbg
  ubuntuone-control-panel-gui vinagre cdrkit-doc otf-stix ttf-lyx ttf-dejavu
Recommended packages:
  ubuntu-sso-client-gui
The following NEW packages will be installed:
  acpi-support acpid activity-log-manager-common
  activity-log-manager-control-center adium-theme-ubuntu aisleriot apg
  app-install-data-partner appmenu-gtk appmenu-gtk3 appmenu-qt apturl
  apturl-common at-spi2-core avahi-autoipd bamfdaemon baobab binutils
  bluez-alsa bluez-cups bluez-gstreamer branding-ubuntu brasero brasero-cdrkit
  brasero-common brltty checkbox checkbox-qt cmap-adobe-japan2 compiz
  compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default
  compizconfig-backend-gconf cups-bsd dc deja-dup doc-base docbook-xml
  duplicity dvd+rw-tools empathy empathy-common eog espeak espeak-data
  evolution-data-server evolution-data-server-common example-content
  firefox-gnome-support folks-common fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-opensymbol fonts-takao-pgothic
  fonts-thai-tlwg fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma
  fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee
  fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush
  fonts-tlwg-waree foomatic-db-engine gcalctool gcc gcc-4.6 gedit gedit-common
  geoclue geoclue-ubuntu-geoip ginn gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dee-1.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-indicate-0.7
  gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0
  gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-soup-2.4 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gnome-accessibility-themes gnome-bluetooth
  gnome-control-center gnome-control-center-data gnome-desktop3-data
  gnome-font-viewer gnome-games-data gnome-icon-theme-symbolic gnome-media
  gnome-menus gnome-nettool gnome-online-accounts gnome-orca
  gnome-power-manager gnome-screensaver gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-share gnomine
  growisofs gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x guile-1.8-libs gvfs-bin gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hwdata ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-pinyin-db-open-phrase ibus-table indicator-application
  indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-printers indicator-session indicator-sound
  indicator-status-provider-mc5 intel-gpu-tools kerneloops-daemon
  landscape-client-ui-install laptop-detect launchpad-integration
  libatk-adaptor libatk-adaptor-schemas libatkmm-1.6-1 libatspi2.0-0
  libavahi-gobject0 libbamf0 libbamf3-0 libboost-serialization1.46.1
  libbrasero-media3-1 libbrlapi0.5 libc-dev-bin libc6-dev libcairo-perl
  libcairomm-1.0-1 libcamel-1.2-29 libcanberra-gtk-module libcanberra-gtk0
  libcanberra-pulse libcmis-0.2-0 libcompizconfig0 libcrypt-passwdmd5-perl
  libcupsdriver1 libcurl3 libcurl3-nss libdbusmenu-qt2 libdconf-dbus-1-0
  libdconf-qt0 libdecoration0 libdee-1.0-4 libdmapsharing-3.0-2 libdotconf1.0
  libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10 libedata-book-1.2-11
  libedata-cal-1.2-13 libedataserver-1.2-15 libedataserverui-3.0-1 libespeak1
  libexempi3 libexiv2-11 libexttextcat-data libexttextcat0 libfolks-eds25
  libfolks-telepathy25 libfolks25 libfreerdp-plugins-standard libfreerdp1
  libgail-common libgdata-common libgdata13 libgee2 libgexiv2-1 libglew1.6
  libglewmx1.6 libglib-perl libglibmm-2.4-1c2a libgmime-2.6-0
  libgnome-control-center1 libgnome-desktop-3-2 libgnome-media-profiles-3.0-0
  libgnome-menu-3-0 libgnome-menu2 libgnome2-common libgnomekbd-common
  libgnomekbd7 libgoa-1.0-0 libgoa-1.0-common libgomp1 libgtk2-perl
  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libgtkspell-3-0 libgweather-3-0 libgweather-common libgwibber-gtk2
  libgwibber2 libhyphen0 libidl-common libidl0 libido3-0.1-0 libindicate-gtk3
  libindicate5 libindicator-messages-status-provider1
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 liblouis-data liblouis2
  liblua5.1-0 libmetacity-private0 libmission-control-plugins0 libmng1
  libmysqlclient18 libmythes-1.2-0 libnotify-bin libnux-2.0-0
  libnux-2.0-common liboauth0 libopencc1 liborbit2 liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libpackagekit-glib2-14 libpam-gnome-keyring
  libpango-perl libpangomm-1.4-1 libpeas-1.0-0 libpeas-common libprotobuf7
  libprotoc7 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulsedsp libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1
  libqtgui4 libquadmath0 libquvi-scripts libquvi7 librarian0 libraw5
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  librest-0.7-0 librhythmbox-core5 librsync1 libsonic0 libspeechd2 libssh-4
  libstlport4.6ldbl libsyncdaemon-1.0-1 libtelepathy-farstream2
  libtelepathy-logger2 libtimezonemap1 libtotem-plparser17 libtotem0
  libubuntuoneui-3.0-1 libunity-2d-private0 libunity-core-5.0-5 libunity-misc4
  libunity9 libuuid-perl libvncserver0 libwacom-common libwacom2
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwmf0.2-7-gtk libwnck-3-0
  libwnck-3-common libyaml-tiny-perl libyelp0 libzeitgeist-1.0-1 light-themes
  linux-headers-3.2.0-22-generic-pae linux-headers-generic-pae linux-libc-dev
  mahjongg make manpages-dev media-player-info metacity metacity-common
  mousetweaks mscompress mtools mysql-common nautilus nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager-pptp
  network-manager-pptp-gnome notify-osd notify-osd-icons nux-tools
  obexd-client onboard oneconf overlay-scrollbar pcmciautils pinyin-database
  pkg-config plymouth-theme-ubuntu-logo policykit-desktop-privileges
  pptp-linux printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-min12xxw printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix protobuf-compiler pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-aptdaemon.pkcompat python-brlapi python-configglue
  python-dateutil python-debtagshw python-dirspec python-egenix-mxdatetime
  python-egenix-mxtools python-gconf python-gi-cairo python-gst0.10
  python-libproxy python-louis python-mako python-markupsafe python-openssl
  python-packagekit python-pam python-piston-mini-client python-protobuf
  python-pyatspi2 python-pyinotify python-serial python-speechd
  python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python-virtkey python-zeitgeist qdbus qt-at-spi radeontool rarian-compat
  remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone rtkit seahorse sessioninstaller sgml-data shotwell
  sni-qt software-center software-center-aptdaemon-plugins speech-dispatcher
  ssh-askpass-gnome syslinux syslinux-common telepathy-gabble telepathy-haze
  telepathy-idle telepathy-indicator telepathy-logger
  telepathy-mission-control-5 telepathy-salut thunderbird
  thunderbird-globalmenu thunderbird-gnome-support toshset totem totem-common
  totem-mozilla totem-plugins ttf-indic-fonts-core ttf-punjabi-fonts
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-system-service
  ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome
  ubuntuone-control-panel ubuntuone-couch ubuntuone-installer unity unity-2d
  unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-asset-pool unity-common unity-greeter unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores
  unity-scope-video-remote unity-services uno-libs3 ure usb-creator-common
  usb-creator-gtk vino whois whoopsie wodim xcursor-themes xdg-user-dirs-gtk
  xdiagnose xfonts-mathml yelp yelp-xsl zeitgeist zeitgeist-core
  zeitgeist-datahub zenity zenity-common
0 upgraded, 519 newly installed, 0 to remove and 0 not upgraded.
Need to get 252 MB/263 MB of archives.
After this operation, 864 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
lance@lance-desktop:~$ 

```

If you parse that closely you'll see that 'linux-headers-3.2.0-22-generic-pae' & 'linux-headers-generic-pae' are being installed. So converting to Ubuntu or Kubuntu from either Xubuntu or Lubuntu may be more difficult than expected ;)

---

### Post by cariboo on 2012-04-05
I've got a couple of P4 systems in my shop, I'll check to see if they are non-pae today, if they are, i'll try the upgrade from Lubuntu to the ubuntu-desktop, seeing as there doesn't seem to be anyone else willing to step up to the plate and give it a try.

---

### Post by Elfy on 2012-04-05
piskie tried with old laptop - no go :(

---

### Post by NHclimber on 2012-04-05
> **cariboo907 said:**
> I've got a couple of P4 systems in my shop, I'll check to see if they are non-pae today, if they are, i'll try the upgrade from Lubuntu to the ubuntu-desktop, seeing as there doesn't seem to be anyone else willing to step up to the plate and give it a try.

I'll give it a whirl tonight on my Pentium-M laptop.  Gives me an excuse to 'fresh install' Lubuntu anyway.

---

### Post by cariboo on 2012-04-05
Thanks forestpiskie and NHclimber. I had some real life stuff to do that I hadn't planned on so I put things off until Friday.

---

### Post by kansasnoob on 2012-04-06
> **forestpiskie said:**
> piskie tried with old laptop - no go :(

I wondered about this :(

What did things seem to choke on?

---

### Post by Elfy on 2012-04-06
> **kansasnoob said:**
> I wondered about this :(

What did things seem to choke on?

Sorry - was in a hurry and not very clear - didn't do it - it had pae flag.

I have some bits in the loft - might see if there is enough to create a frankenstein - if there is I will try with that.

---

### Post by kansasnoob on 2012-04-06
I decided to parse 'ubuntu-desktop' recommends and depends just a bit and I think just using "--no-install-recommends" may solve this:

```
lance@lance-desktop:~$ **sudo apt-get install --no-install-recommends ubuntu-desktop**
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-21-generic linux-headers-3.2.0-21 libgarcon-1-0
  libgarcon-common exo-utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adium-theme-ubuntu apg at-spi2-core bamfdaemon baobab checkbox checkbox-qt
  compiz compiz-core compiz-gnome compiz-plugins-default
  compiz-plugins-main-default compizconfig-backend-gconf doc-base docbook-xml
  eog gcalctool gedit gedit-common gir1.2-gmenu-3.0 gir1.2-gtksource-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-peas-1.0 gir1.2-soup-2.4
  gir1.2-webkit-3.0 gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-font-viewer gnome-icon-theme-symbolic gnome-media
  gnome-menus gnome-nettool gnome-power-manager gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools
  gvfs-bin intel-gpu-tools launchpad-integration libatk-adaptor
  libatk-adaptor-schemas libatkmm-1.6-1 libatspi2.0-0 libbamf3-0
  libboost-serialization1.46.1 libcairomm-1.0-1 libcanberra-gtk0
  libcompizconfig0 libdbusmenu-qt2 libdconf-dbus-1-0 libdconf-qt0
  libdecoration0 libdee-1.0-4 libexempi3 libgee2 libglew1.6 libglewmx1.6
  libglibmm-2.4-1c2a libgnome-control-center1 libgnome-desktop-3-2
  libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgnome2-common
  libgnomekbd-common libgnomekbd7 libgoa-1.0-0 libgoa-1.0-common
  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 libmetacity-private0 libmng1
  libnotify-bin libnux-2.0-0 libnux-2.0-common libpangomm-1.4-1 libpeas-1.0-0
  libpeas-common libprotobuf7 libpulsedsp libqt4-dbus libqt4-declarative
  libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-svg libqt4-xml
  libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4
  librarian0 librest-0.7-0 libunity-2d-private0 libunity-core-5.0-5
  libunity-misc4 libunity9 libuuid-perl libwacom-common libwacom2
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwnck-3-0 libwnck-3-common
  libyaml-tiny-perl libyelp0 libzeitgeist-1.0-1 light-themes metacity
  metacity-common nautilus nautilus-sendto notify-osd nux-tools oneconf
  pkg-config pulseaudio pulseaudio-utils python-debtagshw python-gconf
  python-gi-cairo python-openssl python-piston-mini-client python-twisted-bin
  python-twisted-core python-twisted-web python-ubuntu-sso-client
  rarian-compat seahorse sgml-data software-center
  software-center-aptdaemon-plugins ssh-askpass-gnome ubuntu-artwork
  ubuntu-mono ubuntu-sounds ubuntu-sso-client ubuntu-system-service
  ubuntu-wallpapers unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-asset-pool unity-common unity-greeter
  unity-services whois xdg-user-dirs-gtk xdiagnose yelp yelp-xsl zenity
  zenity-common
Suggested packages:
  checkbox-cli checkbox-gtk bonnie++ bootchart bzr cvs ethtool flex fwts
  git-core make nmap obexd-client smartmontools sox stress wodim
  compizconfig-settings-manager gnome-themes docbook docbook-dsssl docbook-xsl
  docbook-defguide libcanberra-gtk-module gnome-user-guide desktop-base
  gnome-session-fallback gnome-screensaver libgnome2-0 konqueror glew-utils
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev qt4-qtconfig gnome-themes-standard totem mp3-decoder gnome-sushi
  evolution thunderbird claws-mail pavumeter paman paprefs
  pulseaudio-module-raop pulseaudio-esound-compat python-gnome2-doc
  python-openssl-doc python-openssl-dbg python-twisted-bin-dbg python-tk
  python-glade2 python-qt3 python-wxgtk2.8 seahorse-plugins perlsgml
  doc-html-w3 opensp libxml2-utils ttf-dejavu
Recommended packages:
  python-dateutil python-gst0.10 gnome-online-accounts mousetweaks ubuntu-docs
  indicator-sound indicator-power libcanberra-pulse hwdata qdbus
  libqt4-sql-mysql libqt4-sql-odbc libqt4-sql-psql libqt4-sql-sqlite zeitgeist
  zeitgeist-core brasero notify-osd-icons pulseaudio-module-x11 rtkit
  gir1.2-gudev-1.0 laptop-detect python-pam python-serial
  gir1.2-launchpad-integration-3.0 sessioninstaller acpi-support
  activity-log-manager-control-center aisleriot app-install-data-partner
  avahi-autoipd bluez-alsa bluez-cups bluez-gstreamer branding-ubuntu brltty
  cmap-adobe-japan2 cups-bsd deja-dup empathy example-content
  firefox-gnome-support fonts-kacst-one fonts-khmeros-core fonts-lao
  fonts-takao-pgothic fonts-thai-tlwg gcc ginn gnome-accessibility-themes
  gnome-bluetooth gnome-orca gnome-sudoku gnomine gwibber ibus-gtk3
  ibus-pinyin ibus-pinyin-db-android ibus-table kerneloops-daemon
  landscape-client-ui-install libgail-common libpam-gnome-keyring
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libreoffice-calc
  libreoffice-gnome libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer libwmf0.2-7-gtk
  linux-headers-generic-pae mahjongg nautilus-share network-manager-pptp
  network-manager-pptp-gnome onboard overlay-scrollbar pcmciautils
  plymouth-theme-ubuntu-logo policykit-desktop-privileges printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-min12xxw printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio-module-bluetooth pulseaudio-module-gconf
  python-aptdaemon.pkcompat qt-at-spi remmina rhythmbox
  rhythmbox-plugin-magnatune rhythmbox-ubuntuone shotwell sni-qt
  speech-dispatcher telepathy-idle thunderbird-gnome-support totem-mozilla
  ttf-indic-fonts-core ttf-punjabi-fonts ubuntuone-client-gnome
  ubuntuone-installer usb-creator-gtk vino whoopsie xcursor-themes
  ubuntu-sso-client-gtk ubuntu-sso-client-gui unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-video indicator-appmenu
  indicator-application indicator-datetime indicator-messages
  indicator-printers indicator-session
The following NEW packages will be installed:
  adium-theme-ubuntu apg at-spi2-core bamfdaemon baobab checkbox checkbox-qt
  compiz compiz-core compiz-gnome compiz-plugins-default
  compiz-plugins-main-default compizconfig-backend-gconf doc-base docbook-xml
  eog gcalctool gedit gedit-common gir1.2-gmenu-3.0 gir1.2-gtksource-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-peas-1.0 gir1.2-soup-2.4
  gir1.2-webkit-3.0 gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-font-viewer gnome-icon-theme-symbolic gnome-media
  gnome-menus gnome-nettool gnome-power-manager gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools
  gvfs-bin intel-gpu-tools launchpad-integration libatk-adaptor
  libatk-adaptor-schemas libatkmm-1.6-1 libatspi2.0-0 libbamf3-0
  libboost-serialization1.46.1 libcairomm-1.0-1 libcanberra-gtk0
  libcompizconfig0 libdbusmenu-qt2 libdconf-dbus-1-0 libdconf-qt0
  libdecoration0 libdee-1.0-4 libexempi3 libgee2 libglew1.6 libglewmx1.6
  libglibmm-2.4-1c2a libgnome-control-center1 libgnome-desktop-3-2
  libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgnome2-common
  libgnomekbd-common libgnomekbd7 libgoa-1.0-0 libgoa-1.0-common
  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 libmetacity-private0 libmng1
  libnotify-bin libnux-2.0-0 libnux-2.0-common libpangomm-1.4-1 libpeas-1.0-0
  libpeas-common libprotobuf7 libpulsedsp libqt4-dbus libqt4-declarative
  libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-svg libqt4-xml
  libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4
  librarian0 librest-0.7-0 libunity-2d-private0 libunity-core-5.0-5
  libunity-misc4 libunity9 libuuid-perl libwacom-common libwacom2
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwnck-3-0 libwnck-3-common
  libyaml-tiny-perl libyelp0 libzeitgeist-1.0-1 light-themes metacity
  metacity-common nautilus nautilus-sendto notify-osd nux-tools oneconf
  pkg-config pulseaudio pulseaudio-utils python-debtagshw python-gconf
  python-gi-cairo python-openssl python-piston-mini-client python-twisted-bin
  python-twisted-core python-twisted-web python-ubuntu-sso-client
  rarian-compat seahorse sgml-data software-center
  software-center-aptdaemon-plugins ssh-askpass-gnome ubuntu-artwork
  ubuntu-desktop ubuntu-mono ubuntu-sounds ubuntu-sso-client
  ubuntu-system-service ubuntu-wallpapers unity unity-2d unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool unity-common
  unity-greeter unity-services whois xdg-user-dirs-gtk xdiagnose yelp yelp-xsl
  zenity zenity-common
0 upgraded, 175 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.8 MB/50.9 MB of archives.
After this operation, 196 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

Unless my eyes are failing me that eliminates the pae pkgs ................. I hope.

---

### Post by Elfy on 2012-04-06
> **kansasnoob said:**
> ...

Unless my eyes are failing me that eliminates the pae pkgs ................. I hope.

Not seeing pae pkgs either - not seeing any kernel at all though.

---

### Post by kansasnoob on 2012-04-06
> **forestpiskie said:**
> Not seeing pae pkgs either - not seeing any kernel at all though.

That's what we want though. I ran those commands from a Precise Lubuntu installation.

I'll hopefully have time in just the next couple of days to try some trials and see if I can keep a non-pae box non-pae.

---

### Post by kansasnoob on 2012-04-06
Clearly some of the other missing recommends would leave one with a fairly borked Ubuntu:

```
Recommended packages:
  python-dateutil python-gst0.10 gnome-online-accounts mousetweaks ubuntu-docs
  indicator-sound indicator-power libcanberra-pulse hwdata qdbus
  libqt4-sql-mysql libqt4-sql-odbc libqt4-sql-psql libqt4-sql-sqlite zeitgeist
  zeitgeist-core brasero notify-osd-icons pulseaudio-module-x11 rtkit
  gir1.2-gudev-1.0 laptop-detect python-pam python-serial
  gir1.2-launchpad-integration-3.0 sessioninstaller acpi-support
  activity-log-manager-control-center aisleriot app-install-data-partner
  avahi-autoipd bluez-alsa bluez-cups bluez-gstreamer branding-ubuntu brltty
  cmap-adobe-japan2 cups-bsd deja-dup empathy example-content
  firefox-gnome-support fonts-kacst-one fonts-khmeros-core fonts-lao
  fonts-takao-pgothic fonts-thai-tlwg gcc ginn gnome-accessibility-themes
  gnome-bluetooth gnome-orca gnome-sudoku gnomine gwibber ibus-gtk3
  ibus-pinyin ibus-pinyin-db-android ibus-table kerneloops-daemon
  landscape-client-ui-install libgail-common libpam-gnome-keyring
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libreoffice-calc
  libreoffice-gnome libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer libwmf0.2-7-gtk
  linux-headers-generic-pae mahjongg nautilus-share network-manager-pptp
  network-manager-pptp-gnome onboard overlay-scrollbar pcmciautils
  plymouth-theme-ubuntu-logo policykit-desktop-privileges printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-min12xxw printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio-module-bluetooth pulseaudio-module-gconf
  python-aptdaemon.pkcompat qt-at-spi remmina rhythmbox
  rhythmbox-plugin-magnatune rhythmbox-ubuntuone shotwell sni-qt
  speech-dispatcher telepathy-idle thunderbird-gnome-support totem-mozilla
  ttf-indic-fonts-core ttf-punjabi-fonts ubuntuone-client-gnome
  ubuntuone-installer usb-creator-gtk vino whoopsie xcursor-themes
  ubuntu-sso-client-gtk ubuntu-sso-client-gui unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-video indicator-appmenu
  indicator-application indicator-datetime indicator-messages
  indicator-printers indicator-session
```

---

### Post by Elfy on 2012-04-06
Sorry - getting a bit confused here then.

I understand the not wanting people to be attempting to get a pae kernel when their h/ware doesn't support it - but no kernel at all ?

Probably should read the whole thing ... ignore me :)

Probably also why I can't understand the whole upgrade to ubuntu or kubuntu from xubuntu or lubuntu :p

---

### Post by NHclimber on 2012-04-06
Just finished getting Lubuntu onto Pentium-M laptop. Slick :)


```
peter@beowulf:~$ sudo apt-get install --dry-run ubuntu-desktop | grep pae
  linux-headers-3.2.0-22-generic-pae linux-headers-generic-pae linux-libc-dev
  linux-headers-3.2.0-22-generic-pae linux-headers-generic-pae linux-libc-dev
Inst linux-headers-3.2.0-22-generic-pae (3.2.0-22.35 Ubuntu:12.04/precise [i386])
Inst linux-headers-generic-pae (3.2.0.22.24 Ubuntu:12.04/precise [i386])
Conf linux-headers-3.2.0-22-generic-pae (3.2.0-22.35 Ubuntu:12.04/precise [i386])
Conf linux-headers-generic-pae (3.2.0.22.24 Ubuntu:12.04/precise [i386])

```

That would be bad :(
Did you file a bug for that?

---

### Post by kansasnoob on 2012-04-06
> **forestpiskie said:**
> Sorry - getting a bit confused here then.

I understand the not wanting people to be attempting to get a pae kernel when their h/ware doesn't support it - but no kernel at all ?

Probably should read the whole thing ... ignore me :)

Probably also why I can't understand the whole upgrade to ubuntu or kubuntu from xubuntu or lubuntu :p

What we're doing is basically an extension of what Aysiu always does in the "playing around" section here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Of course Aysiu hasn't done one for Precise yet, we just need to be certain that any non-pae install will remain non-pae regardless of DE conversion.

I found something here by Jorge Castro that may be a viable answer:

[http://askubuntu.com/questions/24609/blacklisting-packages-from-installing](http://askubuntu.com/questions/24609/blacklisting-packages-from-installing)

I have a doctors appointment shortly but I'll get back to this.

---

### Post by kansasnoob on 2012-04-06
Another thought, just a thought, we may also be able to get the devs to change the meta-package so the pae kernel shifts to "suggests" instead of "recommends".

I need to reinstall an Ubuntu DE using the non-pae mini.iso as a base and see what mechanism is used to keep the PAE kernel from installing.

---

### Post by sudodus on 2012-04-06
> **jerrylamos said:**
> 
Is there any way to test the code that CD Live uses to determine non-pae capability?  I think I've seen posts somewhere on this forum from someone with a T41 who couldn't boot CD Live.

I've been happily running Lubuntu Beta 2.  I could try an ubuntu Unity-2D if it were of any use to anyone.

Jerry

I've posted about that. Let me know (maybe via an ubuntu forum message) when and where you have an iso file to test in my T41 without pae :-)

---

### Post by kansasnoob on 2012-04-06
> **sudodus said:**
> I've posted about that. Let me know (maybe via an ubuntu forum message) when and where you have an iso file to test in my T41 without pae :-)

Currently only the Lubuntu and Xubuntu images are non-pae, although there is a non-official Beta 1 Ubuntu image available here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)

What DE do you want?

Would you be willing to do some testing?

By testing I mean trying unproven methods and having to reinstall several times ;)

I'm working on this as fast as I can.

---

### Post by nm_geo on 2012-04-06
> **kansasnoob said:**
> Currently only the Lubuntu and Xubuntu images are non-pae, although there is a non-official Beta 1 Ubuntu image available here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)

What DE do you want?

Would you be willing to do some testing?

By testing I mean trying unproven methods and having to reinstall several times ;)

I'm working on this as fast as I can.
Yeah and he is serious about that too :lolflag:

Hope you are doing well kansasnoob and all ready for the next respins .. I believe testing is in kernel freeze right now. It will not be long and we will get busy for a few days.

---

### Post by sudodus on 2012-04-06
> **kansasnoob said:**
> Currently only the Lubuntu and Xubuntu images are non-pae, although there is a non-official Beta 1 Ubuntu image available here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/44)
What DE do you want?
Would you be willing to do some testing?
By testing I mean trying unproven methods and having to reinstall several times
I'm working on this as fast as I can.
I think that I'll want Lubuntu on the T41 before EOL of Lucid. Maybe I can test other flavours too. I should be able to deliver results at least within a week.

- Are the [LX]ubuntu daily build pae or non-pae now? Or are the non-pae versions somewhere else, or will be somewhere else?

- What should be tested? The first and obvious test is to try to run live from CD and USB. And I understand that some installing will also be needed.

- What do you mean by unproven methods: That whatever is on the hard drive might be wiped, so I should backup my systems (I dual boot now with Win XP and 'vanilla' Lucid.) ? Or something more?

I'll have time now, but I will not be able to do as much after April 14. Is it still worthwhile?

---

### Post by nm_geo on 2012-04-06
> **sudodus said:**
> I think that I'll want Lubuntu on the T41 before EOL of Lucid. Maybe I can test other flavours too. I should be able to deliver results at least within a week.

- Are the [LX]ubuntu daily build pae or non-pae now? Or are the non-pae versions somewhere else, or will be somewhere else?

- What should be tested? The first and obvious test is to try to run live from CD and USB. And I understand that some installing will also be needed.

- What do you mean by unproven methods: That whatever is on the hard drive might be wiped, so I should backup my systems (I dual boot now with Win XP and 'vanilla' Lucid.) ? Or something more?

I'll have time now, but I will not be able to do as much after April 14. Is it still worthwhile?
  The LX(ubuntu) precise i386 daily build are non-pae for sure.

Run the live CD that is one of the tests on the qa-tracker.  [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)
Then install - either along side or manual. Those are both tests too. Then install full disk if you can is another test.  

I would recommend that you back-up your system yes before you do any of the installs. I have 3 HDs for my testing laptop original XP, Lucid two versions of Lubuntu Precise, and a test ing HD for complete HD install regular and encrypted. Then my backup HD of my original.

The unproven methods are like picking a mini-iso non-pae and starting there and build you system like you want it.

kansasnoob and i have been testing Lubuntu since Alpha 1 and they have got better on each install. He really just got everyone (Lubuntu) on board with the non-pae kernel as default recently.

PS.  Any of the tests you can get done on the daily builds will help kansasnoob as we test right before the final spins.  He will be testing the i386 build right up to the final release day if things go as predicted.

---

### Post by sudodus on 2012-04-06
> **nm_geo said:**
> the lx(ubuntu) precise i386 daily build are non-pae for sure.

Run the live cd that is one of the tests on the qa-tracker.  [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)
then install - either along side or manual. Those are both tests too. Then install full disk if you can is another test.  

I would recommend that you back-up your system yes before you do any of the installs. I have 3 hds for my testing laptop original xp, lucid two versions of lubuntu precise, and a test ing hd for complete hd install regular and encrypted. Then my backup hd of my original.

The unproven methods are like picking a mini-iso non-pae and starting there and build you system like you want it.

Kansasnoob and i have been testing lubuntu since alpha 1 and they have got better on each install. He really just got everyone (lubuntu) on board with the non-pae kernel as default recently.

Ps.  Any of the tests you can get done on the daily builds will help kansasnoob as we test right before the final spins.  He will be testing the i386 build right up to the final release day if things go as predicted.
ok :-)

---

### Post by jerrylamos on 2012-04-06
> Any of the tests you can get done on the daily builds will help kansasnoob as we test right before the final spins. He will be testing the i386 build right up to the final release day if things go as predicted.
Maybe this is a bit off topic or not?  I have a Lubuntu Alpha updated to 3.2.0-21 running on a circa 2005 Thinkpad R31, Celeron, has pae flag, 1 GHz, 512 MB, intel integrated graphics.

Lubuntu is definitely preferable it's a bit slow for Unity-2D.

So far unsuccessful at installing Lubuntu Beta 2.  Today's 20120406 hangs at detecting keyboard while copying files goes right on.  Any way to tell if memory is all used up?  It doesn't have a webcam which I saw as a problem in a previous bug.  I did enter launchpad bug #975562

Jerry

---

### Post by nm_geo on 2012-04-06
> **jerrylamos said:**
> Maybe this is a bit off topic or not?  I have a Lubuntu Alpha updated to 3.2.0-21 running on a circa 2005 Thinkpad R31, Celeron, has pae flag, 1 GHz, 512 MB, intel integrated graphics.

Lubuntu is definitely preferable it's a bit slow for Unity-2D.

So far unsuccessful at installing Lubuntu Beta 2.  Today's 20120406 hangs at detecting keyboard while copying files goes right on.  Any way to tell if memory is all used up?  It doesn't have a webcam which I saw as a problem in a previous bug.  I did enter launchpad bug #975562

Jerry

I just downloaded the amd64 current daily put it on a flash drive with unebootin for another reason anyway I am going to do some install 
testing later today and will post back how it all goes.  Maybe i will zsync the i386 and test them too.. time time time my worst enemey.

---

### Post by sudodus on 2012-04-06
Now I can boot my IBM T41 with the daily build of Lubuntu Precise :KS

One attached file shows the screen during the live session (unetbootin-USB and CD), which were my first and only non-pae tests so far.

I also tested it on an HP xw8400, and according to htop it recognized the four processors, so this kernel has SMP capability and also seems to recognize more than 2 GB of RAM. Are these observations correct? See the other attached file

---

### Post by sudodus on 2012-04-07
... but I found and reported a bug in mplayer. I cannot play mp4, mp3, wav, MTS (probably nothing). Maybe because it is not recompiled to co-operate with the non-pae cpu of my IBM T41. *Edit: I tested it also in a Dell Dimension 4600 with Pentium 4 2.8 GHz with pae, and it was the same problem, so the mplayer bug is not related to non-pae. When auto-reporting this bug, I saw a report that the bug should be related to sse3. But I don't think so, because an AMD Athlon cpu without sse3 can play video with mplayer (booted from our non-pae CD drive).*
--
mplayer output:
--
MPlayer interrupted by signal 4 in module: read_subtitles_file
- MPlayer crashed by an 'Illegal Instruction'.
  It usually happens when you run it on a CPU different than the one it was
  compiled/optimized for.
  Verify this!
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by kansasnoob on 2012-04-07
I think we're OK now, at least on the main and US servers, because even if you find the pae versions of 'linux-headers' being installed the rest of the kernel will not be.

For those who are adventurous (and don't mind breakage if things go amiss) please install a daily build of Lubuntu or Xubuntu and then install 'ubuntu-desktop' with no modifications to recommendations or depends.

Once you're done I think you'll not find a pae kernel boot option in the grub menu ............... I hope.

I've tested Lubuntu i386 -> Ubuntu once and all is well .......... still no pae kernel in the boot menu, and "sudo update-grub" verifies this.

Writing the rest of the conversion from either Lubuntu or Xubuntu to Ubuntu should be fairly simple. I'll worry about Kubuntu later - Aysiu may even beat me ;)

---

### Post by kansasnoob on 2012-04-07
> **sudodus said:**
> I think that I'll want Lubuntu on the T41 before EOL of Lucid. Maybe I can test other flavours too. I should be able to deliver results at least within a week.

- Are the [LX]ubuntu daily build pae or non-pae now? Or are the non-pae versions somewhere else, or will be somewhere else?

- What should be tested? The first and obvious test is to try to run live from CD and USB. And I understand that some installing will also be needed.

- What do you mean by unproven methods: That whatever is on the hard drive might be wiped, so I should backup my systems (I dual boot now with Win XP and 'vanilla' Lucid.) ? Or something more?

I'll have time now, but I will not be able to do as much after April 14. Is it still worthwhile?

First of all there was no need whatsoever for two PM's. If I stopped what I was doing every time I got a PM I'd never have time to shave or shower!

Just test what you're comfortable with. One thing I'd point out though is that Lubuntu chose not to be LTS for the 12.04 life-cycle, and 12.04 is the end of the road for the non-pae kernel.

---

### Post by jerrylamos on 2012-04-07
> **kansasnoob said:**
>  ...One thing I'd point out though is that Lubuntu chose not to be LTS for the 12.04 life-cycle, and 12.04 is the end of the road for the non-pae kernel.

My opinion, 12.04 is the end of the road for UBUNTU on a LOT of good fast usable pc's like this one.

Looking at Distrowatch, there's lots of fish out there in the ocean.

Jerry

---

### Post by kansasnoob on 2012-04-08
> **jerrylamos said:**
> My opinion, 12.04 is the end of the road for UBUNTU on a LOT of good fast usable pc's like this one.

Looking at Distrowatch, there's lots of fish out there in the ocean.

Jerry

But, other than Lubuntu, 12.04 is a 5 year LTS. I think 5 years is a reasonable period of support for 6 and 7 year old laptops.

---

### Post by sudodus on 2012-04-08
> **kansasnoob said:**
> First of all there was no need whatsoever for two PM's. If I stopped what I was doing every time I got a PM I'd never have time to shave or shower!

Just test what you're comfortable with. One thing I'd point out though is that Lubuntu chose not to be LTS for the 12.04 life-cycle, and 12.04 is the end of the road for the non-pae kernel.
1. Sorry for double pm-ing :oops:

The reason was that the feedback from my interface indicated that the PMs were not sent (first I assumed they were lost in cyperspace, then I thought that you had switched off reception of PMs from strangers and posted in this thread). I'll stick to posting in the thread in the future.

2. Lifetime

What exactly does it mean, that Lubuntu does not have LTS status? What is the difference in support for the following cases?

- install from Lubuntu iso file

- install from Xubuntu iso file and into that installing lubuntu-desktop

- install from Xubuntu iso file and into that installing LXDE

In other words: is there a way to get 'near-lubuntu functionality' for five years?

---

### Post by kansasnoob on 2012-04-08
> **sudodus said:**
> 1. Sorry for double pm-ing :oops:

The reason was that the feedback from my interface indicated that the PMs were not sent (first I assumed they were lost in cyperspace, then I thought that you had switched off reception of PMs from strangers and posted in this thread). I'll stick to posting in the thread in the future.

2. Lifetime

What exactly does it mean, that Lubuntu does not have LTS status? What is the difference in support for the following cases?

- install from Lubuntu iso file

- install from Xubuntu iso file and into that installing lubuntu-desktop

- install from Xubuntu iso file and into that installing LXDE

In other words: is there a way to get 'near-lubuntu functionality' for five years?

I've wondered about that myself. Other than being "oldish" what are the security implications of installing any DE in an existing LTS release?

I can't answer that :(

Right now I'm concentrating on how to totally convert an Lubuntu installation to non-pae Ubuntu and the kernel thing ended up being the easy part. I'm running into what seem to be endless plymouth and lightdm problems :-k

I'm stumped ATM ............ time to sleep on it.

---

### Post by sudodus on 2012-04-08
> **sudodus said:**
> ... but I found and reported a bug in mplayer. I cannot play mp4, mp3, wav, MTS (probably nothing). Maybe because it is not recompiled to co-operate with the non-pae cpu of my IBM T41. *Edit: I tested it also in a Dell Dimension 4600 with Pentium 4 2.8 GHz with pae, and it was the same problem, so the mplayer bug is not related to non-pae. When auto-reporting this bug, I saw a report that the bug should be related to sse3. But I don't think so, because an AMD Athlon cpu without sse3 can play video with mplayer (booted from our non-pae CD drive).*
--
mplayer output:
--
MPlayer interrupted by signal 4 in module: read_subtitles_file
- MPlayer crashed by an 'Illegal Instruction'.
  It usually happens when you run it on a CPU different than the one it was
  compiled/optimized for.
  Verify this!
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
I could not find my bug report after logging in again to launchpad, so I tried again, and this time I managed: Bug #976465.

Please test if ***mplayer in Lubuntu daily build precise-desktop-i386.iso*** works on your computer and add comments about it here and/or at Launchpad! In particular, can you run mplayer with a 32-bit cpu? And, mplayer prints a request to compile it, but I don't know how to do that. If *you* can compile mplayer, maybe we can get better knowledge about the bug.

---

### Post by jerrylamos on 2012-04-08
> **kansasnoob said:**
> But, other than Lubuntu, 12.04 is a 5 year LTS. I think 5 years is a reasonable period of support for 6 and 7 year old laptops.

12.04 generic-pae is reported as an LTS.

12-04 non-pae on lubuntu is not to be LTS, hence limited support life.

12-04 non-pae on Xubuntu - anyone have any info LTS or not?  

I run this wide (?!) 1366x768 notebook on a big table in the back room.  Special sale, bought sight unseen, oof. All kinds of cpu info flags, 64 bit (any 128 bits yet?).  Rather huge for the dining room table.

On the dining room table I run a nice responsive easy to read 14" Thinkpad T40 non-pae or else a netbook (squint).  If the T40 goes bonkers or it falls off the table there are used Thinkpad T61's 2 GHz core 2 duo from $150 on the used market, again, non-pae I gather from the launchpad bugs.  My son-in-law has one, maybe I can get him to give it to me.

So anyway, any idea will there be non-pae ubuntu's after 12.04 lubuntu or not?

Thanks,

Jerry

---

### Post by kansasnoob on 2012-04-08
> So anyway, any idea will there be non-pae ubuntu's after 12.04 lubuntu or not?

Nope, as I understand it 12.04 is the end of the road for the non-pae kernel in Ubuntu.

> The Ubuntu Technical Board weighed the pros and cons of non-PAE support and came to a decision. The board has decided they will support the non-PAE kernel option until the Ubuntu 12.10 release, so there will still be support in Ubuntu 12.04 LTS. The default i386 kernel in Ubuntu 12.04 LTS will become the PAE-enabled kernel, but the non-PAE flavor will be available.

Below are the details in full from the non-PAE discussion.

    Non-PAE kernel disposition
    * Kernel team would like to drop non-PAE kernel soon
    * TB members generally feel that (1) dropping the current default kernel is too much of a step, and (2) there is still a significant number of users which have non-PAE systems, based on Launchpad bug report data and an ubuntu-devel@ strawpoll
    * Maintaining the extra flavour is not much extra work, and not comparable to e. g. the -ti-omap4 kernel which is an entirely separate source tree
    * We need a way to prevent upgrades for non-PAE systems. Some options were mentioned:
    * Add update-manager check to not offer the upgrade if PAE is not available
    * Add libc6/linux preinst to abort the upgrade early if PAE is not available; that's not the best failure mode, but will prevent a safety net for users of `apt-get dist-upgrade`
    * '''Agreements''':
    * Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout (Colin)
    * **[COLOR="Red"]Drop non-PAE flavour in 12.10; this will give non-PAE systems another 5 years of life time, which is considered enough[/COLOR]**
    * Further discuss upgrade strategy/checks

[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM)

---

### Post by Yellow Pasque on 2012-04-08
> **jerrylamos said:**
> So anyway, any idea will there be non-pae ubuntu's after 12.04 lubuntu or not?

Probably not. They were reluctant to include non-pae in 12.04.

BTW, Jerry, please respond to your bug! [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/968469](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/968469)

---

### Post by kansasnoob on 2012-04-08
I figured out the lightdm problem. I'd removed 'lightdm-gtk-greeter' without changing to 'unity-greeter' in "/etc/lightdm/lightdm.conf". Pretty dense huh :redface:

Similar situation with 'plymouth-theme-lubuntu-logo' and 'plymouth-theme-lubuntu-text', but I just needed to run "sudo apt-get install --reinstall plymouth" to remedy that.

Anyway I'm getting closer. I'll drop removing those packages just in an overabundance of caution. I should have a preliminary **how-to convert Lubuntu to Ubuntu non-pae** very soon, but I'm going to take in some sun today ;)

---

### Post by cariboo on 2012-04-08
> **jerrylamos said:**
> 12.04 generic-pae is reported as an LTS.

12-04 non-pae on lubuntu is not to be LTS, hence limited support life.

12-04 non-pae on Xubuntu - anyone have any info LTS or not?  

I run this wide (?!) 1366x768 notebook on a big table in the back room.  Special sale, bought sight unseen, oof. All kinds of cpu info flags, 64 bit (any 128 bits yet?).  Rather huge for the dining room table.

On the dining room table I run a nice responsive easy to read 14" Thinkpad T40 non-pae or else a netbook (squint).  If the T40 goes bonkers or it falls off the table there are used Thinkpad T61's 2 GHz core 2 duo from $150 on the used market, again, non-pae I gather from the launchpad bugs.  My son-in-law has one, maybe I can get him to give it to me.

So anyway, any idea will there be non-pae ubuntu's after 12.04 lubuntu or not?

Thanks,

Jerry

I'd say no, but there is always the option of rolling your own kernel with the non-pae option.

---

### Post by keithpeter on 2012-04-08
> **jerrylamos said:**
> If the T40 goes bonkers or it falls off the table there are used Thinkpad T61's 2 GHz core 2 duo from $150 on the used market, again, non-pae I gather from the launchpad bugs.  

Hello jerrylamos

The T60 (dual core) I did up for my sister had PAE.

The old T42 (single core Centrino M) that developed an LCD problem definitely didn't. That went to another forum user as a headless server.

[http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T61-physical-address-extension/td-p/480509](http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T61-physical-address-extension/td-p/480509)

That link tends to imply that T61's have the PAE flag available in the CPU. 

My quick and dirty way of assessing PAE or non-PAE is to try a Fedora 15+ or Scientific Linux 6.x live CD. The RHEL world has already dropped non-pae support. If you get a (polite) one line error message when booting from those images if your target machine definitely does not support PAE.

Kudos to Canonical for supporting the non-PAE Centrino laptops in this cycle.

---

### Post by jerrylamos on 2012-04-08
> **Temüjin said:**
> Probably not. They were reluctant to include non-pae in 12.04.

BTW, Jerry, please respond to your bug! [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/968469](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/968469)

That bug was found on my Compaq Presario.  Video sound working O.K. will try checkbox-qt when I get back on the PC.  I'm on the Thinkpad T40 at the moment.

On topic, on the Thinkpad T40 just updated a lubuntu to -22 and did apt-get install ubuntu-desktop which did.  Still generic no pae as expected.  I can log out and choose desktops ubuntu, ubuntu-2D, lubuntu, GNOME/openbox, Openbox, Lubuntu Netbook.  

A bit piggy,
```

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda9        6039488 3364060   2368640  59% /
```

lubuntu Used was 2000000 before installing the ubuntu-desktop.  I've got 4 partitions running various ubuntu plus an archive on 40 GB.

Currently logged on with "ubuntu" note no Compiz in sight (Yay!) system monitor shows unity-2d-shell active.

I tried installing from 3.2.0-20 all sorts of complaints. dist-upgrade to 3.2.0-22 and then the ubuntu-desktop did install O.K.  I don't know what level lubuntu would have to be updated to for install of ubuntu-desktop LTS as time goes on.

Jerry

---

### Post by jerrylamos on 2012-04-09
More disk space than I want to use for Ubuntu desktop since Lubuntu desktop does everything I'm doing lately.  Doing a zsync to clean up partition and re-install lubuntu.

Jerry

---

### Post by kansasnoob on 2012-04-09
> **jerrylamos said:**
> More disk space than I want to use for Ubuntu desktop since Lubuntu desktop does everything I'm doing lately.  Doing a zsync to clean up partition and re-install lubuntu.

Jerry

No doubt adding an entire DE adds a lot of bloat, but I think I'm pretty close to having an actual conversion from Lubuntu to Ubuntu while retaining the non-pae kernel.

I'll try to remember at each step along the way to run a "df -H" to check disc usage. OTOH I hope to get a better answer regarding security implications installing various DE's to an existing Ubuntu LTS.

It's all a matter of time. Right now I'm focusing on two projects:

#1: Completing an Lubuntu -> Ubuntu guide as part of a very preliminary guide regarding the non-pae issue. A more comprehensive guide will have to wait until after the release of Precise.

#2: Completing a preliminary Precise classic w/o effects guide. Once again a more comprehensive guide will have to wait until after the final release of Precise.

I'll be doing good if I get both of those projects done ;)

---

### Post by kansasnoob on 2012-04-09
Mega-fail on my last Lubuntu -> Ubuntu non-pae trial run ](*,)

Back to the drawing board ;)

---

### Post by Kelvari on 2012-04-11
Just my 2 cents here, not that it matters much, but I think that the x86 kernel should remain non-PAE (at least for 12.04). By the time 14.04 comes out, though, I can definitely understand dropping support for it, at least in standard Ubuntu/Kubuntu. 

Xubuntu and Lubuntu would probably serve the masses better by allowing non-PAE support for a longer time, as they are designed to run on older hardware anyway. As such, I think that a 16.04 deadline would work better for them.

---

### Post by kansasnoob on 2012-04-11
> **Kelvari said:**
> Just my 2 cents here, not that it matters much, but I think that the x86 kernel should remain non-PAE (at least for 12.04). By the time 14.04 comes out, though, I can definitely understand dropping support for it, at least in standard Ubuntu/Kubuntu. 

Xubuntu and Lubuntu would probably serve the masses better by allowing non-PAE support for a longer time, as they are designed to run on older hardware anyway. As such, I think that a 16.04 deadline would work better for them.

This was my wish too:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50)

> I'm really sticking my neck out here, I subscribed Colin Watson which is totally rude and I hope he'll forgive me :^)

I was so clueless about the change to the pae enabled kernel that I had to ask a question at the forums. All of my hardware works great with "pae" and I wouldn't even have noticed except for the new suffix in grub. But that forum post became a bit of a lightning rod so I followed it up with two questions at Ubuntu answers. So even though I'm not directly effected I've now thrown myself into the fray, testing the non-pae mini.iso, upgrade options, etc.

So my question to Colin is; according to the minutes of the Ubuntu Technical Board meeting on Dec 12, 2011 you said, "Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout (Colin)".

Now obviously I want to know if we've yet seen enough "fallout"?

I think we must seriously consider that question based on the following facts:

#1: Both pae and non-pae kernel versions are going to be supported throughout the 5 year Precise life cycle anyway, and those who desire a PAE-enabled kernel can easily install it post-installation.

#2: The only official methods to install non-pae Precise are:

(a) Install Lucid (10.04.4), install all available updates, then upgrade to Precise. Do note however this is not likely to work for Lubuntu.

(b) Install Oneiric (11.10), install all available updates, then upgrade to Precise. This should work for all official derivatives.

(c) Use the non-pae mini.iso, aka; netboot image, and then install the desired DE.

#3: I have a 5000kbps+ wired connection and any of the three above options are time consuming. Depending on which DE I use a mini.iso install takes about 1 hour and 20 minutes to 1 hour and 45 minutes to complete.

Either of the install + update + dist-upgrade options are even more time consuming, Oneiric more so since Lucid just had a point-release (10.04.4).

#4: More important than just time required is the fact that most, if not all, of those reporting the inability to install Precise due to the lack of pae support are laptop users many of whom lack access to a wired connection which is almost a requirement for a netboot/mini.iso install, and certainly preferable for dist-upgrades.

#5: It's nearly impossible to determine how many users are effected at this point but based on PM's, bug reports, mailing lists, etc. I'd put it at no less than 2 dozen .......... and remember we're just in Beta 1.

#6: David Henningsson has already produced the first "hybrid" Ubuntu image, and Greg Faith has reported on the Lubuntu mailing list that he's managed to create an Lubuntu hybrid image. While I applaud their efforts, how much difficulty does this present for the devs when it comes to squashing unrelated bugs? I'd think we can be sure that others will create their own hybrid images for other DE's and such.

#7: I understand that the Precise default download will be 64 bit anyway, and most hardware capable of 4GB+ RAM will run a 64 bit system so why default to the PAE kernel on i386? Isn't this a bit like rubbing salt in a wound?

#8: We're running out of time to revert ........ maybe we've already done so. It would be incredibly awkward to introduce such a change at 12.04.1!

Summary:

I subscribed Colin for two reasons. He's both reasonable to work with and he knows what is and is NOT possible. My two greatest concerns are the difficulty installing a non-pae system with no available wired connection and the difficulty presented by introducing multiple hybrid images into the fray.

I certainly apologize again for rudely subscribing Colin, that's the price he has to pay for being reliable in the past ;^)

Thanks in advance.


Shortly following that both Xubuntu and Lubuntu were allowed to revert to a default non-pae kernel.

That's it ............ deal done! At this point in developmemt the devs will NOT make any more changes!!!!

We're mostly down to bug fixes now.

Lubuntu will be supported for 18 months.

Xubuntu will be supported for 3 years.

IMHO Ubuntu-2D or "classic w/o effects" will be a very good choice for non-pae users, and both will be possible.

I just need time to perfect the process :)

Being patient would be a really good thing.

---

### Post by kansasnoob on 2012-04-13
Just wanted to reassure everyone that I've not given up on this. I've been testing Lubuntu to Ubuntu conversions ad nauseam  and I've gotten past most of the hurdles but I now get a 'zenity' crash report so it's going to take a while to figure out the DE conversion thing.

Right now I'm going to focus on my Gnome Classic thing and ASAP I'll put up an appropriately named thread for non-pae options ............ including the need for patience ;)

---

### Post by Irihapeti on 2012-04-13
> **kansasnoob said:**
> Just wanted to reassure everyone that I've not given up on this. I've been testing Lubuntu to Ubuntu conversions ad nauseam  and I've gotten past most of the hurdles but I now get a 'zenity' crash report so it's going to take a while to figure out the DE conversion thing.

Right now I'm going to focus on my Gnome Classic thing and ASAP I'll put up an appropriately named thread for non-pae options ............ including the need for patience ;)

I say that even if you did nothing more, you would still absolutely deserve a medal for everything you've already done.

/me sneaks off feeling a little guilty for how little *I've* done...

---

### Post by cariboo on 2012-04-13
> **Irihapeti said:**
> I say that even if you did nothing more, you would still absolutely deserve a medal for everything you've already done.

/me sneaks off feeling a little guilty for how little *I've* done...

+1 to both statements. :P

---

### Post by kansasnoob on 2012-04-14
OK I think I'm ready to start, one thing I'm going to need right off the bat is a brief history of what's going on, and it needn't be something that can be replied to so it can be an archived Precise post ........ like this :)

I'm just going to start with some links in historical order and then I'll figure out how to translate it into an actual history of the process:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMzU](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMzU)

[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM)

Sadly the Beta 1 release notes said nothing about defaulting to pae:

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1)

Xubuntu did better in Beta 2:

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Xubuntu](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Xubuntu)

But Lubuntu said nothing:

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Lubuntu](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Lubuntu)

So I'll have to rely on Launchpad:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866](https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866)

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009](https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009)

I'll probably include a link to my complaining:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50)

I need to do some "rinse-n-repeat" testing on my Precise classic how-to tomorrow and then I'll try to cook this "pae vs non-pae - how we got here post".

Then I can do the actual intended thread ........ I hope ;)

---

### Post by kansasnoob on 2012-04-14
Could go something like this:

I think I'll just title it:

**Kernel requires pae, unable to boot - now what?** and mark it solved.

If you're reading this you probably tried to run a 12.04 live session or install 12.04 and were presented with this warning, "**This kernel requires the following features not present on the CPU: pae. Unable to boot - please use a kernel appropriate for you CPU**." 

So what's up and what are your options?

In November 2011 the kernel devs seemed to have [doomed the non-pae kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTAxMzU") but in December 2011 [things began to look up]("http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM"), however when Precise Beta 1 was released the only real options to install a non-pae kernel were to upgrade from either Lucid or Oneiric or to use the [netboot non-pae mini.iso]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/").

But after some [complaining on my part]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50") and requests from [Xubuntu]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009") and [Lubuntu]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866") the options have improved somewhat. Both the Xubuntu and Lubuntu 12.04 images now use the non-pae kernel by default. You should however consider that Lubuntu 12.04 is only supported for 18 months, and Xubuntu 12.04 is supported for 3 years, whereas Ubuntu 12.04 LTS itself is supported for 5 years.

The Ubuntu, Kubuntu, Edubuntu, and Mythbuntu i386 images all now use the PAE kernel by default but, as previously mentioned, upgrades from either 10.04 or 11.10 will remain non-pae. Please refer to [the release notes]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2") or your distros official documentation regarding the proper upgrade methods and options.

Note: Need to change that release note link when Precise final is released.

And it's also quite possible to install 'ubuntu-desktop' on top of an Xubuntu or Lubuntu installation and still remain non-pae. Shortly after the final release of Precise I do plan on collaborating with the author of [Psychocats]("http://www.psychocats.net/ubuntu/index") on a full conversion method from either Xubuntu or Lubuntu to Ubuntu.

Remember when making a decision here that 12.04 is the end of the road for the non-pae kernel in Ubuntu so I'd personally think a 5 year LTS would be a good choice, but that's totally up to you, and the aforementioned non-pae mini.iso is a reasonable choice if you have a fast wired internet connection. You can read more about that here:

I'll create a separate brief how-to for the netboot images to link to here.

Arrgh ............. brain needs to rest :(

---

### Post by jerrylamos on 2012-04-14
> **kansasnoob said:**
> But after some [complaining on my part]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50") and requests from [Xubuntu]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009") and [Lubuntu]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866") the options have improved. 


Hey, we appreciate your efforts!  Others too, anyone that can help.  Do note there are still Pentium M's on the marketplace.  Mine's running fine with lubuntu 12.04, a whole lot more visible than the little netbook (squint) I'm using here on the dining room table.

I'm still on the page with linux being trim, efficient, capable, fast.  This "pseudo smartphone pseudo ipad" is fat, inefficient, bogged down, and slow.  Now future ubuntu needs ever faster more $$ complex features more memory buy a new pc to upgrade ubuntu - sounds like Microsoft!  

And when you get down to it, I'm doing internet news, video, email, word processing, spreadsheet full screen so I only see the "fancy eye candy" when I'm doing updates, local network file transfer, and certainly when running system moniter to see the excess overhead ....

Cheer up, we're with you!

Jerry

---

### Post by ronacc on 2012-04-14
even though I don't have any boxes that require the non-pae kernel I appreciate your efforts to save Ubuntu for all those who do .

---

### Post by sudodus on 2012-04-14
Thanks again for your hard work *kansasnoob*. It makes a difference :KS

My small contribution is to test the daily build, so that it keeps working without pae. Except for some small bugs I have only one issue: the default media player, mplayer, does not work on my 32-bit computers (pae as well as non-pae). VLC works, but needs more horsepower. Are there others who have the same problem?

---

### Post by kansasnoob on 2012-04-14
I'm getting closer:

[http://ubuntuforums.org/showpost.php?p=11842853&postcount=67](http://ubuntuforums.org/showpost.php?p=11842853&postcount=67)

But one of the links I'd planned on using for a mini.iso install is now dead :(

So I need to do something slightly different than planned for using the mini.iso. I'm thinking something along these lines:

Using the [netboot mini.iso]("http://cdimage.ubuntu.com/netboot/") is considerably reliant on a fast wired internet connection. My ethernet speed is 5000kbps+ and the average total installation time is 1 hour and 45 minutes, but on a positive note you're getting the latest packages so you'll have little or no updates to install after the installation is complete.

The images are quite small, typically under 30MB, and they can either be burned to disc or you can create a [bootable USB using Unetbootin]("http://www.psychocats.net/ubuntu/usb"). If you're familiar with the Debian installer or the Ubuntu alternate installer this will all seem quite straight forward to you. If not there is a [good guide here]("http://www.psychocats.net/ubuntu/minimal") for using the mini.iso to perform a Command-Line Install.

That should give you a good idea of what the installation screens look like but **for our purpose most users will be fine just choosing "Install"** from the boot options and then '[tasksel]("https://help.ubuntu.com/community/Tasksel")' will offer a list of options at the end of the installation (It's a long list and you must use the keyboard arrow keys to scroll through the entire list - I've highlighted those of interest):

```
u server	Basic Ubuntu server
u openssh-server	OpenSSH server
u dns-server	DNS server
u lamp-server	LAMP server
u mail-server	Mail server
u openstack	Openstack
u postgresql-server	PostgreSQL database
i print-server	Print server
u samba-server	Samba file server
u tomcat-server	Tomcat Java server
u cloud-image	Ubuntu Cloud Image (instance)
u virt-host	Virtual Machine host
u ubuntustudio-graphics	2D/3D creation and editing suite
u ubuntustudio-recording	Audio recording and editing suite
u edubuntu-desktop-kde	Edubuntu KDE desktop (unsupported)
u **edubuntu-desktop-gnome	Edubuntu desktop**
u **kubuntu-desktop	Kubuntu desktop**
u kubuntu-full	Kubuntu full
u kubuntu-mobile	Kubuntu mobile
u ubuntustudio-audio-plugins	LADSPA/LV2/DSSI audio plugins
u ubuntustudio-font-meta	Large selection of font packages
u lubuntu-core	Lubuntu minimal installation
u **mythbuntu-desktop	Mythbuntu additional roles**
u mythbuntu-frontend	Mythbuntu frontend
u mythbuntu-backend-master	Mythbuntu master backend
u mythbuntu-backend-slave	Mythbuntu slave backend
u ubuntustudio-generation	Tone generation and editing suite
u **lubuntu-desktop	Ubuntu LXDE Desktop**
i **ubuntu-desktop	Ubuntu desktop**
u ubuntu-usb	Ubuntu desktop USB
u ubuntustudio-video	Video creation and editing suite
u **xubuntu-desktop	Xubuntu desktop**
u edubuntu-dvd-live	Edubuntu live DVD
u kubuntu-mobile-live	Kubuntu Mobile Remix live CD
u kubuntu-live	Kubuntu live CD
u kubuntu-dvd-live	Kubuntu live DVD
u lubuntu-live	Lubuntu live CD
u ubuntustudio-dvd-live	Ubuntu Studio live DVD
u ubuntu-live	Ubuntu live CD
u ubuntu-dvd-live	Ubuntu live DVD
u ubuntu-usb-live	Ubuntu live USB
u xubuntu-live	Xubuntu live CD
u manual	Manual package selection

```

I've personally only tested 'ubuntu-desktop', 'lubuntu-desktop', and 'xubuntu desktop' so I can't comment on the rest but my experience has been generally good. I would however point out the following things to consider during installation:

* You'll be asked if you want the installer to detect your keyboard layout or proceed with the default (I always just select No when asked and the US keyboard defaults seem fine for me).

* Specify the hostname for your system - this may confuse new users, but I typically use my first name accompanied by some computer ID or location, eg; john-AMD-desktop, or john-INTEL-laptop. This will be how your computer is recognized on your network.

* HTTP proxy - I'm totally clueless here as I've never dealt with such

* Encrypt home directory? I've never done so, but [this]("http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t") may be helpful to others.

* Partitioning gets rather complex so I'll not get into detail here, but one nice thing is that the "Use largest continuous free space" option still exists.

* After quite some time you'll be asked about how to handle updates - Select 'No Automatic Updates' (trust me).

As with any installation if you have questions please ask them in [this forum subsection]("http://ubuntuforums.org/forumdisplay.php?f=333").

---

### Post by jerrylamos on 2012-04-15
> ********** I'm saving even when things are quite incomplete because the weather is rough, the lights keep flickering, and my UPS is only good for about 5 minutes ************
Kansas is all over the news this morning - any problems near you?

Jerry

---

### Post by kansasnoob on 2012-04-15
> **jerrylamos said:**
> Kansas is all over the news this morning - any problems near you?

Jerry

I'm fine, just some fairly minor property damage but I'm insured :)

Being somewhat rural the biggest challenge is power outages, and since I have my own well that also means no water. An indoor toilet w/o running water gets nasty in a hurry :lolflag:

---

### Post by jerrylamos on 2012-04-15
> **kansasnoob said:**
> Being somewhat rural the biggest challenge is power outages, and since I have my own well that also means no water. An indoor toilet w/o running water gets nasty in a hurry :lolflag:

Wooded here, southern NH, so ice and wind breaks branches which bring power lines down frequently.  For hours, even days like last Halloween.  I fill 5 gallon containers with downspout rainwater and save in the basement for flushing.

Jerry

---

