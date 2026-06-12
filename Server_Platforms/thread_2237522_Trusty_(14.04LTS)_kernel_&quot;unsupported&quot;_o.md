---
title: "Trusty (14.04LTS) kernel &quot;unsupported&quot; on Precise (12.04LTS)?"
date: 2014-08-02
forum: Server Platforms
---

### Post by mdlueck on 2014-08-02
Greetings,

I am confused by the output of running:

```
$ ubuntu-support-status --show-unsupported
Support status summary of 'myhostnamehere':

You have 1 packages (0.2%) supported until October 2013 (18m)
You have 416 packages (95.0%) supported until April 2017 (5y)

You have 1 packages (0.2%) that can not/no-longer be downloaded
You have 20 packages (4.6%) that are unsupported

Your Hardware Enablement Stack (HWE) is supported until April 2017.

No longer downloadable:
oorexx 

Unsupported: 
apticron daemontools daemontools-run debsums djbdns dnscache-run 
libdevel-trace-perl libfile-fnmatch-perl libmcrypt4 
linux-generic-lts-trusty linux-headers-3.13.0-32 
linux-headers-3.13.0-32-generic linux-headers-generic-lts-trusty 
linux-image-3.13.0-32-generic linux-image-generic-lts-trusty 
php5-mcrypt php5-suhosin phpmyadmin tripwire ucspi-tcp
```

Now, ooRexx I can understand as that is a manual download from SourceForge and install. I specifically monitor the status of my ooRexx interpreter.

But the Trusty kernel, which I specifically installed the "Hardware Enablement Stack (HWE)" for, IPL, then saw I am supported through April 2017... those packages are grouped into "Unsupported"??? Please explain what I am seeing.

The rest of the "Unsupported" came from the Precise (12.04LTS) repository. So why would those be unsupported already as those packages are from a "supported" LTS release?

I am thankful,

---

### Post by ajgreeny on 2014-08-02
If you think that is a worry, you should see my unsupported list!!!
```
~$ ubuntu-support-status --show-unsupported
Support status summary of 'Xubuntu':

You have 83 packages (3.9%) supported until October 2013 (18m)
You have 7 packages (0.3%) supported until January 2016 (18m)
You have 1441 packages (67.2%) supported until April 2017 (5y)

You have 10 packages (0.5%) that can not/no longer be downloaded
You have 603 packages (28.1%) that are unsupported

Your Hardware Enablement Stack (HWE) is supported until April 2017.

No longer downloadable:
devede faenza-icon-theme faience-icon-theme faience-theme giplayer.py 
libcmis-0.3-3 mencoder mplayer-gui skype:i386 w64codecs 

Unsupported: 
abcde abiword abiword-common abiword-plugin-grammar 
abiword-plugin-mathview acpi alacarte alarm-clock alltray antiword 
asunder atomicparsley audacious audacious-plugins 
audacious-plugins-data audacity audacity-data audio-recorder avidemux 
avidemux-common avidemux-plugins-common avidemux-plugins-gtk 
brltty-x11 bum cabextract calibre calibre-bin catfish cd-discid 
checkinstall chmsee chromium-browser chromium-browser-l10n 
chromium-codecs-ffmpeg-extra compton conky-all dconf-tools digikam 
digikam-data dvdauthor dvgrab easytag ejecter elementary-icon-theme 
enblend enfuse exo-utils extlinux fbreader filezilla filezilla-common 
flashplugin-installer font-manager fonts-droid fonts-opensymbol 
foobillard freepats frei0r-plugins gcolor2 gconf-defaults-service 
gconf-editor gdebi gdebi-core gdisk gecko-mediaplayer get-iplayer 
gigolo gimp gimp-data gimp-help-common gimp-help-en gmail-notify gmtp 
gmusicbrowser gnome-brave-icon-theme gnome-colors-common 
gnome-desktop-data gnome-icon-theme-extras gnome-icon-theme-nuovo 
gnome-mplayer gnome-schedule gnome-system-tools gnome-time-admin 
gnumeric gnumeric-common gnumeric-doc goldendict goldendict-wordnet 
gpicview grsync gstreamer0.10-ffmpeg 
gstreamer0.10-fluendo-plugins-mp3-partner gstreamer0.10-gnomevfs 
gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly gstreamer0.10-vaapi gthumb gthumb-data 
gtk2-engines-pixbuf gtkhash gtkhash-common gtkperf gufw guvcview hal 
hal-info hardinfo hddtemp htop hugin hugin-data hugin-tools 
human-icon-theme icedtea-7-plugin id3v2 indicator-application-gtk2 
indicator-sound-gtk2 jpeginfo kdenlive kdenlive-data kipi-plugins 
kipi-plugins-common kmymoney kmymoney-common lame leafpad 
liba52-0.7.4 libaacs0 libabiword-2.8 libabiword-2.9 libaften0 
libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a 
libalkimia4 libamd2.2.0 libaqbanking-data libaqbanking33 libass4 
libaudclient2 libaudcore1 libaudio-scrobbler-perl libavcodec-extra-53 
libavdevice-extra-53 libavfilter-extra-2 libavformat-extra-53 
libavidemux0 libavutil-extra-51 libbabl-0.1-0 libbinio1ldbl 
libbluray1 libboost-date-time1.46.1 libboost-date-time1.54.0 
libboost-filesystem1.46.1 libboost-signals1.46.1 
libboost-system1.46.1 libboost-thread1.46.1 libbs2b0 
libcairo-gobject2 libcairo2 libcdaudio1 libcddb2 libcdr-0.0-0 
libcelt0-0 libchm1 libchromaprint-tools libchromaprint0 
libclucene-contribs1 libclucene-core1 libcmis-0.4-4 libcolamd2.7.1 
libcrystalhd3 libdca0 libdigest-crc-perl libdirac-encoder0 
libdirectfb-1.2-9 libdvbpsi7 libdvdcss2 libdvdnav4 libdvdread4 
libebml3 libegl1-mesa-drivers-lts-trusty libegl1-mesa-lts-trusty 
libenet1a libexo-1-0 libexo-common libexo-helpers libexttextcat-2.0-0 
libexttextcat-data libfaac0 libfaad2 libfluidsynth1 libgarcon-1-0 
libgarcon-common libgavl1 libgbm1-lts-trusty libgdome2-0 
libgdome2-cpp-smart0c2a libgegl-0.2-0 libgimp2.0 
libgl1-mesa-dri-lts-trusty libgl1-mesa-glx-lts-trusty libglamor-ltst0 
libglapi-mesa-lts-trusty libgme0 libgmlib0 libgmtk0 libgmtk0-data 
libgoffice-0.8-8 libgoffice-0.8-8-common libgraphite2-3 
libgstreamer-perl libgstreamer-plugins-bad0.10-0 
libgstreamer-vaapi0.10 libgtk2-notify-perl libgtk2-trayicon-perl 
libgtkmathview0c2a libguess1 libgwengui-qt4-0 libgwenhywfar-data 
libgwenhywfar60 libhal-storage1 libhal1 libicu48 
libimage-exiftool-perl libiso9660-8 libkate1 libkeybinder0 
libkface-data libkface1 libkgeomap-data libkgeomap1 libkvkontakte1 
liblangtag-common liblangtag1 liblcms2-2 liblensfun-data liblensfun0 
libleptonica liblinebreak2 liblink-grammar4 libllvm3.4 libmatroska5 
libmediainfo0 libmimic0 libmjpegtools-1.9 libmlt++3 libmlt-data 
libmlt4 libmms0 libmodplug1 libmowgli2 libmp3-info-perl 
libmp3-tag-perl libmp3lame0 libmp3splt-mp3 libmp3splt-ogg libmp3splt0 
libmpeg2-4 libmpg123-0 libmspub-0.0-0 libnet-dbus-perl 
libnet-smtp-ssl-perl libnet-smtp-tls-butmaintained-perl libofa0 
libofx4 liboil0.3 liboobs-1-5 libopencore-amrnb0 libopencore-amrwb0 
libopencv-calib3d2.3 libopencv-core2.3 libopencv-features2d2.3 
libopencv-flann2.3 libopencv-highgui2.3 libopencv-imgproc2.3 
libopencv-legacy2.3 libopencv-objdetect2.3 libopencv-video2.3 
libopenjpeg2 libopenraw1 libopenvg1-mesa-lts-trusty liborcus-0.6-0 
libots0 libpano13-2 libpano13-bin libpodofo0.9.0 libportsmf0 
libpostproc-extra-52 libquicktime2 libraptor2-0 librasqal3 librdf0 
libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-base 
libreoffice-base-core libreoffice-base-drivers libreoffice-calc 
libreoffice-common libreoffice-core libreoffice-draw libreoffice-gtk 
libreoffice-gtk3 libreoffice-help-en-gb libreoffice-impress 
libreoffice-java-common libreoffice-l10n-en-gb libreoffice-math 
libreoffice-pdfimport libreoffice-report-builder-bin 
libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb 
libreoffice-style-human libreoffice-style-tango libreoffice-writer 
libresid-builder0c2a librubberband2 libsdl-image1.2 libsidplay1 
libsidplay2 libsidplayfp libslv2-9 libsoundtouch0 libsox-fmt-alsa 
libsox-fmt-base libsox1b libsoxr0 libspandsp2 libsvga1 
libswscale-extra-2 libtar0 libtesseract3 libthunarx-2-0 
libtinyxml2.6.2 libts-0.0-0 libtumbler-1-0 libtwolame0 
libumfpack5.4.0 libupnp3 libva-intel-vaapi-driver libvamp-hostsdk3 
libvcdinfo0 libvisio-0.0-0 libvlc5 libvlccore5 libvo-aacenc0 
libvo-amrwbenc0 libwayland-egl1-mesa-lts-trusty 
libwayland-ltst-client0 libwayland-ltst-server0 libwebcam0 libwebp2 
libwildmidi-config libwildmidi1 libwpd-0.9-9 libwpg-0.2-2 
libwps-0.2-2 libwv-1.2-4 libwxbase2.8-0 libwxgtk2.8-0 libx264-120 
libxatracker2-lts-trusty libxcb-keysyms1 libxfce4ui-1-0 
libxfce4ui-utils libxfce4util-bin libxfce4util-common libxfce4util4 
libxfce4util6 libxfcegui4-4 libxfconf-0-2 libxmmsclient6 
libxrandr-ltst2 libxvidcore4 libzbar0 libzen0 libzlcore-data 
libzlcore0.12 libzltext-data libzltext0.12 libzlui-qt4 
libzthread-2.3-2 libzvbi-common libzvbi0 lightdm-gtk-greeter 
link-grammar-dictionaries-en linux-generic-lts-trusty 
linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic 
linux-headers-3.5.0-52 linux-headers-3.5.0-52-generic 
linux-headers-generic-lts-trusty linux-image-3.13.0-32-generic 
linux-image-3.5.0-52-generic linux-image-generic-lts-trusty 
lm-sensors lp-solve lubuntu-icon-theme mbmon mediainfo melt menu 
menulibre mesa-utils mirage mjpegtools mp3gain mp3splt mp3wrap mpg123 
mpg321 mplayer-skins mplayer2 mtpaint mtpfs myspell-en-gb 
mythes-en-us namebench nuvola-icon-theme openjdk-7-jre 
openjdk-7-jre-headless openshot openshot-doc orage p7zip p7zip-full 
p7zip-rar pandora parcellite parole pastebinit pavucontrol 
plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text pop3browser 
puddletag python-acoustid python-audioread python-central 
python-cherrypy3 python-chm python-cssutils python-eggtrayicon 
python-graphy python-keybinder python-mechanize python-mlt3 
python-musicbrainz2 python-pymad python-pyparsing python-pyquery 
python-support python-uno radiotray recoll recordmydesktop 
rev-plugins rtmpdump rubberband-ladspa shimmer-themes sqlitebrowser 
ssh-askpass stardict stardict-common stardict-gtk streamripper 
streamtuner2 supertuxkart supertuxkart-data swh-plugins synaptic 
syslinux-themes-debian syslinux-themes-debian-squeeze 
system-tools-backends tagtool tap-plugins tesseract-ocr 
tesseract-ocr-eng tesseract-ocr-equ tesseract-ocr-osd thunar 
thunar-archive-plugin thunar-data thunar-gtkhash 
thunar-media-tags-plugin thunar-volman timidity 
timidity-interfaces-extra tsconf ttf-droid ttf-lyx tumbler 
tumbler-common twolame ubuntu-restricted-addons unetbootin 
unetbootin-translations uno-libs3 unrar unrtf ure uvcdynctrl 
uvcdynctrl-data vainfo vcdimager vdpau-va-driver virtualbox-4.3 vlc 
vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse vnstat wavpack 
winff winff-doc x11-xserver-utils-lts-trusty xchat xchat-common 
xfburn xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin 
xfce4-datetime-plugin xfce4-dict xfce4-indicator-plugin 
xfce4-mailwatch-plugin xfce4-mount-plugin xfce4-netload-plugin 
xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel 
xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data 
xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session 
xfce4-settings xfce4-systemload-plugin xfce4-taskmanager 
xfce4-terminal xfce4-verve-plugin xfce4-volumed xfce4-volumed-pulse 
xfce4-weather-plugin xfce4-whiskermenu-plugin xfce4-xkb-plugin xfconf 
xfdesktop4 xfdesktop4-data xfwm4 xfwm4-themes xmp-audacious 
xmp-common xournal xsane xsane-common xserver-common-lts-trusty 
xserver-xorg-core-lts-trusty xserver-xorg-input-all-lts-trusty 
xserver-xorg-input-evdev-lts-trusty 
xserver-xorg-input-mouse-lts-trusty 
xserver-xorg-input-synaptics-lts-trusty 
xserver-xorg-input-vmmouse-lts-trusty 
xserver-xorg-input-wacom-lts-trusty xserver-xorg-lts-trusty 
xserver-xorg-video-all-lts-trusty xserver-xorg-video-ati-lts-trusty 
xserver-xorg-video-cirrus-lts-trusty 
xserver-xorg-video-fbdev-lts-trusty 
xserver-xorg-video-glamoregl-lts-trusty 
xserver-xorg-video-intel-lts-trusty 
xserver-xorg-video-mach64-lts-trusty 
xserver-xorg-video-mga-lts-trusty 
xserver-xorg-video-modesetting-lts-trusty 
xserver-xorg-video-neomagic-lts-trusty 
xserver-xorg-video-nouveau-lts-trusty 
xserver-xorg-video-openchrome-lts-trusty 
xserver-xorg-video-r128-lts-trusty 
xserver-xorg-video-radeon-lts-trusty xserver-xorg-video-s3-lts-trusty 
xserver-xorg-video-savage-lts-trusty 
xserver-xorg-video-siliconmotion-lts-trusty 
xserver-xorg-video-sis-lts-trusty 
xserver-xorg-video-sisusb-lts-trusty 
xserver-xorg-video-tdfx-lts-trusty 
xserver-xorg-video-trident-lts-trusty 
xserver-xorg-video-vesa-lts-trusty 
xserver-xorg-video-vmware-lts-trusty xubuntu-artwork 
xubuntu-default-settings xubuntu-desktop xubuntu-docs 
xubuntu-icon-theme xubuntu-restricted-addons 
xubuntu-restricted-extras xubuntu-wallpapers xul-ext-lightning zsync 

```

I have only just upgraded my HWE to the trusty version and for some reason just about every package that has just been added doing that, along with goodness knows how many others, is shown as unsupported.

None of this makes any sense at all; I know this HWE update process has been a bit of a disaster for many, and caused a huge number of forum threads about problems, but having done it successfully to now be told that it is not supported is ridiculous, to say the least.

Surely someone or other must know what on earth is going on here.

---

