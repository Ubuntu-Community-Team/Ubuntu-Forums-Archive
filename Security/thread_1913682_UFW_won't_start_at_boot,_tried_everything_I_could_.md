---
title: "UFW won't start at boot, tried everything I could find!"
date: 2012-01-23
forum: Security
---

### Post by rough60 on 2012-01-23
Hi all,  I can't get ufw to start at boot, ubuntu 11.10. This is what I've done: ```
sudo ufw enable
```  In the ufw.conf file: ```
# /etc/ufw/ufw.conf
#

# Set to yes to start on boot. If setting this remotely, be sure to add a rule
# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
ENABLED=yes

# Please use the 'ufw' command to set the loglevel. Eg: 'ufw logging medium'.
# See 'man ufw' for details.
LOGLEVEL=low
```  Also tried putting it in programs at start up
Name: ufw Command: ufw 
Name: ufw Command: enable 
Name: ufw Command: ufw enable 
 Programs I've installed:
teamviewer 
wine  
pokerstars (in wine)  
clamtk 
mythtv  
mount manager  
skype  
weather and system monitor indicators 
 dansguardian
privoxy 
  dansguardian and privoxy set up as these pages suggest by bodhi.zazen : 
 [http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/) 
 [http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)  
[http://blog.bodhizazen.net/linux/speed-up-privoxy/](http://blog.bodhizazen.net/linux/speed-up-privoxy/) 

Also I don't have firestarter or similar installed. 

Thanks for any help, Cheers

---

### Post by memilanuk on 2012-01-23
I don't think you need to put it in the programs @ startup... I'd pull it out of there if I were you.

What do you get when you type:

```
sudo ufw status
```

---

### Post by rough60 on 2012-01-23
Yeah I took them out of programs @ startup when they didn't work  this is the after boot
```
:~$ sudo ufw status
[sudo] password: 
Status: inactive 
:~$ sudo ufw enable 
Firewall is active and enabled on system startup 
:~$ sudo ufw status 
Status: active 
To                         Action      From
--                         ------      ----
8080                       DENY        Anywhere
8118                       DENY        Anywhere
192.168.1.10 8080          ALLOW       192.168.0.0/24
192.168.1.10 8118          ALLOW       192.168.0.0/24
8080                       DENY        Anywhere (v6)
8118                       DENY        Anywhere (v6)
  
```   Thanks

---

### Post by bodhi.zazen on 2012-01-25
Did you at any time install another firewall tool such as firestarter ?

---

### Post by rough60 on 2012-01-25
No I pretty sure ufw is the only firewall tool I've installed.
Here is a list of packages installed using
```
dpkg -l
```

```
ii  libzeitgeist-1 0.3.12-0ubuntu library to access Zeitgeist - shared library
ii  libzephyr4     3.0.1-1        Project Athena's notification service - non-
ii  light-themes   0.1.8.25       Light Themes (Ambiance and Radiance)
ii  lightdm        1.0.6-0ubuntu1 Display Manager
ii  linux-firmware 1.60           Firmware for Linux kernel drivers
ii  linux-firmware 1.11           Non-free firmware for Linux kernel drivers
ii  linux-generic  3.0.0.15.17    Complete Generic Linux kernel
ii  linux-generic- 3.0.0.15.17    Complete Generic Linux kernel
ii  linux-headers- 3.0.0-12.20    Header files related to Linux kernel version
ii  linux-headers- 3.0.0-12.20    Linux kernel headers for version 3.0.0 on x8
ii  linux-headers- 3.0.0-14.23    Header files related to Linux kernel version
ii  linux-headers- 3.0.0-14.23    Linux kernel headers for version 3.0.0 on x8
ii  linux-headers- 3.0.0-14.23    Linux kernel headers for version 3.0.0 on x8
ii  linux-headers- 3.0.0-15.26    Header files related to Linux kernel version
ii  linux-headers- 3.0.0-15.26    Linux kernel headers for version 3.0.0 on x8
ii  linux-headers- 3.0.0-15.26    Linux kernel headers for version 3.0.0 on x8
ii  linux-headers- 3.0.0.15.17    Generic Linux kernel headers
ii  linux-headers- 3.0.0.15.17    Generic Linux kernel headers
ii  linux-image-3. 3.0.0-12.20    Linux kernel image for version 3.0.0 on x86/
ii  linux-image-3. 3.0.0-14.23    Linux kernel image for version 3.0.0 on x86/
ii  linux-image-3. 3.0.0-14.23    Linux kernel image for version 3.0.0 on x86
ii  linux-image-3. 3.0.0-15.26    Linux kernel image for version 3.0.0 on x86/
ii  linux-image-3. 3.0.0-15.26    Linux kernel image for version 3.0.0 on x86
ii  linux-image-ge 3.0.0.15.17    Generic Linux kernel image
ii  linux-image-ge 3.0.0.15.17    Generic Linux kernel image
ii  linux-libc-dev 3.0.0-15.26    Linux Kernel Headers for development
ii  linux-sound-ba 1.0.24+dfsg-0u base package for ALSA and OSS sound systems
ii  locales        2.13+git201106 common files for locale support
ii  lockfile-progs 0.1.15ubuntu1  Programs for locking and unlocking files and
ii  login          1:4.1.4.2+svn3 system login tools
ii  logrotate      3.7.8-6ubuntu5 Log rotation utility
ii  lp-solve       5.5.0.13-7     Solve (mixed integer) linear programming pro
ii  lsb-base       4.0-0ubuntu16  Linux Standard Base 4.0 init script function
ii  lsb-release    4.0-0ubuntu16  Linux Standard Base version reporting utilit
ii  lshw           02.15-1        information about hardware configuration
ii  lsof           4.81.dfsg.1-1b List open files
ii  ltrace         0.5.3-2.1ubunt Tracks runtime library calls in dynamically 
ii  lzma           4.43-14ubuntu2 Compression method of 7z format in 7-Zip pro
ii  make           3.81-8.1ubuntu An utility for Directing compilation.
ii  makedev        2.3.1-89ubuntu creates device files in /dev
ii  man-db         2.6.0.2-2      on-line manual pager
ii  manpages       3.27-1ubuntu2  Manual pages about using a GNU/Linux system
ii  manpages-dev   3.27-1ubuntu2  Manual pages about using GNU/Linux for devel
ii  mawk           1.3.3-15ubuntu a pattern scanning and text processing langu
ii  media-player-i 15-1           Media player identification files
ii  memtest86+     4.20-1ubuntu1  thorough real-mode memory tester
ii  metacity       1:2.34.1-1ubun lightweight GTK+ window manager
ii  metacity-commo 1:2.34.1-1ubun shared files for the Metacity window manager
ii  mime-support   3.51-1ubuntu1  MIME files 'mime.types' & 'mailcap', and sup
ii  min12xxw       0.0.9-3ubuntu3 Printer driver for KonicaMinolta PagePro 1[2
ii  mlocate        0.23.1-1ubuntu quickly find files on the filesystem based o
ii  mobile-broadba 20111113-1ubun database of mobile broadband service provide
ii  modemmanager   0.5-1ubuntu1   D-Bus service for managing modems
ii  module-init-to 3.16-1ubuntu1  tools for managing Linux kernel modules
ii  mono-4.0-gac   2.10.5-1       Mono GAC tool (for CLI 4.0)
ii  mono-gac       2.10.5-1       Mono GAC tool
ii  mono-runtime   2.10.5-1       Mono runtime
ii  mount          2.19.1-2ubuntu Tools for mounting and manipulating filesyst
ii  mountall       2.31           filesystem mounting tool
ii  mountmanager   0.2.6-0ubuntu5 User-friendly management of disks and partit
ii  mousetweaks    3.2.1-0ubuntu1 mouse accessibility enhancements for the GNO
ii  mscompress     0.3-3.1        Microsoft "compress.exe/expand.exe" compatib
ii  mtools         4.0.12-1       Tools for manipulating MSDOS files
ii  mtr-tiny       0.80-1ubuntu1  Full screen ncurses traceroute tool
ii  multiarch-supp 2.13-20ubuntu5 Transitional package to ensure multiarch com
ii  myspell-en-au  2.1-5.3        English_australian dictionary for myspell
ii  myspell-en-gb  1:3.3.0-2ubunt English_british dictionary for myspell
ii  myspell-en-za  1:3.3.0-2ubunt English_southafrican dictionary for myspell
ii  mysql-client-5 5.1.58-1ubuntu MySQL database client binaries
ii  mysql-client-c 5.1.58-1ubuntu MySQL database core client binaries
ii  mysql-common   5.1.58-1ubuntu MySQL database common files, e.g. /etc/mysql
ii  mysql-server   5.1.58-1ubuntu MySQL database server (metapackage depending
ii  mysql-server-5 5.1.58-1ubuntu MySQL database server binaries and system da
ii  mysql-server-c 5.1.58-1ubuntu MySQL database server binaries
ii  mythes-en-au   2.1-5.3        Australian English Thesaurus for OpenOffice.
ii  mythes-en-us   1:3.3.0-2ubunt English Thesaurus for LibreOffice/OpenOffice
ii  mythtv         2:0.24.0+fixes A personal video recorder application (clien
ii  mythtv-backend 2:0.24.0+fixes A personal video recorder application (serve
ii  mythtv-common  2:0.24.0+fixes A personal video recorder application (commo
ii  mythtv-databas 2:0.24.0+fixes A personal video recorder application (datab
ii  mythtv-fronten 2:0.24.0+fixes A personal video recorder application (clien
ii  mythtv-transco 2:0.24.0+fixes Utilities used for transcoding MythTV tasks
ii  nano           2.2.6-1        small, friendly text editor inspired by Pico
ii  nautilus       1:3.2.1-0ubunt file manager and graphical shell for GNOME
ii  nautilus-data  1:3.2.1-0ubunt data files for nautilus
ii  nautilus-sendt 3.0.1-0ubuntu1 integrates Evolution and Pidgin into the Nau
ii  nautilus-sendt 3.2.0.1-0ubunt GNOME multi-protocol chat and call client (n
ii  nautilus-share 0.7.3-1ubuntu1 Nautilus extension to share folder using Sam
ii  ncurses-base   5.9-1ubuntu5   basic terminal type definitions
ii  ncurses-bin    5.9-1ubuntu5   terminal-related programs and man pages
ii  net-tools      1.60-23ubuntu3 The NET-3 networking toolkit
ii  netbase        4.45ubuntu3    Basic TCP/IP networking system
ii  netcat-openbsd 1.89-4ubuntu1  TCP/IP swiss army knife
ii  netpbm         2:10.0-12.2    Graphics conversion tools between image form
ii  network-manage 0.9.1.90-0ubun network management framework (daemon and use
ii  network-manage 0.9.1.90-0ubun network management framework (GNOME frontend
ii  network-manage 0.9.0-0ubuntu2 network management framework (PPTP plugin co
ii  network-manage 0.9.0-0ubuntu2 network management framework (PPTP plugin GN
ii  notify-osd     0.9.32-0ubuntu daemon that displays passive pop-up notifica
ii  notify-osd-ico 0.7            Notify-OSD icons
ii  ntfs-3g        1:2011.4.12AR. read/write NTFS driver for FUSE
ii  ntp            1:4.2.6.p2+dfs Network Time Protocol daemon and utility pro
ii  ntpdate        1:4.2.6.p2+dfs client for setting system time from NTP serv
ii  ntrack-module- 014+bzr312-0ub libnl based ntrack module
ii  nux-tools      1.16.0-0ubuntu Visual rendering toolkit for real-time appli
ii  nvidia-common  1:0.2.35       Find obsolete NVIDIA drivers
ii  obex-data-serv 0.4.6-0ubuntu1 D-Bus service for OBEX client and server sid
ii  obexd-client   0.42-0ubuntu1  D-Bus OBEX client
ii  odbcinst       2.2.14p2-2ubun Helper program for accessing odbc ini files
ii  odbcinst1debia 2.2.14p2-2ubun Support library for accessing odbc ini files
ii  onboard        0.96.1-0ubuntu Simple On-screen Keyboard
ii  oneconf        0.2.6.7        synchronize your configuration data over the
ii  openjdk-6-jre  6b23~pre11-0ub OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre- 6b23~pre11-0ub OpenJDK Java runtime, using Hotspot JIT (hea
ii  openjdk-6-jre- 6b23~pre11-0ub OpenJDK Java runtime (architecture independe
ii  openoffice.org 1:3.3.0-7ubunt office productivity suite -- arch-independen
ii  openoffice.org 0.6            Hyphenation patterns for OpenOffice.org
ii  openprinting-p 20110831-0ubun OpenPrinting printer support - PostScript PP
ii  openssh-client 1:5.8p1-7ubunt secure shell (SSH) client, for secure access
ii  openssl        1.0.0e-2ubuntu Secure Socket Layer (SSL) binary and related
ii  os-prober      1.49ubuntu1    utility to detect other OSes on a set of dri
ii  overlay-scroll 0.2.11-0ubuntu Scrollbar overlayed widget
ii  oxygen-icon-th 4:4.7.1-0ubunt Oxygen icon theme
ii  parted         2.3-6ubuntu3   disk partition manipulator
ii  passwd         1:4.1.4.2+svn3 change and administer password and group dat
ii  patch          2.6.1-2        Apply a diff file to an original
ii  pciutils       1:3.1.7-4ubunt Linux PCI Utilities
ii  pcmciautils    015-1ubuntu1   PCMCIA utilities for Linux 2.6
ii  perl           5.12.4-4       Larry Wall's Practical Extraction and Report
ii  perl-base      5.12.4-4       minimal Perl system
ii  perl-modules   5.12.4-4       Core Perl modules
ii  phonon         4:4.7.0really4 multimedia framework from KDE - metapackage
ii  phonon-backend 4:4.7.0really4 Phonon GStreamer 0.10.x backend
ii  pkg-config     0.26-1ubuntu1  manage compile and link flags for libraries
ii  plasma-scripte 4:4.7.4-0ubunt JavaScript script engine for Plasma
ii  plymouth       0.8.2-2ubuntu2 graphical boot animation and logger - main p
ii  plymouth-label 0.8.2-2ubuntu2 graphical boot animation and logger - label 
ii  plymouth-theme 0.8.2-2ubuntu2 graphical boot animation and logger - ubuntu
ii  plymouth-theme 0.8.2-2ubuntu2 graphical boot animation and logger - ubuntu
ii  pm-utils       1.4.1-8ubuntu1 utilities and scripts for power management
ii  pnm2ppa        1.13-0ubuntu1  PPM to PPA converter
ii  policykit-1    0.102-1        framework for managing administrative polici
ii  policykit-1-gn 0.102-1ubuntu1 GNOME authentication agent for PolicyKit-1
ii  policykit-desk 0.7            run common desktop actions without password
ii  poppler-utils  0.16.7-2ubuntu PDF utilities (based on Poppler)
ii  popularity-con 1.53ubuntu1    Vote for your favourite packages automatical
ii  postfix        2.8.5-2~build1 High-performance mail transport agent
ii  powermgmt-base 1.31           Common utils and configs for power managemen
ii  ppp            2.4.5-5ubuntu1 Point-to-Point Protocol (PPP) - daemon
ii  pppconfig      2.3.18+nmu2ubu A text menu based utility for configuring pp
ii  pppoeconf      1.20ubuntu1    configures PPPoE/ADSL connections
ii  pptp-linux     1.7.2-6        Point-to-Point Tunneling Protocol (PPTP) Cli
ii  privoxy        3.0.17-1       Privacy enhancing HTTP Proxy
ii  procps         1:3.2.8-10ubun /proc file system utilities
ii  protobuf-compi 2.4.0a-2ubuntu compiler for protocol buffer definition file
ii  psmisc         22.14-1        utilities that use the proc file system
ii  ptouch-driver  1.3-0ubuntu11  CUPS/Foomatic driver for Brother P-touch lab
ii  pulseaudio     1:1.0-0ubuntu3 PulseAudio sound server
ii  pulseaudio-eso 1:1.0-0ubuntu3 PulseAudio ESD compatibility layer
ii  pulseaudio-mod 1:1.0-0ubuntu3 Bluetooth module for PulseAudio sound server
ii  pulseaudio-mod 1:1.0-0ubuntu3 GConf module for PulseAudio sound server
ii  pulseaudio-mod 1:1.0-0ubuntu3 X11 module for PulseAudio sound server
ii  pulseaudio-uti 1:1.0-0ubuntu3 Command line tools for the PulseAudio sound 
ii  pwgen          2.06-1ubuntu2  Automatic Password generation
ii  pxljr          1.3-0ubuntu2   Driver for HP's Color LaserJet 35xx/36xx col
ii  python         2.7.2-7ubuntu2 interactive high-level object-oriented langu
ii  python-appindi 0.4.1-0ubuntu2 Python bindings for libappindicator
ii  python-apport  1.23-0ubuntu4  apport crash report handling library
ii  python-apt     0.8.0ubuntu9   Python interface to libapt-pkg
ii  python-apt-com 0.8.0ubuntu9   Python interface to libapt-pkg (locales)
ii  python-aptdaem 0.43+bzr697-0u Python module for the server and client of a
ii  python-aptdaem 0.43+bzr697-0u Transitional dummy package
ii  python-aptdaem 0.43+bzr697-0u Python GTK+ 3 widgets to run an aptdaemon cl
ii  python-aptdaem 0.43+bzr697-0u Python GTK+ 2 widgets to run an aptdaemon cl
ii  python-brlapi  4.2-8ubuntu5.1 Python bindings for BrlAPI
ii  python-cairo   1.8.8-1ubuntu2 Python bindings for the Cairo vector graphic
ii  python-chardet 2.0.1-2        universal character encoding detector
ii  python-configg 1.0-1          Glues together optparse.OptionParser and Con
ii  python-crypto  2.3-2          cryptographic algorithms and protocols for P
ii  python-cups    1.9.59-0ubuntu Python bindings for CUPS
ii  python-cupshel 1.3.6+20110831 Python modules for printer configuration wit
ii  python-dateuti 1.4.1-4        powerful extensions to the standard datetime
ii  python-dbus    0.84.0-2       simple interprocess messaging system (Python
ii  python-debian  0.1.20ubuntu2  Python modules to work with Debian-related d
ii  python-defer   1.0.2-0ubuntu2 Small framework for asynchronous programming
ii  python-egenix- 3.2.0-1        date and time handling routines for Python
ii  python-egenix- 3.2.0-1        collection of additional builtins for Python
ii  python-farsigh 0.0.29-1ubuntu Audio/Video communications framework: Python
ii  python-gconf   2.28.1-3       Python bindings for the GConf configuration 
ii  python-gdbm    2.7.1-3        GNU dbm database support for Python
ii  python-gnomeke 2.32.0-0ubuntu Python bindings for the GNOME keyring librar
ii  python-gnupgin 0.3.2-9.1ubunt Python interface to GnuPG (GPG)
ii  python-gobject 3.0.0-0ubuntu4 Python 2.x bindings for gobject-introspectio
ii  python-gobject 2.28.6-6svn1   deprecated static Python bindings for the GO
ii  python-gobject 3.0.0-0ubuntu4 Python Cairo bindings for the GObject librar
ii  python-gst0.10 0.10.21-2ubunt generic media-playing framework (Python bind
ii  python-gtk2    2.24.0-2       Python bindings for the GTK+ widget set
ii  python-httplib 0.7.1-1ubuntu1 comprehensive HTTP client library written fo
ii  python-ibus    1.3.99.2011041 Intelligent Input Bus - Python support
ii  python-imaging 1.1.7-3ubuntu1 Python Imaging Library
ii  python-indicat 0.6.1-0ubuntu1 Python bindings for libindicate
ii  python-keyring 0.6.2-1        store and access your passwords safely
ii  python-launchp 1.9.8-2        Launchpad web services client library
ii  python-lazr.re 0.11.2-2ubuntu client for lazr.restful-based web services
ii  python-lazr.ur 1.0.2-5        library for parsing, manipulating, and gener
ii  python-libprox 0.3.1-2ubuntu6 automatic proxy configuration management lib
ii  python-libxml2 2.7.8.dfsg-4ub Python bindings for the GNOME XML library
ii  python-louis   2.3.0-2ubuntu1 Python bindings for liblouis
ii  python-lxml    2.3-0.1build1  pythonic binding for the libxml2 and libxslt
ii  python-minimal 2.7.2-7ubuntu2 minimal subset of the Python language (defau
ii  python-mysqldb 1.2.3-0ubuntu1 A Python interface to MySQL
ii  python-notify  0.1.1-2ubuntu2 Python bindings for libnotify
ii  python-oauth   1.0.1-3        Python library implementing of the OAuth pro
ii  python-openssl 0.12-1ubuntu1  Python wrapper around the OpenSSL library
ii  python-pam     0.4.2-12.2ubun A Python interface to the PAM library
ii  python-papyon  0.5.5-1ubuntu3 MSN client library written in Python
ii  python-pexpect 2.3-1ubuntu1   Python module for automating interactive app
ii  python-piston- 0.6+bzr48-0ubu library for writing clients for Django's Pis
ii  python-pkg-res 0.6.16-1       Package Discovery and Resource Access using 
ii  python-problem 1.23-0ubuntu4  Python library to handle problem reports
ii  python-protobu 2.4.0a-2ubuntu Python bindings for protocol buffers
ii  python-psutil  0.2.1-1ubuntu1 module providing convenience functions for m
ii  python-pyatspi 2.2.1-0ubuntu1 Assistive Technology Service Provider Interf
ii  python-pycurl  7.19.0-4ubuntu Python bindings to libcurl
ii  python-pyinoti 0.9.1-1ubuntu1 simple Linux inotify Python bindings
ii  python-pywapi  0.2.2-1        Python wrapper around different weather APIs
ii  python-qt4     4.8.5-0ubuntu2 Python bindings for Qt4
ii  python-serial  2.5-2.1        pyserial - module encapsulating access for t
ii  python-simplej 2.1.6-1        simple, fast, extensible JSON encoder/decode
ii  python-sip     4.12.4-1       Python/C++ bindings generator runtime librar
ii  python-smbc    1.0.10-0ubuntu Python bindings for Samba clients (libsmbcli
ii  python-softwar 0.81.13.1      manage the repositories that you install sof
ii  python-speechd 0.7.1-6ubuntu1 Python interface to Speech Dispatcher
ii  python-support 1.0.13ubuntu1  automated rebuilding support for Python modu
ii  python-telepat 0.15.19-2.1    Python language bindings for telepathy
ii  python-twisted 11.0.0-2       Event-based framework for internet applicati
ii  python-twisted 11.0.0-2       Event-based framework for internet applicati
ii  python-twisted 11.0.0-1       A DNS protocol implementation with client an
ii  python-twisted 11.0.0-1       An HTTP protocol implementation together wit
ii  python-ubuntuo 2.0.0-0ubuntu2 Ubuntu One client Python libraries
ii  python-ubuntuo 2.0.0-0ubuntu1 Ubuntu One Control Panel Python Libraries
ii  python-ubuntuo 2.0.0-0ubuntu1 Python library for Ubuntu One file storage a
ii  python-uno     1:3.4.4-0ubunt Python-UNO bridge
ii  python-virtkey 0.60.0-0ubuntu Library to emulate keyboard keypresses.
ii  python-vte     1:0.28.2-0ubun Python bindings for the VTE widget set
ii  python-wadllib 1.2.0+ds-2     Python library for navigating WADL files
ii  python-webkit  1.1.8-2ubuntu1 WebKit/Gtk Python bindings
ii  python-wnck    2.32.0-0ubuntu Python bindings for the WNCK library
ii  python-xapian  1.2.5-2ubuntu1 Xapian search engine interface for Python
ii  python-xdg     0.19-3ubuntu1  Python library to access freedesktop.org sta
ii  python-xkit    0.4.2.3        library for the manipulation of the xorg.con
ii  python-zope.in 3.6.1-1ubuntu2 Interfaces for Python
ii  python2.7      2.7.2-5ubuntu1 An interactive high-level object-oriented la
ii  python2.7-mini 2.7.2-5ubuntu1 A minimal subset of the Python language (ver
ii  qapt-batch     1.2.1-0ubuntu2 Batch package manager for KDE
ii  qdbus          4:4.7.4-0ubunt Qt 4 Dbus Tool
ii  qt-at-spi      0.0~git2011062 accessibility plugin for Qt
ii  radeontool     1.6.1-1        utility to control ATI Radeon backlight func
ii  rarian-compat  0.8.1-5        Documentation meta-data library (compatibili
ii  rastertosag-gd 0.1-0ubuntu3   Driver for Ricoh Aficio SP1100s/SP1100s
ii  rdesktop       1.7.0-1ubuntu2 RDP client for Windows NT/2000 Terminal Serv
ii  readline-commo 6.2-2ubuntu1   GNU readline and history libraries, common f
ii  rfkill         0.4-1          tool for enabling and disabling wireless dev
ii  rkhunter       1.3.8-7        rootkit, backdoor, sniffer and exploit scann
ii  rsync          3.0.8-1ubuntu1 fast remote file copy program (like rcp)
ii  rsyslog        5.8.1-1ubuntu2 reliable system and kernel logging daemon
ii  rtkit          0.10-1ubuntu1  Realtime Policy and Watchdog Daemon
ii  ruby           4.8            Transitional package for ruby1.8
ii  ruby1.8        1.8.7.352-2    Interpreter of object-oriented scripting lan
ii  samba-common   2:3.5.11~dfsg- common files used by both the Samba server a
ii  samba-common-b 2:3.5.11~dfsg- common files used by both the Samba server a
ii  sane-utils     1.0.22-2ubuntu API library for scanners -- utilities
ii  seahorse       3.2.2-0ubuntu0 GNOME front end for GnuPG
ii  sed            4.2.1-9        The GNU sed stream editor
ii  sensible-utils 0.0.6ubuntu2   Utilities for sensible alternative selection
ii  sessioninstall 0.20+bzr120-0u APT based installer using PackageKit's sessi
ii  sgml-base      1.26+nmu1ubunt SGML infrastructure and SGML catalog file su
ii  sgml-data      2.0.6          common SGML and XML data
ii  shared-desktop 0.7.0-0ubuntu1 shared ontologies for semantic searching
ii  shared-mime-in 0.90-1ubuntu4  FreeDesktop.org shared MIME database and spe
ii  shotwell       0.11.6-0ubuntu digital photo organizer
ii  simple-scan    3.2.1-0ubuntu1 Simple Scanning Utility
ii  skype          2.2.0.35-0onei VOIP and instant messaging client
ii  smbclient      2:3.5.11~dfsg- command-line SMB/CIFS clients for Unix
ii  sni-qt         0.2.5-0ubuntu3 indicator support for Qt
ii  software-cente 5.0.4          Utility for browsing, installing, and removi
ii  software-prope 0.81.13.1      manage the repositories that you install sof
ii  software-prope 0.81.13.1      manage the repositories that you install sof
ii  soprano-daemon 2.7.4+dfsg.1-0 daemon for the Soprano RDF framework
ii  sound-theme-fr 0.7-0ubuntu2   freedesktop.org sound theme
ii  speech-dispatc 0.7.1-6ubuntu1 Common interface to speech synthesizers
ii  splix          2.0.0+20110720 Driver for Samsung's SPL2 (bw) and SPLc (col
ii  ssh-askpass-gn 1:5.8p1-7ubunt interactive X program to prompt users for a 
ii  ssl-cert       1.0.28         simple debconf wrapper for OpenSSL
ii  strace         4.5.20-2.3ubun A system call tracer
ii  sudo           1.7.4p6-1ubunt Provide limited super user privileges to spe
ii  syslinux       2:4.04+dfsg-1u collection of boot loaders
ii  syslinux-commo 2:4.04+dfsg-1u collection of boot loaders (common files)
ii  system-config- 1.3.6+20110831 Printer configuration GUI
ii  system-config- 1.3.6+20110831 Printer configuration GUI
ii  system-config- 1.3.6+20110831 Printer auto-configuration facility based on
ii  sysv-rc        2.88dsf-13.10u System-V-like runlevel change mechanism
ii  sysvinit-utils 2.88dsf-13.10u System-V-like utilities
ii  tar            1.25-3         GNU version of the tar archiving utility
ii  tcpd           7.6.q-21       Wietse Venema's TCP wrapper utilities
ii  tcpdump        4.1.1-2ubuntu2 command-line network traffic analyzer
ii  teamviewer6    6.0.9258       TeamViewer (Remote Control Application)
ii  telepathy-butt 0.5.15-2.1     MSN connection manager for Telepathy
ii  telepathy-gabb 0.13.5-0ubuntu Jabber/XMPP connection manager
ii  telepathy-haze 0.5.0-1        Telepathy connection manager that uses libpu
ii  telepathy-idle 0.1.10-1       IRC connection manager for Telepathy
ii  telepathy-indi 0.0.7-0ubuntu1 Desktop service to integrate Telepathy with 
ii  telepathy-logg 0.2.10-2       Telepathy logger service - Daemon
ii  telepathy-miss 1:5.9.1-0ubunt management daemon for Telepathy real-time co
ii  telepathy-salu 0.5.0-3ubuntu1 Link-local XMPP connection manager for the T
ii  telnet         0.17-36build1  The telnet client
ii  thunderbird    8.0+build1-0ub Email, RSS and newsgroup client with integra
ii  thunderbird-gl 8.0+build1-0ub Unity appmenu integration for Thunderbird
ii  thunderbird-gn 8.0+build1-0ub Email, RSS and newsgroup client - GNOME supp
ii  thunderbird-lo 1:8.0+build1-0 English language pack for Thunderbird
ii  thunderbird-lo 1:8.0+build1-0 Transitional English language pack for Thund
ii  thunderbird-lo 1:8.0+build1-0 Transitional English language pack for Thund
ii  time           1.7-23.1       The GNU time program for measuring cpu resou
ii  tomboy         1.8.0-1ubuntu1 desktop note taking program using Wiki style
ii  toshset        1.76-1ubuntu1  Access much of the Toshiba laptop hardware i
ii  totem          3.0.1-0ubuntu7 Simple media player for the GNOME desktop ba
ii  totem-common   3.0.1-0ubuntu7 Data files for the Totem media player
ii  totem-mozilla  3.0.1-0ubuntu7 Totem Mozilla plugin
ii  totem-plugins  3.0.1-0ubuntu7 Plugins for the Totem media player
ii  transmission-c 2.33-0ubuntu2  lightweight BitTorrent client (common files)
ii  transmission-g 2.33-0ubuntu2  lightweight BitTorrent client (GTK interface
ii  tsconf         1.0-9          touch screen library common files
ii  ttf-dejavu     2.33-1ubuntu1  Metapackage to pull in ttf-dejavu-core and t
ii  ttf-dejavu-cor 2.33-1ubuntu1  Vera font family derivate with additional ch
ii  ttf-dejavu-ext 2.33-1ubuntu1  Vera font family derivate with additional ch
ii  ttf-droid      20101110+git-1 handheld device font with extensive style an
ii  ttf-freefont   20100919-1     Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-font 1:0.5.11ubuntu Core collection of free fonts for languages 
ii  ttf-kacst-one  4.0-0ubuntu1   TrueType font designed for Arabic language
ii  ttf-khmeros-co 5.0-3ubuntu1   KhmerOS Unicode fonts for the Khmer language
ii  ttf-lao        0.0.20060226-7 TrueType font for Lao language
ii  ttf-liberation 1.07.0-1       Fonts with the same metrics as Times, Arial 
ii  ttf-mscorefont 3.3ubuntu4     Installer for Microsoft TrueType core fonts
ii  ttf-opensymbol 2:2.4.3+LibO3. OpenSymbol TrueType font
ii  ttf-punjabi-fo 1:0.5.11ubuntu Free TrueType fonts for the Punjabi language
ii  ttf-takao-pgot 003.02.01-4ubu Japanese TrueType font set, Takao P Gothic F
ii  ttf-thai-tlwg  1:0.4.15-1     Thai fonts in TrueType format
ii  ttf-ubuntu-fon 0.80-0ubuntu1~ Ubuntu Font Family, sans-serif typeface hint
ii  ttf-unfonts-co 1.0.3.is.1.0.1 Un series Korean TrueType fonts
ii  ttf-wqy-microh 0.2.0-beta-1   A droid derived Sans-Seri style CJK font
ii  tzdata         2011n-0ubuntu0 time zone and daylight-saving time data
ii  tzdata-java    2011n-0ubuntu0 time zone and daylight-saving time data for 
ii  ubuntu-artwork 54             Ubuntu themes and artwork
ii  ubuntu-desktop 1.245          The Ubuntu desktop system
ii  ubuntu-docs    11.10.5        Ubuntu Desktop Guide
ii  ubuntu-extras- 2010.09.27     GnuPG keys of the Ubuntu extras archive
ii  ubuntu-keyring 2010.+09.30    GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal 1.245          Minimal core of Ubuntu
ii  ubuntu-mono    0.0.37         Ubuntu Mono Icon theme
ii  ubuntu-restric 8              Commonly used restricted packages for Ubuntu
ii  ubuntu-sounds  0.13           Ubuntu's GNOME audio theme
ii  ubuntu-sso-cli 1.4.0-0ubuntu1 Ubuntu Single Sign-On client
ii  ubuntu-standar 1.245          The Ubuntu standard system
ii  ubuntu-system- 0.1.26         Dbus service to set various system-wide conf
ii  ubuntu-wallpap 0.32.1         Ubuntu Wallpapers
ii  ubuntuone-clie 2.0.0-0ubuntu2 Ubuntu One client
ii  ubuntuone-clie 2.0.1-0ubuntu2 Ubuntu One client GNOME integration
ii  ubuntuone-cont 2.0.0-0ubuntu1 Ubuntu One Control Panel
ii  ubuntuone-cont 2.0.0-0ubuntu1 Ubuntu One Control Panel
ii  ubuntuone-couc 0.3.0-0ubuntu2 Ubuntu One CouchDB
ii  ubuntuone-inst 2.0.0-0ubuntu1 Ubuntu One Installer
ii  ucf            3.0025+nmu2ubu Update Configuration File: preserve user cha
ii  udev           173-0ubuntu4.1 rule-based device node and kernel event mana
ii  udisks         1.0.4-1        storage media interface
ii  ufw            0.30.1-2ubuntu program for managing a Netfilter firewall
ii  unattended-upg 0.73ubuntu1    automatic installation of security upgrades
ii  unhide         20110113-2     Forensic tool to find hidden processes and p
ii  unhide.rb      13-1           Forensic tool to find processes hidden by ro
ii  unity          4.24.0-0ubuntu Interface designed for efficiency of space a
ii  unity-2d       4.12.0-0ubuntu Unity interface for non-accelerated graphics
ii  unity-2d-launc 4.12.0-0ubuntu Unity 2D Launcher
ii  unity-2d-panel 4.12.0-0ubuntu Unity 2D Panel
ii  unity-2d-place 4.12.0-0ubuntu Unity 2D Places
ii  unity-2d-sprea 4.12.0-0ubuntu Unity 2D Spread
ii  unity-asset-po 0.8.22-0ubuntu Unity Assets Pool
ii  unity-common   4.24.0-0ubuntu Common files for the Unity interface.
ii  unity-greeter  0.1.1-0ubuntu1 Unity Greeter
ii  unity-lens-app 0.4.12-0ubuntu Application lens for unity
ii  unity-lens-fil 0.6.12-0ubuntu File lens for unity
ii  unity-lens-mus 0.2.6-0ubuntu2 Music lens for unity
ii  unity-scope-mu 0.2.6-0ubuntu2 Store music lens for unity
ii  unity-services 4.24.0-0ubuntu Services for the Unity interface
ii  uno-libs3      3.4.4-0ubuntu1 LibreOffice UNO runtime environment -- publi
ii  unrar          1:4.0.3-1      Unarchiver for .rar files (non-free version)
ii  unzip          6.0-4ubuntu1   De-archiver for .zip files
ii  update-inetd   4.38+nmu1      inetd configuration file updater
ii  update-manager 1:0.152.25.5   GNOME application that manages apt updates
ii  update-manager 1:0.152.25.5   manage release upgrades
ii  update-notifie 0.117ubuntu3.1 Daemon which notifies about package updates
ii  update-notifie 0.117ubuntu3.1 Files shared between update-notifier and oth
ii  upower         0.9.13-1       abstraction for power management
ii  upstart        1.3-0ubuntu11  event-based init daemon
ii  ure            3.4.4-0ubuntu1 LibreOffice UNO runtime environment
ii  ureadahead     0.100.0-11     Read required files in advance
ii  usb-creator-co 0.2.34         create a startup disk using a CD or disc ima
ii  usb-creator-gt 0.2.34         create a startup disk using a CD or disc ima
ii  usb-modeswitch 1.1.9-1ubuntu3 mode switching tool for controlling "flip fl
ii  usb-modeswitch 20110805-1     mode switching data for usb-modeswitch
ii  usbmuxd        1.0.7-1        USB multiplexor daemon for iPhone and iPod T
ii  usbutils       1:001-1        Linux USB utilities
ii  util-linux     2.19.1-2ubuntu Miscellaneous system utilities
ii  uuid-runtime   2.19.1-2ubuntu runtime components for the Universally Uniqu
ii  vbetool        1.1-2ubuntu1   run real-mode video BIOS code to alter hardw
ii  vim-common     2:7.3.154+hg~7 Vi IMproved - Common files
ii  vim-tiny       2:7.3.154+hg~7 Vi IMproved - enhanced vi editor - compact v
ii  vinagre        3.2.1-0ubuntu1 remote desktop client for the GNOME Desktop
ii  vino           3.2.0-0ubuntu1 VNC server for GNOME
ii  virtuoso-minim 6.1.3+dfsg1-1u high-performance database - core dependency 
ii  virtuoso-opens 6.1.3+dfsg1-1u high-performance database - binaries
ii  virtuoso-opens 6.1.3+dfsg1-1u high-performance database - common files
ii  vlc            1.1.12-2~oneir multimedia player and streamer
ii  vlc-data       1.1.12-2~oneir Common data for VLC
ii  vlc-nox        1.1.12-2~oneir multimedia player and streamer (without X su
ii  vlc-plugin-not 1.1.12-2~oneir LibNotify plugin for VLC
ii  vlc-plugin-pul 1.1.12-2~oneir PulseAudio plugin for VLC
ii  wamerican      6-3            American English dictionary words for /usr/s
ii  wbritish       6-3            British English dictionary words for /usr/sh
ii  wget           1.12-3.1ubuntu retrieves files from the web
ii  whiptail       0.52.11-2ubunt Displays user-friendly dialog boxes from she
ii  whois          5.0.11ubuntu2  an intelligent whois client
ii  winbind        2:3.5.11~dfsg- Samba nameservice integration server
ii  wine1.3        1.3.37-0ubuntu Microsoft Windows Compatibility Layer (Binar
ii  wine1.3-gecko  1.4.0+1        Microsoft Windows Compatibility Layer (Web B
ii  winetricks     0.0+20110629   Microsoft Windows Compatibility Layer (winet
ii  wireless-crda  1.14           Wireless Central Regulatory Domain Agent
ii  wireless-tools 30~pre9-5ubunt Tools for manipulating Linux Wireless Extens
ii  wmctrl         1.07-6         control an EWMH/NetWM compatible X Window Ma
ii  wodim          9:1.1.11-1ubun command line CD/DVD writing tool
ii  wpasupplicant  0.7.3-3.1      client support for WPA and WPA2 (IEEE 802.11
ii  x-ttcidfont-co 32+nmu2        TrueType and CID fonts configuration for X
ii  x11-apps       7.6+4ubuntu2   X applications
ii  x11-common     1:7.6+7ubuntu7 X Window System (X.Org) infrastructure
ii  x11-session-ut 7.6+1ubuntu1   X session utilities
ii  x11-utils      7.6+3          X11 utilities
ii  x11-xfs-utils  7.6+1          X font server utilities
ii  x11-xkb-utils  7.6+4          X11 XKB utilities
ii  x11-xserver-ut 7.6+3          X server utilities
ii  xauth          1:1.0.6-1      X authentication utility
ii  xbitmaps       1.1.1-1        Base X bitmaps
ii  xcftools       1.0.7-2ubuntu1 command-line tools for extracting data for X
ii  xcursor-themes 1.0.3-1        Base X cursor themes
ii  xdg-user-dirs  0.14-0ubuntu1  tool to manage well known user directories
ii  xdg-user-dirs- 0.8-1ubuntu2   tool to manage well known user directories (
ii  xdg-utils      1.1.0~rc1-2ubu desktop integration utilities from freedeskt
ii  xdiagnose      1.6            X.org diagnosis tool
ii  xfonts-base    1:1.0.3        standard fonts for X
ii  xfonts-encodin 1:1.0.4-1      Encodings for X.Org fonts
ii  xfonts-mathml  4ubuntu1       Type1 Symbol font for MathML
ii  xfonts-scalabl 1:1.0.3-1      scalable fonts for X
ii  xfonts-utils   1:7.6+1        X Window System font utility programs
ii  xinit          1.3.1-1        X server initialisation tool
ii  xinput         1.5.3-2ubuntu1 Runtime configuration and test of XInput dev
ii  xkb-data       2.3-1ubuntu2   X Keyboard Extension (XKB) configuration dat
ii  xml-core       0.13           XML infrastructure and XML catalog file supp
ii  xorg           1:7.6+7ubuntu7 X.Org X Window System
ii  xorg-docs-core 1:1.6-1ubuntu2 Core documentation for the X.org X Window Sy
ii  xserver-common 2:1.10.4-1ubun common files used by various X servers
ii  xserver-xorg   1:7.6+7ubuntu7 X.Org X server
ii  xserver-xorg-c 2:1.10.4-1ubun Xorg X server - core server
ii  xserver-xorg-i 1:7.6+7ubuntu7 X.Org X server -- input driver metapackage
ii  xserver-xorg-i 1:2.6.0-1ubunt X.Org X server -- evdev input driver
ii  xserver-xorg-i 1:1.7.1-1      X.Org X server -- mouse input driver
ii  xserver-xorg-i 1.4.1-1ubuntu2 Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-i 1:12.7.0-2     X.Org X server -- VMMouse input driver to us
ii  xserver-xorg-i 1:0.11.0-0ubun X.Org X server -- Wacom input driver
ii  xserver-xorg-v 1:7.6+7ubuntu7 X.Org X server -- output driver metapackage
ii  xserver-xorg-v 1:6.14.99~git2 X.Org X server -- AMD/ATI display driver wra
ii  xserver-xorg-v 1:1.3.2-2ubunt X.Org X server -- Cirrus display driver
ii  xserver-xorg-v 1:0.4.2-3ubunt X.Org X server -- fbdev display driver
ii  xserver-xorg-v 2.11.12-2      X.Org X server -- Geode GX2/LX display drive
ii  xserver-xorg-v 2:2.15.901-1ub X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-v 6.9.0-1        X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-v 1:1.4.13.dfsg- X.Org X server -- MGA display driver
ii  xserver-xorg-v 1:1.2.5-2      X.Org X server -- Neomagic display driver
ii  xserver-xorg-v 1:0.0.16+git20 X.Org X server -- Nouveau display driver (ex
ii  xserver-xorg-v 1:0.2.904+svn9 X.Org X server -- VIA display driver
ii  xserver-xorg-v 0.0.14-1       X.Org X server -- QXL display driver
ii  xserver-xorg-v 6.8.1-5        X.Org X server -- ATI r128 display driver
ii  xserver-xorg-v 1:6.14.99~git2 X.Org X server -- AMD/ATI Radeon display dri
ii  xserver-xorg-v 1:0.6.3-4      X.Org X server -- legacy S3 display driver
ii  xserver-xorg-v 1:2.3.2-3ubunt X.Org X server -- Savage display driver
ii  xserver-xorg-v 1:1.7.5-1      X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-v 1:0.10.3-3     X.Org X server -- SiS display driver
ii  xserver-xorg-v 1:0.9.4-2      X.Org X server -- SiS USB display driver
ii  xserver-xorg-v 1:1.4.3-4      X.Org X server -- tdfx display driver
ii  xserver-xorg-v 1:1.3.4-2      X.Org X server -- Trident display driver
ii  xserver-xorg-v 1:2.3.0-7      X.Org X server -- VESA display driver
ii  xserver-xorg-v 1:11.0.3-2     X.Org X server -- VMware display driver
ii  xterm          271-1ubuntu2   X terminal emulator
ii  xul-ext-ubufox 1.0.2-0ubuntu0 Ubuntu-specific configuration defaults and a
ii  xz-utils       5.0.0-2        XZ-format compression utilities
ii  yelp           3.2.0-0ubuntu1 Help browser for GNOME
ii  yelp-xsl       3.2.0-0ubuntu1 XSL stylesheets for the yelp help browser
ii  zeitgeist      0.8.2-1        event logging framework
ii  zeitgeist-core 0.8.2-1        event logging framework - engine
ii  zeitgeist-data 0.7.0-0ubuntu4 event logging framework - passive logging da
ii  zeitgeist-exte 0.0.13-0ubuntu Extensions for zeitgeist engine - fts extens
ii  zenity         3.2.0-0ubuntu1 Display graphical dialog boxes from shell sc
ii  zenity-common  3.2.0-0ubuntu1 Display graphical dialog boxes from shell sc
ii  zip            3.0-4          Archiver for .zip files
ii  zlib1g         1:1.2.3.4.dfsg compression library - runtime
```

---

### Post by rough60 on 2012-01-25
Also I haven't installed then uninstalled any packages.
Cheers

---

### Post by rough60 on 2012-01-27
> Also I haven't installed then uninstalled any packages.
Cheers

Bump

---

### Post by rough60 on 2012-01-28
I noticed this comes up when i enable ufw in terminal

```
ERROR: problem running ufw-init
```

then when i enable again straight away it enables no problem

---

### Post by rough60 on 2012-01-28
Also could a service or something that starts after ufw is enabled at boot be turning it off?

---

### Post by rough60 on 2012-02-01
any ideas?
still can't get ufw to start on boot
cheers

---

### Post by bodhi.zazen on 2012-02-01
I suggest you file a bug report =)

---

### Post by rough60 on 2012-02-19
Ok I tried setting up another laptop following the same process.

UFW would be enabled at boot until I got to step 5 of bodhi's setup in this blog:
[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

I don't think I need to do step 5 when using UFW and this may have caused a conflict or something.

How do I reverse the iptable changes to see if that helps.

Thanks,
Tony.

---

### Post by kevdog on 2012-02-19
sudo iptables -F
sudo iptables -X

I believe this flushes all the rules.

check with
sudo iptables -L

---

### Post by rough60 on 2012-04-17
Still having problems with this :(

Lodged a bug report but the solution was to just load it into startup programs, which doesn't work.

Any more ideas?

Thanks

---

### Post by darkod on 2012-04-17
If you have any errors in the rules the loading is stopped (which is very bad in remote servers). Have you double checked that there are no messages about bad rules?

Is this a local or remote server over SSH?

EDIT: I just read the whole thread, you post #8 is exactly what I am talking about. The message about init not being able to be run means syntax error in one of the rules, in which cases enabling the firewall stops.

If you don't mind, post your rules if you have entered anything in before.rules and after.rules.

---

### Post by rough60 on 2012-04-18
Thanks Darko!

I was copying the before rules across and noticed and error in the before rules.
I had a typo of the owner in the *nat part.

Cheers

---

### Post by rough60 on 2012-04-20
Ok this is not solved after all!

Here is the before and after rules

Thanks

```
 #
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
#-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT

# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT

# Rules for Dansguardian

-A ufw-before-output -m owner --uid-owner root -j ACCEPT
-A ufw-before-output -p tcp -m multiport --dports 80,443 -m owner --uid-owner privoxy -j ACCEPT
-A ufw-before-output -p tcp -m multiport --dports 80,443 -j DROP
-A ufw-before-output -o lo -p tcp -m tcp --dport 8080 -m owner --uid-owner dansguardian -j ACCEPT
-A ufw-before-output -o lo -p tcp -m tcp --dport 8118 -m owner --uid-owner luke -j ACCEPT
-A ufw-before-output -o lo -p tcp -m tcp --dport 8118 -j DROP
-A ufw-before-output -o lo -j ACCEPT

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A OUTPUT -p tcp -m tcp --dport 80,443 -m owner --uid-owner root -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 80,443 -m owner --uid-owner luke -j REDIRECT --to-port 8118
-A OUTPUT -p tcp -m tcp --dport 8080 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080
-A OUTPUT -p tcp -m tcp --dport 80,443 -m owner ! --uid-owner privoxy -j REDIRECT --to-port 8080

# don’t delete the ‘COMMIT’ line or these rules won’t be processed
COMMIT



```

```
# rules.input-after
#
# Rules that should be run after the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-after-input
#   ufw-after-output
#   ufw-after-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-after-input - [0:0]
:ufw-after-output - [0:0]
:ufw-after-forward - [0:0]
# End required lines

# don't log noisy services by default
-A ufw-after-input -p udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 68 -j ufw-skip-to-policy-input

# don't log noisy broadcast
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT



```

---

### Post by darkod on 2012-04-20
I can't notice anything wrong, but I am not that familiar with the exact syntax rules. You are using a lot of -m options and I haven't used them at all so I am not sure i can spot an error if there is one.

One idea, in the *nat section in before.rules double check the rules used with ! whether the syntax is good.

Another option, if all else fails, comment out rule by rule (the ones you added, ignore the default ones), and see when the message about the init error goes away. There are not that many rules to test.

---

