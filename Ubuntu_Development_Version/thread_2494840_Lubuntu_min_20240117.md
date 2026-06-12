---
title: "Lubuntu min 20240117"
date: 2024-01-28
forum: Ubuntu Development Version
---

### Post by oui on 2024-01-28
I did download + install yesterday and and add a (very) light scope of apps as tiny installed app's.

my actual installation includes over the core of «Lubuntu minimal» following apps:

(coming from sourceforge:)
sudo apt install ~/refractainstaller-base.deb refractasnapshot-base.deb
The following NEW packages will be installed:
  isolinux live-boot live-boot-initramfs-tools live-config
  live-config-systemd mtools refractainstaller-base
  refractasnapshot-base squashfs-tools syslinux syslinux-common
Need to get 1.913 kB/2.097 kB of archives.

all the next come from the ubuntu repository:

sudo apt install refractainstaller-base refractasnapshot-base deborphan didiwiki clex ranger mgp abiword hunspell gnumeric xli gimp nted mplayer mplayer-gui tesseract-ocr gimagereader nemo granule luakit menu jwm

I will also REALLY use as profitable part of my installation:

- xedit
- xviewedit
- xli (instead feh)
- xcalc

are they are installed (xli extra from me) not from me but from distributor x.org or ubuntu ;-)) !

but nothing to find in the menu or in /usr/share/applications!!!

why?

(it is a great contradiction: «Lubuntu minimal» with PREinstalled usefull minimal app's but you can't reach then... grotesque would I say!

(for this reason I did install jwm + menu but both does not help: If you start jwm, you get a VERY WRONG «terminal» and precedent app's are also NOT in the «debian menu»!)

Great deception yesterday:

the settings for the user are WRONG! And it is an unusual situation (I have no experience with) I don't know the steps to change it (matter of passwd ? or matter of rights and, if yes, how to change the rights: there is NO REAL «root» but only an user, only one user, with superuser rights,  but not a real "root"!

the problem with the user settings is that the user can operate NOTHING. The user can only save in the /home/user dir if he do it in sudo mode, he can only start the browser if he does it in sudo mode (horror pure!). else in nano, he must start with

sudo nano

if he want to save the note he did write!

next problem (probably only for me):

the refracta snapshot, a extreme useful tool if you are testing an new distro because you have not to reinstall, reinstall, reinstall, does not work because the settings are not the same as in about ALL OTHER Debian derivatives!

starting

refractasnapshot  

(does not add the ending «-base»!)

and option "1"

you will get a copy of all your files excepted vmlinuz and initrd.img excepted if you did change in /etc/refractasnapshot.conf the address of both files being different in Ubuntu as in Debian (/***boot/***vmlinuz etc...). After changing that, you get the complete copy, and can in a SECOND passage, but with the option "2" this time get the ISO for the CD build.

But great deception, if you try to reinstall with 

refractainstaller (also without ending «-bas»)

you will miss global variants at start and I know myself no way to add then (but [https://extix.se](https://extix.se) did find a way! He did publish an ISO with good refractatools functions excepted an error (as I use it, perhaps it is my fault) reducing the freedom to set «start without login», a great advantage of refractatools to extend those rights!

above installation (is very complete: look those app's to use in family and with children: nted!!! granule!!! marble, merkaartor! you can write Chinese using [https://input.king](https://input.king)! You can translate Chinese books or papers usinge scan, ocr and gimagereader and after that [https://translate.google.com](https://translate.google.com)! You can manage your time in osmo etc... FOR CHILDREN: I would recommend to add, install more: kturtle, ucb-logo (the book of Bryan Harvey are on line FOR FREE, and the software from the university! Or gforth, gprolog or swi-prolog (where it is interessant to note that [https://extix.se](https://extix.se) did offer an «emacs» in it's version I did already name above. I did renounce to preinstall the same because of consumption of disk memory in a MINIMAL "L"ubuntu because the need of disk was always to much as I did try, but, with emacs, you can make an exceptional working environment for swi-prolog, very interesting for big children or young's (I suppose that Exton did have the luck to get an Nightly build having that supplementary option realized with simple middles..)).

Please install with

APT::Install-Recommends "false";
APT::Install-Suggests "false";
APT::Get::Fix-Missing "true";
Acquire::Languages "none";
Acquire::Check-Valid-Until "false";

in a created /etc/apt/apt.conf ;-) 
(if you install with above commando lines, you can

- invoque a first time to look
- answer "no"
- cursor up
- add « > step01» etc. to the line (so you get that protocol; but without the commando line text itself) in your working dir (~)!)

so you can control later what apt would have installed without those restrictions: you have full control!!!

(you can also do it step by step and not for my above very long installations row!)

---

### Post by oui on 2024-01-28
example of protocol you get doing that:
```

sudo apt install refractainstaller-base refractasnapshot-base deborphan didiwiki clex ranger mgp abiword hunspell gnumeric gimp nted mplayer mplayer-gui tesseract-ocr gimagereader nemo
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
refractainstaller-base is already the newest version (9.6.6).
refractasnapshot-base is already the newest version (10.2.12).
deborphan is already the newest version (1.7.35).
didiwiki is already the newest version (0.5-13).
clex is already the newest version (4.6.patch8-1).
ranger is already the newest version (1.9.3-5).
The following additional packages will be installed:
  abiword-common cinnamon-desktop-data evolution-data-server-common
  gimagereader-common gimp-data gnumeric-common graphviz
  libabiword-3.0 libamd3 libann0 libatkmm-1.6-1v5 libaudio2
  libbabl-0.1-0 libcairomm-1.0-1v5 libcamd3 libcamel-1.2-64
  libccolamd3 libcdt5 libcgraph6 libcholmod5 libcinnamon-desktop4
  libcolamd3 libdv4 libebook-contacts-1.2-4 libedataserver-1.2-27
  libenca0 libenchant-2-2 libexempi8 libgail-3-0 libgegl-0.4-0
  libgegl-common libgexiv2-2 libgimp2.0 libglibmm-2.4-1v5
  libgnomekbd-common libgnomekbd8 libgoffice-0.10-10
  libgoffice-0.10-10-common libgsf-1-114 libgsf-1-common
  libgtkmm-3.0-1v5 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtksourceviewmm-3.0-0v5
  libgtkspell3-3-0 libgtkspellmm-3.0-0v5 libgts-0.7-5 libgvc6
  libgvpr2 libjack-jackd2-0 liblab-gamut1 liblept5 libmhash2
  libmypaint-1.5-1 libmypaint-common libnemo-extension1
  libopenal-data libopenal1 libots0 libpangomm-1.4-1v5 libpathplan4
  libperl4-corelibs-perl libphonenumber8 libpodofo0.9.8
  libprotobuf32 libraptor2-0 librasqal3 libraw23 librdf0
  librevenge-0.0-0 libsdl1.2debian libsdl2-2.0-0 libsndio7.0
  libsuitesparseconfig7 libtesseract5 libtidy5deb1 libumfpack6
  libvorbisidec1 libwmf-0.2-7 libwpd-0.10-10 libwpg-0.3-3
  libwv-1.2-4 libxapp1 libxklavier16 libxml++2.6-2v5 libyajl2
  nemo-data pxlib1 tesseract-ocr-eng tesseract-ocr-osd xapps-common
Suggested packages:
  gimp-help-en | gimp-help gimp-data-extras gnumeric-plugins-extra
  libgsf-1-dev graphviz-doc nas libdv-bin oss-compat
  libenchant-2-voikko jackd2 libportaudio2 raptor2-utils
  rasqal-utils librdf-storage-mysql librdf-storage-postgresql
  librdf-storage-sqlite librdf-storage-virtuoso redland-utils sndiod
  libwmf-0.2-7-gtk asiya24-vfont fonts-ipafont-gothic
  | fonts-japanese-gothic fonts-ipafont-mincho
  | fonts-japanese-mincho fonts-opensymbol texlive mplayer-doc
  netselect | fping eog totem | mp3-decoder
Recommended packages:
  abiword-plugin-grammar gnumeric-doc evince lp-solve
  fonts-liberation2 enchant-2 libgts-bin libxapp-gtk3-module
  xapp-sn-watcher sharutils mplayer-skin catdoc cinnamon-l10n exif
  gnome-disk-utility html2text id3 nemo-fileroller odt2txt
  python3-xlrd untex nted-doc
The following NEW packages will be installed:
  abiword abiword-common cinnamon-desktop-data
  evolution-data-server-common gimagereader gimagereader-common gimp
  gimp-data gnumeric gnumeric-common graphviz hunspell
  libabiword-3.0 libamd3 libann0 libatkmm-1.6-1v5 libaudio2
  libbabl-0.1-0 libcairomm-1.0-1v5 libcamd3 libcamel-1.2-64
  libccolamd3 libcdt5 libcgraph6 libcholmod5 libcinnamon-desktop4
  libcolamd3 libdv4 libebook-contacts-1.2-4 libedataserver-1.2-27
  libenca0 libenchant-2-2 libexempi8 libgail-3-0 libgegl-0.4-0
  libgegl-common libgexiv2-2 libgimp2.0 libglibmm-2.4-1v5
  libgnomekbd-common libgnomekbd8 libgoffice-0.10-10
  libgoffice-0.10-10-common libgsf-1-114 libgsf-1-common
  libgtkmm-3.0-1v5 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtksourceviewmm-3.0-0v5
  libgtkspell3-3-0 libgtkspellmm-3.0-0v5 libgts-0.7-5 libgvc6
  libgvpr2 libjack-jackd2-0 liblab-gamut1 liblept5 libmhash2
  libmypaint-1.5-1 libmypaint-common libnemo-extension1
  libopenal-data libopenal1 libots0 libpangomm-1.4-1v5 libpathplan4
  libperl4-corelibs-perl libphonenumber8 libpodofo0.9.8
  libprotobuf32 libraptor2-0 librasqal3 libraw23 librdf0
  librevenge-0.0-0 libsdl1.2debian libsdl2-2.0-0 libsndio7.0
  libsuitesparseconfig7 libtesseract5 libtidy5deb1 libumfpack6
  libvorbisidec1 libwmf-0.2-7 libwpd-0.10-10 libwpg-0.3-3
  libwv-1.2-4 libxapp1 libxklavier16 libxml++2.6-2v5 libyajl2 mgp
  mplayer mplayer-gui nemo nemo-data nted pxlib1 tesseract-ocr
  tesseract-ocr-eng tesseract-ocr-osd xapps-common
0 upgraded, 102 newly installed, 0 to remove and 0 not upgraded.
Need to get 68,3 MB of archives.
After this operation, 285 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

---

