---
title: "500mb Ubuntu for Virtualbox.  Can it be done?"
date: 2009-06-08
forum: Virtualisation
---

### Post by michaelcole on 2009-06-08
I'm looking for specific advice on what I can remove from the standard install to get an Ubuntu/LAMP/NetbeansPHP VirtualBox machine down to a 800mb bittorrent.

 - I've been focusing on removing aptitude packages.  Are there other places to look?
 - What's the smartest way to build lists of packages to remove?
 - How do I remove all the unnecessary drivers?
 - Am I taking the right approach?  Is there a simpler way?

I've been working on it for 2 days, and have gotten from 2.2gb to 1.5gb, but I'm running out of easy stuff.

I'm working on an open-sourced PHP project called Drupal and want a reference dev/test environment to share around.  A VM would make it very easy for non-linux users to learn/use linux in a production-like invironment, instead of installing WAMP.

This script has been very helpful to print out a list of packages sorted by size:  
```
for pkg in `dpkg --list | awk '/ii/ {print $2}'`; do echo -e "`dpkg --status $pkg | grep Installed-Size | awk '{print $2}'` \t\t $pkg" >> pkgs.tmp; done; sort -rg pkgs.tmp > pkgs; rm -f pkgs.tmp;

```

After that, it's been trial and error to remove extra stuff: openoffice, printing, scanners, gimp, etc.  But it's been slow going to know what's what.

I looked at other distros with these results:
 - Puppy linux - no aptitude - [http://www.tombh.co.uk/?p=20](http://www.tombh.co.uk/?p=20)
 - DSL linux - old kernel, no plan to upgrade
 - XUbuntu - After slimming, is the same size as Ubuntu and less mainstream.
 - RULE - Redhat based.
 - Fluxbuntu - current version is Ubuntu 7.10 based
These brought me back to Ubuntu.

Here is the script I've made so far:
```

#!/bin/bash
#Starting size:
df -h -T > size_start.txt
aptitude update   		# update my database of newest packages
aptitude install localepurge	# package to delete unnecessary translations.  Select en and en_us packages to keep them.
# 326mb - Open office
aptitude remove --purge openoffice.org-writer openoffice.org-calc openoffice.org-core openoffice.org-math openoffice.org-impress openoffice.org-base-core openoffice.org-common openoffice.org-draw openoffice.org-emailmerge   openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-style-human openoffice.org-thesaurus-en-au python-uno language-support-writing-en openoffice.org-thesaurus-en-us openoffice.org-hyphenation openoffice.org-hyphenation-en-us openoffice.org-l10n-common language-support-translations-en language-support-en thunderbird-locale-en-gb
#  46mb - games
aptitude remove --purge gnome-games gnome-games-data                                
#   8mb - accessability
aptitude remove --purge gnome-orca                                                   
#   4mb - palm pilot
aptitude remove --purge gnome-pilot gnome-pilot-conduits                             
#  10mb - screen savers
aptitude remove --purge xscreensaver-data xscreensaver-gl screensaver-default-images gnome-screensaver ubuntu-desktop
#  11mb - cd creator
aptitude remove --purge brasero wodim libbrasero-media0 cdparanoia                   
#  28mb - help files
aptitude remove --purge gimp-help-common gimp-help-en                                
#  68mb - user guide
aptitude remove --purge gnome-user-guide gnome-user-guide-en ubuntu-docs             
#  10mb - user guide
aptitude remove --purge man-db manpages yelp info evolution-documentation-en ubuntu-standard 
#   4mb - bluetooth
aptitude remove --purge bluez-gnome bluez bluetooth bluez-utils bluez-alsa bluez-gstreamer bluez-cups libmbca0 
#  16mb - skype clone
aptitude remove --purge espeak ekiga                                                 
#  54mb - email
aptitude remove --purge evolution evolution-common evolution-data-server evolution-exchange evolution-indicator evolution-plugins 
#  10mb - spam filter
aptitude remove --purge bogofilter bogofilter-bdb bogofilter-common                  
#  14mb - video player
aptitude remove --purge totem totem-mozilla totem-common totem-gstreamer totem-plugins 
#  76mb - printing
aptitude remove --purge cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers foo2zjs foomatic-db foomatic-db-engine foomatic-filters ghostscript ghostscript-x groff-base  cups-driver-gutenprint hal-cups-utils hplip hpijs foomatic-db-hpijs openprinting-ppds pnm2ppa pxljr splix hplip-data system-config-printer-common system-config-printer-gnome python-cups 
#   5mb - scanner drivers
aptitude remove --purge xsane sane-utils xsane-common                                
#  .5mb - understand raw camera images
aptitude remove --purge dcraw                                                        
#  30mb - mono .net layer
aptitude remove --purge mono-runtime f-spot libgconf2.24-cil libmono-addins0.2-cil libmono2.0-cil mono-2.0-gac tomboy libgnome2.24-cil libmono-addins-gui0.2-cil libmono-system-web2.0-cil mono-2.0-runtime mono-gac libflickrnet2.1.5-cil libgnomepanel2.24-cil 
#  26mb - Fancy GUI
aptitude remove --purge compiz compiz-core compiz-gnome compiz-plugins compiz-wrapper compiz-fusion-plugins-extra compiz-fusion-plugins-main compizconfig-backend-gconf libcompizconfig0 
#  11mb - example videos and stuff
aptitude remove --purge example-content                                              
#  13mb - pgp GUI
aptitude remove --purge seahorse seahorse-plugins                                   
#  15mb - Audio player
aptitude remove --purge rhythmbox                                                    
#   4mb - Video drivers
aptitude remove --purge nvidia-common rss-glx                                        
#   3mb - Math app - linear programming
aptitude remove --purge libgsl0ldbl lp-solve                                         
#  93mb - Headers for Programming linux 
aptitude remove --purge linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic linux-headers-generic linux-libc-dev libc6-dev 
#  30mb - bittorrent client
aptitude remove --purge transmission-common transmission-gtk                         
#  30mb - Instant Messaging 
aptitude remove --purge pidgin pidgin-data  libpurple0 pidgin-otr pidgin-libnotify   
#  39mb - OpenGL
aptitude remove --purge mesa-utils libglu1-mesa libgl1-mesa-dri libgl1-mesa-glx libvisual-0.4-plugins x11-utils xorg libglew1.5 libglitz-glx1 
#  46mb - Graphics editing.  would be nice to keep.
aptitude remove --purge gimp gimp-help-en gimp-data gimp-help-common 
#  12mb - Laptop stuff
aptitude remove --purge gnome-power-manager 
#  11mb - Desktop theming
aptitude remove --purge tangerine-icon-theme gnome-accessibility-themes gnome-themes-selected usplash-theme-ubuntu gnome-themes-ubuntu ubuntu-sounds gnome-cards-data 
aptitude autoclean 		    	# clean up aptitude files
aptitude upgrade			# upgrade whats left
aptitude install deborphan		# package to find orphan packages
deborphan				# display them to user
#  54mb - Remove orphan packages
deborphan | xargs sudo apt-get -y remove --purge   
#Ending size
df -h -T > size_end.txt
#What's installed: look in file whats_installed.txt
for pkg in `dpkg --list | awk '/ii/ {print $2}'`; do echo -e "`dpkg --status $pkg | grep Installed-Size | awk '{print $2}'` \t\t $pkg" >> pkgs.tmp; done; sort -rg pkgs.tmp > whats_installed.txt; rm -f pkgs.tmp;


```

Here's what's left larger than 1000kb:
```

93424 		 linux-image-2.6.28-11-generic
24876 		 gnome-applets-data
24744 		 smbclient
23360 		 app-install-data
21204 		 gnome-icon-theme
21164 		 ttf-arphic-uming
20528 		 gnome-utils
20380 		 xulrunner-1.9
19568 		 libgtk2.0-common
18716 		 libgweather-common
15980 		 gdm
15052 		 nautilus-data
14520 		 perl-modules
14164 		 libicu38
13632 		 perl
13612 		 gedit-common
12584 		 ttf-unfonts-core
12508 		 gnome-panel-data
11412 		 samba-common
11084 		 coreutils
10904 		 libc6
10460 		 metacity-common
10440 		 ttf-sazanami-mincho
10348 		 human-icon-theme
9676 		 aptitude
9320 		 python2.6
8864 		 gnome-system-tools
8796 		 locales
8768 		 capplets-data
8472 		 binutils
8392 		 iso-codes
8324 		 linux-firmware
8324 		 gnome-terminal-data
8312 		 xfonts-base
8276 		 evolution-data-server-common
8244 		 gcalctool
7636 		 ttf-sazanami-gothic
7512 		 cpp-4.3
7320 		 gnome-system-monitor
7280 		 dpkg
7196 		 brltty
6776 		 libgs8
6680 		 libssl0.9.8
6644 		 gnome-media-common
6396 		 gconf2-common
6312 		 eog
6280 		 tzdata
6204 		 gdb
6140 		 ttf-arabeyes
6080 		 synaptic
5988 		 file-roller
5928 		 libmagickcore1
5528 		 evince
5260 		 libgtk2.0-0
5232 		 apt
4932 		 python-gtk2
4896 		 xfonts-100dpi
4844 		 zenity
4836 		 gnupg
4792 		 gsfonts
4724 		 gcc-4.3
4664 		 python2.6-minimal
4564 		 xfonts-75dpi
4556 		 update-manager-core
4496 		 gnome-keyring
4460 		 libgphoto2-2
4448 		 ttf-thai-tlwg
4388 		 gnome-mime-data
4348 		 perl-base
4284 		 xserver-xorg-core
4284 		 libmono-system2.0-cil
4276 		 xkb-data
4272 		 libgtk2.0-cil
4220 		 libsmbclient
4172 		 gnome-desktop-data
4140 		 libgtk2-perl
4100 		 gucharmap
3948 		 libgtkmm-2.4-1c2a
3852 		 libglib2.0-data
3848 		 xcursor-themes
3780 		 vinagre
3732 		 libgtkhtml3.14-19
3720 		 libgnome2-common
3696 		 gnome-doc-utils
3520 		 dmz-cursor-theme
3496 		 network-manager-gnome
3484 		 ttf-freefont
3484 		 gstreamer0.10-plugins-good
3456 		 libgnomeui-common
3456 		 firefox-3.0
3412 		 libgtksourceview2.0-common
3392 		 libgucharmap7
3352 		 libgnomevfs2-common
3240 		 gnome-settings-daemon
3220 		 fast-user-switch-applet
3176 		 libpt2.6.1
3088 		 gconf-editor
3076 		 uno-libs3
3036 		 shared-mime-info
3008 		 gvfs
2972 		 nautilus
2952 		 gnome-session
2932 		 login
2904 		 mousetweaks
2816 		 language-pack-en-base
2796 		 libnss3-1d
2792 		 libc6-i686
2780 		 ubuntu-gdm-themes
2660 		 gnome-app-install
2652 		 libsnmp-base
2636 		 python-apt
2628 		 libmono0
2624 		 gnome-nettool
2588 		 ttf-dejavu-core
2588 		 libmono-corlib2.0-cil
2564 		 linux-restricted-modules-2.6.28-11-generic
2556 		 tasksel-data
2488 		 docbook-xml
2484 		 libgstreamer0.10-0
2476 		 vino
2440 		 command-not-found-data
2436 		 libpython2.6
2436 		 libgtksourceview-common
2420 		 libmagic1
2388 		 passwd
2332 		 libaspell15
2296 		 mono-jit
2248 		 libwnck-common
2244 		 tar
2224 		 ubuntu-wallpapers
2140 		 language-pack-gnome-en-base
2116 		 libx11-data
2112 		 apparmor
2080 		 network-manager
2068 		 e2fsprogs
2028 		 python-gdata
2012 		 libbonobo2-common
2000 		 python-gst0.10
1980 		 alsa-utils
1956 		 scim
1932 		 wget
1916 		 hal
1900 		 gvfs-backends
1896 		 python-xapian
1896 		 openssh-client
1884 		 gedit
1868 		 w3m
1848 		 libdirectfb-1.0-0
1836 		 libtotem-plparser12
1828 		 util-linux
1816 		 libpoppler4
1796 		 libglib2.0-0
1780 		 pulseaudio
1728 		 nano
1716 		 libgnomeprintui2.2-common
1700 		 gnome-menus
1696 		 gstreamer0.10-plugins-base
1692 		 sgml-data
1672 		 libatk1.0-data
1672 		 iptables
1644 		 gnome-mag
1640 		 python-rdflib
1640 		 libxapian15
1636 		 libxml2
1628 		 apparmor-utils
1616 		 libdjvulibre21
1612 		 ttf-indic-fonts-core
1612 		 libbonoboui2-common
1548 		 lftp
1540 		 espeak-data
1536 		 python-libxml2
1536 		 libgnomeprint2.2-data
1528 		 findutils
1528 		 at-spi
1520 		 update-manager
1520 		 jockey-common
1504 		 libsamplerate0
1504 		 libgnomecanvas2-common
1492 		 sg3-utils
1432 		 dialog
1420 		 checkbox
1416 		 genisoimage
1416 		 binutils-static
1408 		 libprotobuf3
1408 		 libdb4.7
1388 		 libperl5.10
1388 		 language-selector-common
1384 		 libdns45
1380 		 python-gnome2-desktop
1376 		 kbd
1344 		 python-imaging
1336 		 libgstreamer-plugins-base0.10-0
1328 		 hicolor-icon-theme
1328 		 console-setup
1292 		 xserver-xorg-video-intel
1264 		 libasound2
1260 		 x11-apps
1260 		 libvte9
1260 		 libdb4.6
1240 		 alacarte
1236 		 bash
1228 		 python-gnome2
1224 		 libgraphviz4
1220 		 gnome-control-center
1208 		 make
1208 		 gtk2-engines
1184 		 libmagickwand1
1176 		 libx11-6
1176 		 libkrb53
1172 		 libstdc++6
1168 		 gnome-panel
1160 		 aspell
1152 		 xterm
1144 		 grep
1136 		 tsclient
1136 		 reiserfsprogs
1136 		 libmono-i18n2.0-cil
1120 		 libslang2
1108 		 libglib-perl
1100 		 evolution-webcal
1100 		 debconf-i18n
1088 		 python-gobject
1088 		 ppp
1084 		 libvte-common
1064 		 libgnome2-perl
1060 		 libvorbisenc2
1048 		 libgnutls26
1044 		 libwww-perl
1040 		 python-software-properties
1032 		 libpam-runtime
1024 		 libgtop2-common
1020 		 wamerican
1020 		 nautilus-sendto
1016 		 wbritish
1016 		 libpam-modules
1016 		 libmono-system-data2.0-cil
1008 		 screen
1004 		 busybox-initramfs

```

---

### Post by Cheesemill on 2009-06-09
What are you using as your base OS?
If you're using a standard server install then try taking a look at Ubuntu JeOS instead. It's a Ubuntu server install that's specifically designed for VM's. It uses a smaller kernel which only has the drivers needed for virtual machines as well as installing absolutely no unneeded packages at all.

You basically start of with the smallest Ubuntu possible and build it up from there.

From 8.10 onwards JeOS is part of the standard server install CD, just hit F4 on the first install screen and select 'Install a minimal virtual machine'.

Of course you'll be wanting to use 8.04 instead because it's LTS. You can download the CD image from [here]("http://cdimage.ubuntu.com/jeos/hardy/daily/current/"), it's only 100MB.

There are also instructions here
[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)
that guide you through setting up a virtual machine with JeOS. They were a great help to me for my dev work.

Hope this helps,
Cheesemill

---

### Post by Cheesemill on 2009-06-09
I've just re-read your post and realised that you have a Desktop install.
Is there any reason you've chosen this route (ie why do you need a GUI)?

If you absolutely have to have a GUI (read [here]("https://help.ubuntu.com/community/ServerGUI") and [here]("http://ubuntuforums.org/showthread.php?t=1091273") for why you shouldn't) then you should use the JeOS option I mentioned above to get a minimal CLI install then do the following to install your Desktop.

```

sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install xorg
sudo apt-get install gdm gnome-core ubuntu-artwork fast-user-switch-applet
sudo apt-get clean
sudo shutdown now -r

```

This will give you the smallest Ubuntu Desktop possible, you can then build it up from there.

Cheesemill



Edit - I've just been testing out VM installs for work and have the following stats for you:

JeOS Install + Updates = 425MB
JeOS Install + Updates + Desktop = 803MB

This doesn't include the swap partition, so for what you're trying to do the I think the answer is no - you can't have a Ubuntu desktop install that's smaller than 803MB (not including **any** apps).

---

### Post by bodhi.zazen on 2009-06-09
I suggest JeOS :

[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)

Or the minimal CD :
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and build up.

The smallest install can be done with debootstrap

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

But to be honest, JeOS is probably the easiest.

---

### Post by Andrew.Z on 2009-07-21
BleachBit [frees 700% more disk space than localepurge](http://bleachbit.blogspot.com/2009/07/free-disk-space-localepurge.html) (on a standard Jaunty)

---

