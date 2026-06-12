---
title: "Idea for a 'Desktop Cleanup' application for ubuntu"
date: 2010-08-18
forum: The Cafe
---

### Post by user1397 on 2010-08-18
So I just got an idea...an app similar to Windows' Disk Cleanup, except for ubuntu of course!

I got the idea from doing several commands in the terminal to clean my system. I thought well the whole point of user friendliness is that things should migrate to GUI when possible, right? So the commands I'll include (at least at first) are:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get check
sudo apt-get -f install
localepurge
deborphan --guess-all

(those last two obviously requiring the programs localepurge and deborphan)

So I'm thinking if a simple app could be made that performs various cleanup commands such as these (and possibly many more) it would be kinda neat.

Any thoughts?

(I can't program, so this is just an idea for now.)

P.S. I do realize the program 'Computer Janitor' is similar to my idea (maybe even identical, I don't really know because I've never tried it).  I have heard it has its fair share of problems though.

---

### Post by user1397 on 2010-08-19
bump

---

### Post by sataris on 2010-08-19
Computer janitor loves to remove things that are actually useful. First, Last, and Only time I ever ran it, it wiped out my X .conf and several other files.
 
This is a good idea, however i think there is actually a prog out there that acts like CCCleaner for Linux. Just search the forums, as i think its a recurring question.

---

### Post by linux18 on 2010-08-19
bleachbit does most of that already, but the main space hogs in ubuntu are the programs that you will never use that take up space, I've already made a remix with these programs removed from a normal installation:

```
 aisleriot 
apport 
apport-gtk 
apturl 
aspell 
aspell-en 
bc 
bluez 
bluez-cups 
bluez-gstreamer 
bogofilter 
bogofilter-bdb 
bogofilter-common 
branding-ubuntu 
brasero 
brasero-common 
brltty 
brltty-x11 
byobu 
checkbox 
checkbox-gtk 
command-not-found 
command-not-found-data 
compiz 
compiz-core 
compiz-fusion-plugins-main 
compiz-gnome 
compiz-plugins 
compizconfig-backend-gconf 
computer-janitor 
computer-janitor-gtk 
couchdb-bin 
cups 
cups-bsd 
cups-client 
cups-common 
cups-driver-gutenprint 
desktopcouch 
dictionaries-common 
dmz-cursor-theme 
doc-base 
empathy 
empathy-common 
eog 
espeak 
espeak-data 
evince 
evolution 
evolution-common 
evolution-couchdb 
evolution-data-server 
evolution-exchange 
evolution-indicator 
evolution-plugins 
example-content 
f-spot 
firefox 
firefox-branding 
firefox-gnome-support 
foo2zjs 
foomatic-db 
foomatic-db-engine 
foomatic-filters 
gbrainy 
gcalctool 
gedit 
gedit-common 
ghostscript 
ghostscript-cups 
ghostscript-x 
gnome-accessibility-themes 
gnome-bluetooth 
gnome-codec-install 
gnome-doc-utils 
gnome-games-common 
gnome-mag 
gnome-mahjongg 
gnome-media 
gnome-media-common 
gnome-orca 
gnome-screensaver 
gnome-sudoku 
gnome-themes-selected 
gnome-themes-ubuntu 
gnome-user-guide 
gnome-user-share 
gnomine 
gsfonts 
gstreamer0.10-alsa 
gstreamer0.10-gnonlin 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-pulseaudio 
gstreamer0.10-x 
gucharmap 
guile-1.8-libs 
gvfs-backends 
gwibber 
gwibber-service 
hpijs 
hplip 
hplip-data 
humanity-icon-theme 
hunspell-en-ca 
hunspell-en-us 
indicator-me 
indicator-messages 
language-pack-de 
language-pack-de-base 
language-pack-en 
language-pack-en-base 
language-pack-es 
language-pack-es-base 
language-pack-gnome-de 
language-pack-gnome-de-base 
language-pack-gnome-en 
language-pack-gnome-en-base 
language-pack-gnome-es 
language-pack-gnome-es-base 
language-pack-gnome-pt 
language-pack-gnome-pt-base 
language-pack-gnome-xh 
language-pack-gnome-xh-base 
language-pack-pt 
language-pack-pt-base 
language-pack-xh 
language-pack-xh-base 
language-support-en 
language-support-writing-en 
libart2.0-cil 
libaspell15 
libbrasero-media0 
libcompizconfig0 
libenchant1c2a 
libespeak1 
libflickrnet2.2-cil 
libgconf2.0-cil 
libglade2.0-cil 
libglib2.0-cil 
libgmime2.4-cil 
libgnome-keyring1.0-cil 
libgnome-media0 
libgnome-vfs2.0-cil 
libgnome2.24-cil 
libgnomepanel2.24-cil 
libgnomevfs2-extra 
libgs8 
libgstfarsight0.10-0 
libgstreamer-plugins-base0.10-0 
libgtk2.0-cil 
libgtkhtml-editor0 
libgtkhtml3.14-19 
libgtkspell0 
libgutenprint2 
libhunspell-1.2-0 
liblaunchpad-integration1.0-cil 
liblouis-data 
liblouis0 
libmagickcore2-extra 
libmono-addins-gui0.2-cil 
libmono-addins0.2-cil 
libmono-cairo2.0-cil 
libmono-corlib2.0-cil 
libmono-data-tds2.0-cil 
libmono-i18n-west2.0-cil 
libmono-posix2.0-cil 
libmono-security2.0-cil 
libmono-sharpzip2.84-cil 
libmono-sqlite2.0-cil 
libmono-system-data2.0-cil 
libmono-system-runtime2.0-cil 
libmono-system-web2.0-cil 
libmono-system2.0-cil 
libmono2.0-cil 
libndesk-dbus-glib1.0-cil 
libndesk-dbus1.0-cil 
libnunit2.4-cil 
libpurple0 
libsane 
libsmbclient 
libspectre1 
libtelepathy-farsight0 
libtelepathy-glib0 
libtotem-plparser17 
libubuntuone-1.0-1 
libwebkit-1.0-2 
libwmf0.2-7 
libwmf0.2-7-gtk 
light-themes 
m17n-contrib 
m17n-db 
manpages-dev 
modemmanager 
mono-2.0-gac 
mono-gac 
mono-runtime 
mousetweaks 
myspell-en-au 
myspell-en-gb 
myspell-en-za 
nautilus-sendto 
nautilus-sendto-empathy 
nautilus-share 
notify-osd-icons 
onboard 
openoffice.org-base-core 
openoffice.org-calc 
openoffice.org-common 
openoffice.org-core 
openoffice.org-draw 
openoffice.org-emailmerge 
openoffice.org-gnome 
openoffice.org-gtk 
openoffice.org-help-en-us 
openoffice.org-impress 
openoffice.org-math 
openoffice.org-style-human 
openoffice.org-writer 
openprinting-ppds 
openssh-client 
pitivi 
pnm2ppa 
pppconfig 
pxljr 
python-aptdaemon-gtk 
python-desktopcouch 
python-desktopcouch-records 
python-farsight 
python-gst0.10 
python-gtkspell 
python-louis 
python-papyon 
python-smbc 
python-speechd 
python-telepathy 
python-ubuntuone 
python-uno 
python-webkit 
quadrapassel 
rhythmbox 
rhythmbox-plugin-cdrecorder 
rhythmbox-plugins 
rhythmbox-ubuntuone-music-store 
samba-common 
samba-common-bin 
sane-utils 
screen 
screensaver-default-images 
seahorse 
simple-scan 
smbclient 
software-center 
speech-dispatcher 
splix 
ssh-askpass-gnome 
syslinux 
system-config-printer-common 
system-config-printer-gnome 
telepathy-butterfly 
telepathy-gabble 
telepathy-haze 
telepathy-idle 
telepathy-mission-control-5 
telepathy-salut 
tomboy 
totem 
totem-common 
totem-mozilla 
totem-plugins 
transmission-common 
transmission-gtk 
ttf-indic-fonts-core 
ttf-khmeros-core 
ttf-liberation 
ttf-takao-pgothic 
ttf-thai-tlwg 
ttf-unfonts-core 
ttf-wqy-microhei 
ubiquity-slideshow-ubuntu 
ubufox 
ubuntu-artwork 
ubuntu-desktop 
ubuntu-docs 
ubuntu-mono 
ubuntu-sounds 
ubuntu-wallpapers 
ubuntuone-client 
ubuntuone-client-gnome 
uno-libs3 
ure 
usb-creator-common 
usb-creator-gtk 
vinagre 
vino 
wamerican 
wbritish 
wodim 
x11-apps 
x11-utils 
xcursor-themes 
xfonts-75dpi 
xorg 
xscreensaver-data 
xscreensaver-gl 
xulrunner-1.9.2 
yelp 

gvfs-bin
libgraphite3
libwps-0.1-1
libsdl1.2debian
tk8.4
libv4l-0
libglitz-glx1
libavc1394-0
libgtk-vnc-1.0-0
libwbclient0
libloudmouth1-0
libwavpack1
libexchange-storage1.2-3
libmtp8
libegroupwise1.2-13
librdf0
libxxf86dga1
libkpathsea5
libslp1
liboil0.3
libgtkhtml-editor-common
libcupsmime1
libdv4
libneon27-gnutls
libgpgme11
libieee1284-3
libspeechd2
gnome-session-canberra
libcupsdriver1
libevview2
libgdiplus
libportaudio2
libevent-1.4-2
libdesktopcouch-glib-1.0-2
libshout3
libsilc-1.1-2
libclutter-gtk-0.10-0
libcdio-paranoia0
libwpg-0.1-1
libsqlite0
libpoppler-glib4
libsilcclient-1.1-3
libpst4
libcryptui0
libavahi-gobject0
libgraphviz4
libopenexr6
libgnome-pilot2
libhpmud0
libcurl3
libijs-0.35
libgadu3
libiec61883-0
libgmime-2.4-2
liblircclient0
libgail-gnome-module
libbeagle1
libwebkit-1.0-common
libxp6
libgdata-google1.2-1
libdotconf1.0
libedata-book1.2-2
libhyphen0
libcaca0
libcupscgi1
libtag1c2a
libgphoto2-2
liblpint-bonobo0
libedata-cal1.2-6
libarchive1
libedit2
libzephyr4
libcupsppdc1
libaa1
libdjvulibre21
libmeanwhile1
libgnome-mag2
libmusicbrainz4c2a
gvfs-fuse
libgdata6
libcupsimage2
libclutter-1.0-0
libpth20
libraw1394-11
libpisync1
libspeex1
libgif4
libtag1-vanilla
libcdio-cdda0
libgdata-common
libevdocument2
libsnmp15
libtheora0
libgdata1.2-1
libdjvulibre-text
libebackend1.2-0
liblzma1
libilmbase6
libsdl1.2debian-pulseaudio
librasqal2
libtalloc2
libcouchdb-glib-1.0-2
libglitz1
libgphoto2-port0
libwpd8c2a
libperl5.10
libsnmp-base
libcdio10
libpisock9
libraptor1 
```if you want to try it out, send me a message later, I'm still working on it so the newer the version the better.

but for existing installations, bleachbit is one of the best programs out there

---

### Post by sataris on 2010-08-19
if you rm all that, just use arch?

---

### Post by linux18 on 2010-08-19
> **sataris said:**
> if you rm all that, just use arch?
arch doesn't support my hardware :)

---

### Post by TwoEars on 2010-08-19
> **linux18 said:**
> bleachbit does most of that already, but the main space hogs in ubuntu are the programs that you will never use that take up space, I've already made a remix with these programs removed from a normal installation:

```
 aisleriot 
apport 
apport-gtk 
apturl 
aspell 
aspell-en 
bc 
bluez 
bluez-cups 
bluez-gstreamer 
bogofilter 
bogofilter-bdb 
bogofilter-common 
branding-ubuntu 
brasero 
brasero-common 
brltty 
brltty-x11 
byobu 
checkbox 
checkbox-gtk 
command-not-found 
command-not-found-data 
compiz 
compiz-core 
compiz-fusion-plugins-main 
compiz-gnome 
compiz-plugins 
compizconfig-backend-gconf 
computer-janitor 
computer-janitor-gtk 
couchdb-bin 
cups 
cups-bsd 
cups-client 
cups-common 
cups-driver-gutenprint 
desktopcouch 
dictionaries-common 
dmz-cursor-theme 
doc-base 
empathy 
empathy-common 
eog 
espeak 
espeak-data 
evince 
evolution 
evolution-common 
evolution-couchdb 
evolution-data-server 
evolution-exchange 
evolution-indicator 
evolution-plugins 
example-content 
f-spot 
firefox 
firefox-branding 
firefox-gnome-support 
foo2zjs 
foomatic-db 
foomatic-db-engine 
foomatic-filters 
gbrainy 
gcalctool 
gedit 
gedit-common 
ghostscript 
ghostscript-cups 
ghostscript-x 
gnome-accessibility-themes 
gnome-bluetooth 
gnome-codec-install 
gnome-doc-utils 
gnome-games-common 
gnome-mag 
gnome-mahjongg 
gnome-media 
gnome-media-common 
gnome-orca 
gnome-screensaver 
gnome-sudoku 
gnome-themes-selected 
gnome-themes-ubuntu 
gnome-user-guide 
gnome-user-share 
gnomine 
gsfonts 
gstreamer0.10-alsa 
gstreamer0.10-gnonlin 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-pulseaudio 
gstreamer0.10-x 
gucharmap 
guile-1.8-libs 
gvfs-backends 
gwibber 
gwibber-service 
hpijs 
hplip 
hplip-data 
humanity-icon-theme 
hunspell-en-ca 
hunspell-en-us 
indicator-me 
indicator-messages 
language-pack-de 
language-pack-de-base 
language-pack-en 
language-pack-en-base 
language-pack-es 
language-pack-es-base 
language-pack-gnome-de 
language-pack-gnome-de-base 
language-pack-gnome-en 
language-pack-gnome-en-base 
language-pack-gnome-es 
language-pack-gnome-es-base 
language-pack-gnome-pt 
language-pack-gnome-pt-base 
language-pack-gnome-xh 
language-pack-gnome-xh-base 
language-pack-pt 
language-pack-pt-base 
language-pack-xh 
language-pack-xh-base 
language-support-en 
language-support-writing-en 
libart2.0-cil 
libaspell15 
libbrasero-media0 
libcompizconfig0 
libenchant1c2a 
libespeak1 
libflickrnet2.2-cil 
libgconf2.0-cil 
libglade2.0-cil 
libglib2.0-cil 
libgmime2.4-cil 
libgnome-keyring1.0-cil 
libgnome-media0 
libgnome-vfs2.0-cil 
libgnome2.24-cil 
libgnomepanel2.24-cil 
libgnomevfs2-extra 
libgs8 
libgstfarsight0.10-0 
libgstreamer-plugins-base0.10-0 
libgtk2.0-cil 
libgtkhtml-editor0 
libgtkhtml3.14-19 
libgtkspell0 
libgutenprint2 
libhunspell-1.2-0 
liblaunchpad-integration1.0-cil 
liblouis-data 
liblouis0 
libmagickcore2-extra 
libmono-addins-gui0.2-cil 
libmono-addins0.2-cil 
libmono-cairo2.0-cil 
libmono-corlib2.0-cil 
libmono-data-tds2.0-cil 
libmono-i18n-west2.0-cil 
libmono-posix2.0-cil 
libmono-security2.0-cil 
libmono-sharpzip2.84-cil 
libmono-sqlite2.0-cil 
libmono-system-data2.0-cil 
libmono-system-runtime2.0-cil 
libmono-system-web2.0-cil 
libmono-system2.0-cil 
libmono2.0-cil 
libndesk-dbus-glib1.0-cil 
libndesk-dbus1.0-cil 
libnunit2.4-cil 
libpurple0 
libsane 
libsmbclient 
libspectre1 
libtelepathy-farsight0 
libtelepathy-glib0 
libtotem-plparser17 
libubuntuone-1.0-1 
libwebkit-1.0-2 
libwmf0.2-7 
libwmf0.2-7-gtk 
light-themes 
m17n-contrib 
m17n-db 
manpages-dev 
modemmanager 
mono-2.0-gac 
mono-gac 
mono-runtime 
mousetweaks 
myspell-en-au 
myspell-en-gb 
myspell-en-za 
nautilus-sendto 
nautilus-sendto-empathy 
nautilus-share 
notify-osd-icons 
onboard 
openoffice.org-base-core 
openoffice.org-calc 
openoffice.org-common 
openoffice.org-core 
openoffice.org-draw 
openoffice.org-emailmerge 
openoffice.org-gnome 
openoffice.org-gtk 
openoffice.org-help-en-us 
openoffice.org-impress 
openoffice.org-math 
openoffice.org-style-human 
openoffice.org-writer 
openprinting-ppds 
openssh-client 
pitivi 
pnm2ppa 
pppconfig 
pxljr 
python-aptdaemon-gtk 
python-desktopcouch 
python-desktopcouch-records 
python-farsight 
python-gst0.10 
python-gtkspell 
python-louis 
python-papyon 
python-smbc 
python-speechd 
python-telepathy 
python-ubuntuone 
python-uno 
python-webkit 
quadrapassel 
rhythmbox 
rhythmbox-plugin-cdrecorder 
rhythmbox-plugins 
rhythmbox-ubuntuone-music-store 
samba-common 
samba-common-bin 
sane-utils 
screen 
screensaver-default-images 
seahorse 
simple-scan 
smbclient 
software-center 
speech-dispatcher 
splix 
ssh-askpass-gnome 
syslinux 
system-config-printer-common 
system-config-printer-gnome 
telepathy-butterfly 
telepathy-gabble 
telepathy-haze 
telepathy-idle 
telepathy-mission-control-5 
telepathy-salut 
tomboy 
totem 
totem-common 
totem-mozilla 
totem-plugins 
transmission-common 
transmission-gtk 
ttf-indic-fonts-core 
ttf-khmeros-core 
ttf-liberation 
ttf-takao-pgothic 
ttf-thai-tlwg 
ttf-unfonts-core 
ttf-wqy-microhei 
ubiquity-slideshow-ubuntu 
ubufox 
ubuntu-artwork 
ubuntu-desktop 
ubuntu-docs 
ubuntu-mono 
ubuntu-sounds 
ubuntu-wallpapers 
ubuntuone-client 
ubuntuone-client-gnome 
uno-libs3 
ure 
usb-creator-common 
usb-creator-gtk 
vinagre 
vino 
wamerican 
wbritish 
wodim 
x11-apps 
x11-utils 
xcursor-themes 
xfonts-75dpi 
xorg 
xscreensaver-data 
xscreensaver-gl 
xulrunner-1.9.2 
yelp 

gvfs-bin
libgraphite3
libwps-0.1-1
libsdl1.2debian
tk8.4
libv4l-0
libglitz-glx1
libavc1394-0
libgtk-vnc-1.0-0
libwbclient0
libloudmouth1-0
libwavpack1
libexchange-storage1.2-3
libmtp8
libegroupwise1.2-13
librdf0
libxxf86dga1
libkpathsea5
libslp1
liboil0.3
libgtkhtml-editor-common
libcupsmime1
libdv4
libneon27-gnutls
libgpgme11
libieee1284-3
libspeechd2
gnome-session-canberra
libcupsdriver1
libevview2
libgdiplus
libportaudio2
libevent-1.4-2
libdesktopcouch-glib-1.0-2
libshout3
libsilc-1.1-2
libclutter-gtk-0.10-0
libcdio-paranoia0
libwpg-0.1-1
libsqlite0
libpoppler-glib4
libsilcclient-1.1-3
libpst4
libcryptui0
libavahi-gobject0
libgraphviz4
libopenexr6
libgnome-pilot2
libhpmud0
libcurl3
libijs-0.35
libgadu3
libiec61883-0
libgmime-2.4-2
liblircclient0
libgail-gnome-module
libbeagle1
libwebkit-1.0-common
libxp6
libgdata-google1.2-1
libdotconf1.0
libedata-book1.2-2
libhyphen0
libcaca0
libcupscgi1
libtag1c2a
libgphoto2-2
liblpint-bonobo0
libedata-cal1.2-6
libarchive1
libedit2
libzephyr4
libcupsppdc1
libaa1
libdjvulibre21
libmeanwhile1
libgnome-mag2
libmusicbrainz4c2a
gvfs-fuse
libgdata6
libcupsimage2
libclutter-1.0-0
libpth20
libraw1394-11
libpisync1
libspeex1
libgif4
libtag1-vanilla
libcdio-cdda0
libgdata-common
libevdocument2
libsnmp15
libtheora0
libgdata1.2-1
libdjvulibre-text
libebackend1.2-0
liblzma1
libilmbase6
libsdl1.2debian-pulseaudio
librasqal2
libtalloc2
libcouchdb-glib-1.0-2
libglitz1
libgphoto2-port0
libwpd8c2a
libperl5.10
libsnmp-base
libcdio10
libpisock9
libraptor1 
```if you want to try it out, send me a message later, I'm still working on it so the newer the version the better.

but for existing installations, bleachbit is one of the best programs out there

Erm..... haven't you found the minimal CD yet? [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by linux18 on 2010-08-19
> **TwoEars said:**
> Erm..... haven't you found the minimal CD yet? [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
this runs just like a live cd, so it's more user friendly to install, however were getting off topic here, I recieved a warning this morning about spamming my remixes, if you want to continue the discussion send private messages

---

### Post by user1397 on 2010-08-20
> **linux18 said:**
> bleachbit does most of that already, 
snip

but for existing installations, bleachbit is one of the best programs out there

hmm yea bleachbit looks a lot like a ccleaner equivalent for linux.   very similar to my idea i guess

---

### Post by linux18 on 2010-08-20
I think it's time to mark this thread as solved

---

### Post by MCVenom on 2010-08-20
> **linux18 said:**
> I think it's time to mark this thread as solved
I agree, I love BleachBit :)

---

### Post by user1397 on 2010-08-20
Done. :)

---

