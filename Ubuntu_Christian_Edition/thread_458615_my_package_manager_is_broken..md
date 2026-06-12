---
title: "my package manager is broken."
date: 2007-05-29
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-05-29
**Ok, never mind this thread.  It was a problem of trying to install Virtual Box.**

Ok, I don't think I did anything weird.  I was going to install Virtual Box, and went to install some dependencies, and it wouldn't let me.  Then it asked me to run ```
sudo aptitude install -f 
```  So I did that, and here is what I get ```

sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  about-ubuntu-ce dansguardian-gui-ubuntu esword-ubuntu gyachi 
  internet-explorer-6-ubuntu libwxgtk2.4-1 linux-headers-generic 
  linux-image-generic linux-restricted-modules-generic ntfs-3g ntfsprogs 
  theword-ubuntu ubuntu-ce-installer vlc-nox 
The following NEW packages will be installed:
  bug-buddy libxalan110 libxerces27 nfs-user-server 
The following packages will be REMOVED:
  alien biblememorizer blast bsc cvs dansguardian debhelper dialog 
  dvdauthor emelfm ffmpeg firehol fuse-utils g-wrap gambas-gb-qt 
  gambas-runtime gawk gettext gnucash gnucash-common gocr gpaint 
  gsfonts-other gstreamer0.8-a52dec gstreamer0.8-mpeg2dec guile-1.6 
  guile-1.6-dev guile-1.6-slib guile-g-wrap guile-library html2text 
  imagemagick imlib-base imlib11 intltool-debian kfilereplace kino kinoplus 
  klinkstatus kommander krusader lame libavcodec0d libavformat0d 
  libbeecrypt6 libcrypt-ssleay-perl libcvsservice0 libdate-manip-perl 
  libdc1394-13 libesmtp5 libfame-0.9 libffi4 libffi4-dev 
  libfinance-quote-perl libfuse2 libglib1.2 libgpgme11 libgsf-gnome-1-114 
  libgstreamer0.8-0 libgtk1.2 libgtk1.2-common libgwrap-runtime0 
  libgwrap-runtime0-dev libhtml-tableextract-perl libkjsembed1 libkonq4 
  libmcrypt4 libmikmod2 libncurses5-dev libnetpbm10 libntfs-3g0 libofx3 
  libosp5 libpostproc0d libpvm3 libreadline5-dev librpm4 libsvga1 
  libtidy-0.99-0 linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 
  mc mjpegtools mpeg2dec nfs-kernel-server openclipart 
  openclipart-openoffice.org openclipart-png openclipart-svg opera 
  oss-compat picasa po-debconf psfontmgr python2.4 python2.4-minimal quanta 
  quanta-data rpm sabre-common samba screem slib sox subtitleripper 
  sword-text-kjv t1-xfree86-nonfree tidy tinyproxy toolame transcode 
  ttf-dustin ttf-f500 ttf-isabella ttf-larabie-deco ttf-larabie-straight 
  ttf-larabie-uncommon ttf-staypuft ttf-summersby ttf-ubuntu-title 
  ttf-xfree86-nonfree ubuntu-restricted-extras vorbis-tools xfonts-artwiz 
  xfonts-intl-european xmms xracer xracer-tools xsabre xteddy 
0 packages upgraded, 4 newly installed, 132 to remove and 0 not upgraded.
Need to get 1573kB/2666kB of archives. After unpacking 853MB will be freed.
The following packages have unmet dependencies:
  about-ubuntu-ce: Depends: gambas-runtime but it is not installable
                   Depends: gambas-gb-qt but it is not installable
  linux-headers-generic: Depends: linux-headers-2.6.20-16-generic but it is not installable
  libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
  internet-explorer-6-ubuntu: Depends: gambas-runtime but it is not installable
                              Depends: gambas-gb-qt but it is not installable
  linux-image-generic: Depends: linux-image-2.6.20-16-generic but it is not installable
  theword-ubuntu: Depends: gambas-runtime but it is not installable
                  Depends: gambas-gb-qt but it is not installable
  vlc-nox: Depends: libavcodec0d (>= 0.cvs20060823) but it is not installable
           Depends: libavformat0d (>= 0.cvs20060823) but it is not installable
           Depends: libdc1394-13 but it is not installable
           Depends: libpostproc0d (>= 0.cvs20060823) but it is not installable
  dansguardian-gui-ubuntu: Depends: dansguardian but it is not installable
                           Depends: gambas-runtime but it is not installable
                           Depends: gambas-gb-qt but it is not installable
                           Depends: tinyproxy but it is not installable
  esword-ubuntu: Depends: gambas-runtime but it is not installable
                 Depends: gambas-gb-qt but it is not installable
  ubuntu-ce-installer: Depends: gambas-runtime but it is not installable
                       Depends: gambas-gb-qt but it is not installable
  ntfsprogs: Depends: libfuse2 (>= 2.6) but it is not installable
             Depends: fuse-utils (> 2.5.0) but it is not installable
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.20-16-generic but it is not installable
  gyachi: Depends: libglib1.2 (>= 1.2.0) but it is not installable
          Depends: libgpgme11 (>= 1.0.1) but it is not installable
          Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
          Depends: libmcrypt4 but it is not installable
          Depends: xmms (>= 1.2.10+cvs20060429) but it is not installable
  ntfs-3g: Depends: libfuse2 (>= 2.6) but it is not installable
           Depends: libntfs-3g0 (>= 1.0) but it is not installable
           PreDepends: fuse-utils but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
dansguardian-gui-ubuntu
vlc
vlc-nox

Keep the following packages at their current version:
fuse-utils [2.6.3-1ubuntu2 (feisty, now)]
gambas-gb-qt [1.0.15-1.2ubuntu1 (feisty, now)]
gambas-runtime [1.0.15-1.2ubuntu1 (feisty, now)]
imagemagick [7:6.2.4.5.dfsg1-0.14 (feisty, now)]
libfuse2 [2.6.3-1ubuntu2 (feisty, now)]
libglib1.2 [1.2.10-17build1 (feisty, now)]
libgpgme11 [1.1.2-2ubuntu2 (feisty, now)]
libgtk1.2 [1.2.10-18 (feisty, now)]
libgtk1.2-common [1.2.10-18 (feisty, now)]
libmcrypt4 [2.5.7-5 (feisty, now)]
libmikmod2 [3.1.11-a-6ubuntu3 (feisty, now)]
libntfs-3g0 [1:1.328-1 (feisty, now)]
linux-image-2.6.20-16-generic [2.6.20-16.28 (feisty-security, now)]
linux-restricted-modules-2.6.20-16-generic [2.6.20.5-16.28 (feisty-security,
now)]
oss-compat [0.0.4 (feisty, now)]
psfontmgr [0.11.10 (feisty, now)]
sword-text-kjv [2.3-1 (feisty, now)]
xmms [1:1.2.10+20061201-1ubuntu3 (feisty, now)]

Downgrade the following packages:
linux-headers-generic [2.6.20.16.28.1 (feisty-security, now) -> 2.6.20.15.14
(feisty)]

Leave the following dependencies unresolved:
file-roller recommends rpm
Score is -1818

```

Ok, this is weird, when I run ```

sudo apt-get install -f
```  here is the results that looks less problematic!
```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxalan110 libxerces27
Suggested packages:
  xalan
The following NEW packages will be installed:
  libxalan110 libxerces27
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1321kB/2414kB of archives.
After unpacking 8577kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```  

Anyone know why I get such different responses? 

I really don't understand what caused this conflict.  The other day I did have a kernel upgrade, is it not compatible with Ubuntu CE?  Any ideas on what to do?  If I don't hear something, I may just try something and see what I can come up with.  But it would be nice to have some input of others that may actually be able to interpret this jumble.  :)  Thanks.

Shane

---

