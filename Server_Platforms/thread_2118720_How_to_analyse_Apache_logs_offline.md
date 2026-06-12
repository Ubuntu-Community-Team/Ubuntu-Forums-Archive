---
title: "How to analyse Apache logs offline?"
date: 2013-02-22
forum: Server Platforms
---

### Post by Irihapeti on 2013-02-22
I have a website with a hosting company and I regularly download the Apache logfiles so I have a copy of them.

Does anyone know of a program that I could use to analyse these logfiles, that doesn't assume that they belong to a webserver running on the same machine? Ideally, I'd like something that resembles AWStats, but any suggestions would be considered.

I'm using Ubuntu 12.04.

---

### Post by d4m1r on 2013-02-25
Do you mean the .log text files? If so, Notepad++ on Windows or Gedit work just fine...

---

### Post by tgalati4 on 2013-02-25
There's probably a few in this list:

tgalati4@Mint14-Extensa ~ $ apt-cache search log viewer analyzer
goaccess - log analyzer and interactive viewer for the Apache Webserver
tgalati4@Mint14-Extensa ~ $ apt-cache search log viewer
gnome-system-log - system log viewer for GNOME
malaga-doc - Documentation for an automatic language analysis system
texlive-base - TeX Live: Essential programs and files
x11-apps - X applications
auth2db - Powerful and eye-candy IDS logger, log viewer and alert generator
bidiv - BiDi viewer - command-line tool displaying logical Hebrew/Arabic
bppphyview - Bio++ Phylogenetic Viewer
calibre - e-book converter and library management
calibre-bin - e-book converter and library management
dialog - Displays user-friendly dialog boxes from shell scripts
dicomscope - OFFIS DICOM Viewer
figtree - graphical phylogenetic tree viewer
gdis - molecular and crystal model viewer
gelemental - Periodic Table viewer
gelemental-dbg - Periodic Table viewer (main application debugging symbols)
ginkgocadx - Medical Imaging Software and complete DICOM Viewer
goaccess - log analyzer and interactive viewer for the Apache Webserver
gthumb - image viewer and browser
gthumb-data - image viewer and browser - arch-independent files
gthumb-dbg - image viewer and browser - debugging symbols
gthumb-dev - image viewer and browser - development files
gwave - waveform viewer eg for spice simulators
konqueror - advanced file manager, web browser and document viewer
kpartsplugin - Netscape-compatible plugin to embed KDE file-viewers into browser
ksystemlog - system log viewer
laditools - Linux Audio Desktop Integration Tools
libcurses-ui-perl - curses-based OO user interface framework for Perl
libelemental-dev - Periodic Table viewer (development files)
libelemental-doc - Periodic Table viewer (API documentation)
libelemental0 - Periodic Table viewer (data and shared library)
libelemental0-dbg - Periodic Table viewer (shared library debugging symbols)
libsoqt4-dev - Qt4 GUI component toolkit for Inventor - development
mrpt-apps - Mobile Robot Programming Toolkit - Console and GUI applications
plasma-widgets-addons - additional widgets for Plasma
qbzr - Graphical interface for Bazaar using the Qt toolkit
starplot - 3-dimensional perspective star map viewer
sugar-logviewer-activity - log viewing activity on the XO laptop
swatch - Log file viewer with regexp matching, highlighting & hooks
torrentflux - web based, feature-rich BitTorrent download manager

---

### Post by Irihapeti on 2013-02-27
> **tgalati4 said:**
> There's probably a few in this list:

tgalati4@Mint14-Extensa ~ $ apt-cache search log viewer analyzer
goaccess - log analyzer and interactive viewer for the Apache Webserver
....


That looks interesting. At first glance, it looks as though it will give me most of the information I want. Thanks.

---

### Post by hydn79 on 2013-02-27
Try this: [http://www.apacheviewer.com/](http://www.apacheviewer.com/)

---

### Post by Irihapeti on 2013-02-27
> **hydn79 said:**
> Try this: [http://www.apacheviewer.com/](http://www.apacheviewer.com/)

That one is Windows only, and requires a payment if you want all the reports.

---

