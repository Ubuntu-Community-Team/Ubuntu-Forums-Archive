---
title: "Chromium OS compiled - VMWare image made"
date: 2009-11-19
forum: The Cafe
---

### Post by jmmL on 2009-11-19
Decided to have a go at compiling chromiumOS. It's pretty basic, but that's the philosophy behind it. I converted it to a .vmdk and booted it using VirtualBox. I've attached some screenshots for everyone to see.

You have to log in with your gmail account, which foxed me for a few seconds. Didn't time the boot - will do that now. I can upload the vmware disk to rapidshare if there's demand and if I research how to split things across multiple archives. (I can't torrent it before anyone asks).

[SIZE=3]*Download the vmdk:*[/SIZE]
I've 7zipped ide.vmdk and as a result it's much, much smaller. Unfortunately I've still had to split it across two archives, but that's still better than four! I'd recommend you use these.
[http://rapidshare.com/files/310240546/ide.vmdk.7z.001](http://rapidshare.com/files/310240546/ide.vmdk.7z.001)
[http://rapidshare.com/files/310241525/ide.vmdk.7z.002](http://rapidshare.com/files/310241525/ide.vmdk.7z.002)
~245MB total.

Old links in case anyone still needs them.
[http://rapidshare.com/files/309484345/chromiumOS-1.tar](http://rapidshare.com/files/309484345/chromiumOS-1.tar)
[http://rapidshare.com/files/309485808/chromiumOS-2.tar](http://rapidshare.com/files/309485808/chromiumOS-2.tar)
[http://rapidshare.com/files/309487192/chromiumOS-3.tar](http://rapidshare.com/files/309487192/chromiumOS-3.tar)
[http://rapidshare.com/files/309488963/chromiumOS-4.tar](http://rapidshare.com/files/309488963/chromiumOS-4.tar)
~720MB total.


*Other sources:*
[SIZE=1]I can't personally vouch for any of these - they aren't images that I have personally built.[/SIZE]
[Torrent at the pirate bay]("https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2") - much smaller than mine - it's been bziped to 280MB (I wish rapidshare would allow larger uploads!)
[Direct download from gdgt]("http://gdgt.com/google/chrome-os/download/") - registration (free) required.
Both sources via [this techcrunch article]("http://www.techcrunch.com/2009/11/19/guide-install-google-chrome-os/"), found by themusicalduck.

[SIZE=3]*Instructions*[/SIZE]
You'll need to extract the vmdk first. Here's what you'll see, with what you need to type in bold:
     ```
:~$ **tar -x -M --file=chromiumOS-1.tar ide.vmdk**
Prepare volume #2 for `chromiumOS.tar' and hit return: **n chromiumOS-2.tar**
Prepare volume #3 for `chromiumOS-2.tar' and hit return: **n chromiumOS-3.tar**
Prepare volume #4 for `chromiumOS-3.tar' and hit return: **n chromiumOS-4.tar**
```[I]

[SIZE=3]Timings[/SIZE][/I]
I make it about 11 seconds from boot to log-in screen.
Then about 16 from log-in to a fully loaded gmail, which is the default state. I can confirm that it remembers which tabs were open and which one you were viewing between reboot cycles.
~4 seconds to shut down. There isn't actually a shut-down button (unless I'm being dense), so I did this via vb's "send shutdown signal" command. 
Remember that this is all in a virtual machine, on under-powered hardware and on rotating media. I wasn't expecting 7 second boots!

[SIZE=3]*Browser Tidbits*[/SIZE]
Here's the user agent string:```
Mozilla/5.0 (X11; U; CrOS i686 9.10.0; en-US) AppleWebKit/532.5 (KHTML, like Gecko) Chrome/4.0.253.0 Safari/532.5
```It scores 100/100 in acid3, but with that pink "X" in the top right-hand corner. **Flash** seems to be working. I've only tested youtube - it was jerky (probably just virtual machine) and I didn't test sound, but video appeared to be working at ~3fps.

[SIZE=3]*Mouse and Keyboard*[/SIZE]
The keyboard defaults to en-US. There are touchpad sensitivity sliders if you click the clock and then "Open time and date options". This is where all the other options are kept for the time being as well. There is quite a cool pointer icon when hovering over links. There are multiple keyboard shortcuts. A schematic of them can be obtained by pressing F8. See [#39]("http://ubuntuforums.org/showpost.php?p=8352797&postcount=39") for shots.
[I]
[SIZE=3]Do-it-yourself[/SIZE][/I]
The guys working on this at Google have some brilliant documentation to go along with it. It was really, really easy to follow their instructions. Everything worked fine on an up-to-date karmic install.
Here's the page that'll get you started building: [http://www.chromium.org/chromium-os/building-chromium-os](http://www.chromium.org/chromium-os/building-chromium-os)
Here are the prerequisites: [http://code.google.com/p/chromium/wiki/LinuxBuildInstructionsPrerequisites](http://code.google.com/p/chromium/wiki/LinuxBuildInstructionsPrerequisites) - but they have a neat script to grab all the dependencies for you.
Here are the actual build instructions, including guidance on how to turn your image into a vmdk, put it on a USB stick, and convert your hard-drive over to chromeOS!
[http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions](http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions)

[SIZE=3]*We have root*[/SIZE]
In hindsight, I probably should have tried this earlier. Take a look at the dev FAQ: [http://www.chromium.org/chromium-os/how-tos-and-troubleshooting/developer-faq#TOC-Shortcut-Keys](http://www.chromium.org/chromium-os/how-tos-and-troubleshooting/developer-faq#TOC-Shortcut-Keys)
Those shortcut keys are a gold-mine! Ctrl + alt + T will open you up a terminal in a new window. Haven't really tried much yet. Sudo works though - the password for my build is chromium05. We've also got alt-tabbing through windows. Screenshots for proof in a new post - darn the 5 attachment limit!

[SIZE=3]*System information*[/SIZE]
Most of this section is now in [post #3]("http://ubuntuforums.org/showpost.php?p=8351782&postcount=3").
As expected the root file system is read-only. Because /var/lib/dpkg/lock exists apt-get won't install any packages. However, because we have super-user privileges, we can simply remount the root filesystem to be writable.```
sudo mount -o remount,rw /
```Now we can do pretty much whatever we want!

[SIZE=3]*Making a USB image*[/SIZE]
Some people have requested the mbr.image and/or the rootfs.image, so that they can make a USB image.
Here is the mbr.image:
[http://rapidshare.com/files/310321805/mbr.image](http://rapidshare.com/files/310321805/mbr.image)
It's 512 bytes. md5: 69f612ef469475f8c4a086d1ae21bca0

and here's the build folder (hence the odd name) 7zipped up:
[http://rapidshare.com/files/310326848/999.999.32409.013733-a1.7z.001](http://rapidshare.com/files/310326848/999.999.32409.013733-a1.7z.001)
[http://rapidshare.com/files/310327598/999.999.32409.013733-a1.7z.002](http://rapidshare.com/files/310327598/999.999.32409.013733-a1.7z.002)
~245MB total.

If you've got the scripts that google has provided, then I think it should be a simple matter of running *image_to_usb.sh* - but I haven't tried this myself.

---

### Post by Shpongle on 2009-11-19
il seed it !, cant promise il always be on but il be happy to seed along with #! and karmic, and give back!

---

### Post by jmmL on 2009-11-19
I've reached my attachment limit on the first post. Here's a shot of the memory manager (pretty much like chromium-browser I think). This guest is running with 768MB of RAM and 128MB video memory. The host is a laptop - T5450 1.6GHz (no Intel VT-x), 2GB RAM, rotating media and a nVidia 8600M 512MB. The vmdk is about 720MB.

I removed this bit from the first post; it was cluttering things up.
[SIZE=3]*System information*[/SIZE]
Here's the output of dpkg -l```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                      Version                                 Description
+++-=========================================-=======================================-============================================
ii  acpid                                     1.0.6-9ubuntu5                          Utilities for using ACPI power management
ii  adduser                                   3.110ubuntu6                            add and remove users and groups
ii  alsa-base                                 1.0.20+dfsg-1ubuntu4                    ALSA driver configuration files
ii  alsa-utils                                1.0.20-2ubuntu1                         ALSA utilities
ii  apt                                       0.7.21ubuntu1                           Advanced front-end for dpkg
ii  apt-utils                                 0.7.21ubuntu1                           APT utility programs
ii  aptitude                                  0.4.11.11-1ubuntu4                      terminal-based package manager
ii  base-files                                5.0.0ubuntu6                            Debian base system miscellaneous files
ii  base-passwd                               3.5.21                                  Debian base system master password and group
ii  bash                                      3.2-5ubuntu2                            The GNU Bourne Again SHell
ii  bootchart                                 0.90.1-3                                boot sequence auditing
ii  bootchart-java                            0.10~svn407-3ubuntu1                    Boot process performance analyser (visualisa
ii  bsdutils                                  1:2.16-1ubuntu1                         Basic utilities from 4.4BSD-Lite
ii  busybox-initramfs                         1:1.13.3-1ubuntu5                       Standalone shell setup for initramfs
ii  bzip2                                     1.0.5-3                                 high-quality block-sorting file compressor -
ii  ca-certificates                           20090701                                Common CA certificates
ii  ca-certificates-java                      20090629                                Common CA certificates (JKS keystore)
ii  chromeos-assets                           0.3                                     Chrome OS platform assets
ii  chromeos-chrome                           0.1                                     chromeos chrome
ii  chromeos-connman                          0.3                                     connman
ii  chromeos-cryptohome                       0.1                                     Helper scripts which smooth the integration 
ii  chromeos-init                             0.3                                     Chrome OS init scripts
ii  chromeos-installer                        0.1                                     Chrome OS installer
ii  chromeos-libcros                          0.1                                     Chrome OS plug-in library for Chrome
ii  chromeos-login                            0.4                                     Chrome OS login manager
ii  chromeos-monitor-reconfig                 0.1                                     Small module that will reconfigure an extern
ii  chromeos-pam-google                       0.10                                    Linux-PAM module to authenticate against Goo
ii  chromeos-ply-image                        0.1                                     Chrome OS boot splash image loader.
ii  chromeos-screenlocker                     1.0-1                                   Screen locker configuration for Chrome OS.  
ii  chromeos-wm                               0.4                                     Chrome OS window manager
ii  chromeos-wpasupplicant                    0.1                                     wpasupplicant
ii  console-setup                             1.34ubuntu1                             console font and keymap setup program
ii  console-terminus                          4.28-1                                  Fixed-width fonts for fast reading on the Li
ii  consolekit                                0.3.1-0ubuntu1                          framework for defining and tracking users, s
ii  coreutils                                 7.4-2                                   The GNU core utilities
ii  cpio                                      2.10-1ubuntu1                           GNU cpio -- a program to manage archives of 
ii  cpp                                       4:4.4.0-3ubuntu1                        The GNU C preprocessor (cpp)
ii  cpp-4.4                                   4.4.1-1ubuntu3                          The GNU C preprocessor
ii  dash                                      0.5.5.1-2ubuntu2                        POSIX-compliant shell
ii  dbus                                      1.2.16-0ubuntu2                         simple interprocess messaging system
ii  debconf                                   1.5.27ubuntu1                           Debian configuration management system
ii  debconf-i18n                              1.5.27ubuntu1                           full internationalization support for debcon
ii  debianutils                               2.30ubuntu3                             Miscellaneous utilities specific to Debian
ii  default-jre-headless                      1.6-30ubuntu5                           Standard Java or Java compatible Runtime (he
ii  defoma                                    0.11.10-0.2ubuntu1                      Debian Font Manager -- automatic font config
ii  devicekit-disks                           006-0ubuntu4                            abstraction for enumerating block devices
ii  devicekit-power                           010-0ubuntu1                            abstraction for power management
ii  dhcp3-client                              3.1.2-1ubuntu5                          DHCP client
ii  dhcp3-common                              3.1.2-1ubuntu5                          common files used by all the dhcp3* packages
ii  diff                                      2.8.1-13                                File comparison utilities
ii  dmidecode                                 2.9-1ubuntu1                            Dump Desktop Management Interface data
ii  dmsetup                                   2:1.02.27-4ubuntu6                      The Linux Kernel Device Mapper userspace lib
ii  dpkg                                      1.15.3.1ubuntu1                         Debian package management system
ii  e2fslibs                                  1.41.8-1ubuntu2                         ext2/ext3/ext4 file system libraries
ii  e2fsprogs                                 1.41.8-1ubuntu2                         ext2/ext3/ext4 file system utilities
ii  e4fsprogs-git                             1.41.9-1chromeos1                       statically-linked version of the ext2/ext3/e
ii  eject                                     2.1.5+deb1+cvs20081104-6                ejects CDs and operates CD-Changers under Li
ii  file                                      5.03-1ubuntu1                           Determines file type using "magic" numbers
ii  findutils                                 4.4.2-1                                 utilities for finding files--find, xargs
ii  flashplugin-installer                     10.0.32.18ubuntu1                       Adobe Flash Player plugin installer
ii  fontconfig                                2.6.0-1ubuntu12                         generic font configuration library - support
ii  fontconfig-config                         2.6.0-1ubuntu12                         generic font configuration library - configu
ii  gcc-4.4-base                              4.4.1-1ubuntu3                          The GNU Compiler Collection (base package)
ii  gcj-4.4-base                              4.4.1-1ubuntu4                          The GNU Compiler Collection (gcj base packag
ii  gcj-4.4-jre                               4.4.1-1ubuntu4                          Java runtime environment using GIJ/classpath
ii  gcj-4.4-jre-headless                      4.4.1-1ubuntu4                          Java runtime environment using GIJ/classpath
ii  gcj-4.4-jre-lib                           4.4.1-1ubuntu4                          Java runtime library for use with gcj (jar f
ii  gcj-jre                                   4:4.4.0-3ubuntu1                        Java runtime environment using GIJ/classpath
ii  gcj-jre-headless                          4:4.4.0-3ubuntu1                        Java runtime environment using GIJ/classpath
ii  gconf2-common                             2.26.2-3ubuntu2                         GNOME configuration database system (common 
ii  gnupg                                     1.4.9-4ubuntu5                          GNU privacy guard - a free PGP replacement
ii  gpgv                                      1.4.9-4ubuntu5                          GNU privacy guard - signature verification t
ii  grep                                      2.5.4-4                                 GNU grep, egrep and fgrep
ii  gzip                                      1.3.12-8ubuntu1                         GNU compression utilities
ii  hal                                       1.0                                     Fake hal package to satisfy dependencies.
ii  hicolor-icon-theme                        0.10-2                                  default fallback theme for FreeDesktop.org i
ii  hostname                                  2.95                                    utility to set/show the host name or domain 
ii  icedtea-6-jre-cacao                       6b16~pre5-0ubuntu2                      Alternative JVM for OpenJDK, using Cacao
ii  ifupdown                                  0.6.8ubuntu19                           high level tools to configure network interf
ii  initramfs-tools                           0.92bubuntu39                           tools for generating an initramfs
ii  initscripts                               2.86.ds1-61ubuntu16                     Scripts for initializing and shutting down t
ii  iproute                                   20090324-1                              networking and traffic control tools
ii  iptables                                  1.4.4-1ubuntu1                          administration tools for packet filtering an
ii  iputils-ping                              3:20071127-1build1                      Tools to test the reachability of network ho
ii  java-common                               0.30ubuntu5                             Base of all Java packages
ii  kbd                                       1.15-1ubuntu1                           Linux console font and keytable utilities
ii  klibc-utils                               1.5.15-1                                small utilities built with klibc for early b
ii  laptop-detect                             0.13.7ubuntu1                           attempt to detect a laptop
ii  less                                      429-2                                   pager program similar to more
ii  libacl1                                   2.2.47-2                                Access control list shared library
ii  libasound2                                1.0.20-3ubuntu3                         shared library for ALSA applications
ii  libasound2-plugins                        1.0.20-1ubuntu6                         ALSA library additional plugins
ii  libatasmart4                              0.16-1                                  ATA S.M.A.R.T. reading and parsing library
ii  libatk1.0-0                               1.27.90-0ubuntu1                        The ATK accessibility toolkit
ii  libatk1.0-data                            1.27.90-0ubuntu1                        Common files for the ATK accessibility toolk
ii  libatm1                                   2.4.1-17.2                              shared library for ATM (Asynchronous Transfe
ii  libattr1                                  1:2.4.43-3                              Extended attribute shared library
ii  libblkid1                                 2.16-1ubuntu1                           block device id library
ii  libbz2-1.0                                1.0.5-3                                 high-quality block-sorting file compressor l
ii  libc6                                     2.10.1-0ubuntu6                         GNU C Library: Shared libraries
ii  libc6-i686                                2.10.1-0ubuntu6                         GNU C Library: Shared libraries [i686 optimi
ii  libcairo2                                 1.8.8-2ubuntu1                          The Cairo 2D vector graphics library
ii  libcap2                                   1:2.16-5ubuntu1                         support for getting/setting POSIX.1e capabil
ii  libck-connector0                          0.3.1-0ubuntu1                          ConsoleKit libraries
ii  libclass-accessor-perl                    0.33-1                                  Automated accessor generator
ii  libcloog-ppl0                             0.15-1                                  the Chunky Loop Generator (runtime library)
ii  libclutter-0.9-0                          0.9.8-0ubuntu1                          Open GL based interactive canvas library
ii  libcomerr2                                1.41.8-1ubuntu2                         common error description library
ii  libcommons-cli-java                       1.1-3ubuntu1                            API for working with the command line argume
ii  libcommons-compress-java                  0~svn604876-1                           Java API for working with tar, zip and bzip2
ii  libcommons-lang-java                      2.4-1ubuntu1                            Extension of the java.lang package
ii  libcups2                                  1.3.11-1ubuntu1                         Common UNIX Printing System(tm) - libs
ii  libcurl3                                  7.19.5-1ubuntu2                         Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                           7.19.5-1ubuntu1                         Multi-protocol file transfer library (GnuTLS
ii  libcwidget3                               0.5.12-4ubuntu2                         high-level terminal interface library for C+
ii  libdatrie1                                0.2.2-1                                 Double-array trie library
ii  libdb4.7                                  4.7.25-7ubuntu2                         Berkeley v4.7 Database Libraries [runtime]
ii  libdbus-1-3                               1.2.16-0ubuntu2                         simple interprocess messaging system
ii  libdbus-glib-1-2                          0.80-4                                  simple interprocess messaging system (GLib-b
ii  libdevkit-power-gobject1                  010-0ubuntu1                            abstraction for power management - shared li
ii  libdevmapper1.02.1                        2:1.02.27-4ubuntu6                      The Linux Kernel Device Mapper userspace lib
ii  libdirectfb-1.2-0                         1.2.7-2ubuntu1                          direct frame buffer graphics - shared librar
ii  libdrm-intel1                             2.4.12-1ubuntu1                         Userspace interface to intel-specific kernel
ii  libdrm2                                   2.4.12-1ubuntu1                         Userspace interface to kernel DRM services -
ii  libedit2                                  2.11~20080614-2                         BSD editline and history libraries
ii  libeggdbus-1-0                            0.5-1                                   D-Bus bindings for GObject
ii  libept0                                   0.5.26build1                            High-level library for managing Debian packa
ii  libexpat1                                 2.0.1-4                                 XML parsing C library - runtime library
ii  libffi5                                   3.0.7-1ubuntu1                          Foreign Function Interface library runtime
ii  libflac8                                  1.2.1-2                                 Free Lossless Audio Codec - runtime C librar
ii  libfontconfig1                            2.6.0-1ubuntu12                         generic font configuration library - runtime
ii  libfontenc1                               1:1.0.4-3                               X11 font encoding library
ii  libfreetype6                              2.3.9-5                                 FreeType 2 font engine, shared library files
ii  libfribidi0                               0.10.9-1build1                          Free Implementation of the Unicode BiDi algo
ii  libgcc1                                   1:4.4.1-1ubuntu3                        GCC support library
ii  libgcj-common                             1:4.4.0-3ubuntu1                        Java runtime library (common files)
ii  libgcj10                                  4.4.1-1ubuntu4                          Java runtime library for use with gcj
ii  libgcj10-awt                              4.4.1-1ubuntu4                          AWT peer runtime libraries for use with gcj
ii  libgconf2-4                               2.26.2-3ubuntu2                         GNOME configuration database system (shared 
ii  libgcrypt11                               1.4.4-2ubuntu2                          LGPL Crypto library - runtime library
ii  libgdbm3                                  1.8.3-4                                 GNU dbm database routines (runtime version)
ii  libgflags0                                1.1-1                                   a library that implements commandline flags
ii  libgl1-mesa-dri                           7.5-1ubuntu1                            A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx                           7.5-1ubuntu1                            A free implementation of the OpenGL API -- G
ii  libglib2.0-0                              2.21.4-0ubuntu1                         The GLib library of C routines
ii  libglib2.0-data                           2.21.4-0ubuntu1                         Common files for GLib library
ii  libgmp3c2                                 2:4.3.1+dfsg-1ubuntu2                   Multiprecision arithmetic library
ii  libgmpxx4ldbl                             2:4.3.1+dfsg-1ubuntu2                   Multiprecision arithmetic library (C++ bindi
ii  libgnutls26                               2.6.6-1                                 the GNU TLS library - runtime library
ii  libgpg-error0                             1.6-1ubuntu1                            library for common error values and messages
ii  libgpm2                                   1.20.4-3.2                              General Purpose Mouse - shared library
ii  libgssapi-krb5-2                          1.7dfsg~beta3-1                         MIT Kerberos runtime libraries - krb5 GSS-AP
ii  libgtk2.0-0                               2.17.6-0ubuntu2                         The GTK+ graphical user interface library
ii  libgtk2.0-bin                             2.17.6-0ubuntu2                         The programs for the GTK+ graphical user int
ii  libgtk2.0-common                          2.17.6-0ubuntu2                         Common files for the GTK+ graphical user int
ii  libgudev-1.0-0                            1:145-1                                 GObject-based wrapper library for libudev
ii  libhal1                                   0.5.13-1ubuntu1                         Hardware Abstraction Layer - shared library
ii  libhx18                                   2.9-3                                   A library providing queue, tree, I/O and uti
ii  libice6                                   2:1.0.5-1                               X11 Inter-Client Exchange library
ii  libidl0                                   0.8.13-0.1                              library for parsing CORBA IDL files
ii  libidn11                                  1.15-1                                  GNU Libidn library, implementation of IETF I
ii  libio-string-perl                         1.08-2                                  Emulate IO::File interface for in-core strin
ii  libiw29                                   29-2ubuntu3                             Wireless tools - library
ii  libjasper1                                1.900.1-6                               The JasPer JPEG-2000 runtime library
ii  libjline-java                             0.9.94-1ubuntu1                         Java library for handling console input
ii  libjpeg62                                 6b-14build1                             The Independent JPEG Group's JPEG runtime li
ii  libk5crypto3                              1.7dfsg~beta3-1                         MIT Kerberos runtime libraries - Crypto Libr
ii  libkeyutils1                              1.2-10                                  Linux Key Management Utilities (library)
ii  libklibc                                  1.5.15-1                                minimal libc subset for use with initramfs
ii  libkrb5-3                                 1.7dfsg~beta3-1                         MIT Kerberos runtime libraries
ii  libkrb5support0                           1.7dfsg~beta3-1                         MIT Kerberos runtime libraries - Support lib
ii  liblcms1                                  1.18.dfsg-1ubuntu1                      Color management library
ii  libldap-2.4-2                             2.4.17-1ubuntu2                         OpenLDAP libraries
ii  liblocale-gettext-perl                    1.05-4build1                            Using libc functions for internationalizatio
ii  liblockfile1                              1.08-3                                  NFS-safe locking library, includes dotlockfi
ii  libmagic1                                 5.03-1ubuntu1                           File type determination library using "magic
ii  libmpfr1ldbl                              2.4.1-1ubuntu1                          multiple precision floating-point computatio
ii  libncurses5                               5.7+20090607-1ubuntu1                   shared libraries for terminal handling
ii  libncursesw5                              5.7+20090607-1ubuntu1                   shared libraries for terminal handling (wide
ii  libnewt0.52                               0.52.10-4                               Not Erik's Windowing Toolkit - text mode win
ii  libnspr4-0d                               4.8-0ubuntu1                            NetScape Portable Runtime Library
ii  libnss3-1d                                3.12.3.1-0ubuntu1                       Network Security Service libraries
ii  libogg0                                   1.1.3-5build1                           Ogg Bitstream Library
ii  liborbit2                                 1:2.14.17-0.1                           libraries for ORBit2 - a CORBA ORB
ii  libpam-ck-connector                       0.3.1-0ubuntu1                          ConsoleKit PAM module
ii  libpam-modules                            1.0.1-10ubuntu1                         Pluggable Authentication Modules for PAM
ii  libpam-mount                              1.27-4                                  PAM module that can mount volumes for a user
ii  libpam-runtime                            1.0.1-10ubuntu1                         Runtime support for the PAM library
ii  libpam0g                                  1.0.1-10ubuntu1                         Pluggable Authentication Modules library
ii  libpango1.0-0                             1.25.2-0ubuntu1                         Layout and rendering of internationalized te
ii  libpango1.0-common                        1.25.2-0ubuntu1                         Modules and configuration files for the Pang
ii  libparse-debianchangelog-perl             1.1.1-2ubuntu1                          parse Debian changelogs and output them in o
ii  libparted1.8-12                           1.8.8.git.2009.06.03-1ubuntu6           The GNU Parted disk partitioning shared libr
ii  libpci3                                   1:3.0.0-4ubuntu11                       Linux PCI Utilities (shared library)
ii  libpciaccess0                             0.10.6-1                                Generic PCI access library for X
ii  libpcre3                                  7.8-2ubuntu1                            Perl 5 Compatible Regular Expression Library
ii  libpcrecpp0                               7.8-2ubuntu1                            Perl 5 Compatible Regular Expression Library
ii  libpixman-1-0                             0.14.0-1                                pixel-manipulation library for X and cairo
ii  libpng12-0                                1.2.37-1                                PNG library - runtime
ii  libpolkit-backend-1-0                     0.94-0ubuntu1                           PolicyKit backend API
ii  libpolkit-gobject-1-0                     0.94-0ubuntu1                           PolicyKit Authorization API
ii  libpopt0                                  1.14-4                                  lib for parsing cmdline parameters
ii  libppl-c2                                 0.10.2-2                                Parma Polyhedra Library (C interface)
ii  libppl7                                   0.10.2-2                                Parma Polyhedra Library (runtime library)
ii  libprotobuf3                              2.0.3-2.2ubuntu1                        protocol buffer C++ library
ii  libpulse0                                 1:0.9.16~test4-0ubuntu4                 PulseAudio client libraries
ii  libpython2.6                              2.6.2-0ubuntu3                          Shared Python runtime library (version 2.6)
ii  libreadline5                              5.2-4                                   GNU readline and history libraries, run-time
ii  libsamplerate0                            0.1.7-2                                 audio rate conversion library
ii  libsasl2-2                                2.1.23.dfsg1-1ubuntu1                   Cyrus SASL - authentication abstraction libr
ii  libsasl2-modules                          2.1.23.dfsg1-1ubuntu1                   Cyrus SASL - pluggable authentication module
ii  libselinux1                               2.0.82-1ubuntu2                         SELinux shared libraries
ii  libsepol1                                 2.0.36-1                                Security Enhanced Linux policy library for c
ii  libsgutils2-2                             1.27-0.1                                utilities for working with generic SCSI devi
ii  libsigc++-2.0-0c2a                        2.0.18-2                                type-safe Signal Framework for C++ - runtime
ii  libslang2                                 2.1.4-3                                 The S-Lang programming library - runtime ver
ii  libsm6                                    2:1.1.0-2                               X11 Session Management library
ii  libsndfile1                               1.0.20-1ubuntu1                         Library for reading/writing audio files
ii  libsqlite3-0                              3.6.16-1                                SQLite 3 shared library
ii  libss2                                    1.41.8-1ubuntu2                         command-line interface parsing library
ii  libssl0.9.8                               0.9.8g-16ubuntu2                        SSL shared libraries
ii  libstdc++6                                4.4.1-1ubuntu3                          The GNU Standard C++ Library v3
ii  libsub-name-perl                          0.04-1                                  Assigns a new name to referenced sub
ii  libsysfs2                                 2.1.0-5                                 interface library to sysfs
ii  libtasn1-3                                2.2-1                                   Manage ASN.1 structures (runtime)
ii  libtext-charwidth-perl                    0.04-5build1                            get display widths of characters on the term
ii  libtext-iconv-perl                        1.7-1build1                             converts between character sets in Perl
ii  libtext-wrapi18n-perl                     0.06-7                                  internationalized substitute of Text::Wrap
ii  libthai-data                              0.1.12-1                                Data files for Thai language support library
ii  libthai0                                  0.1.12-1                                Thai language support library
ii  libtiff4                                  3.8.2-13                                Tag Image File Format (TIFF) library
ii  libtimedate-perl                          1.1600-9                                Time and date functions for Perl
ii  libts-0.0-0                               1.0-7                                   touch screen library
ii  libudev0                                  145-1                                   udev library
ii  libusb-0.1-4                              2:0.1.12-13                             userspace USB programming library
ii  libuuid1                                  2.16-1ubuntu1                           Universally Unique ID library
ii  libvorbis0a                               1.2.0.dfsg-5                            The Vorbis General Audio Compression Codec: 
ii  libvorbisenc2                             1.2.0.dfsg-5                            The Vorbis General Audio Compression Codec: 
ii  libwrap0                                  7.6.q-16                                Wietse Venema's TCP wrappers library
ii  libx11-6                                  2:1.2.2-1ubuntu1                        X11 client-side library
ii  libx11-data                               2:1.2.2-1ubuntu1                        X11 client-side library
ii  libxapian15                               1.0.14-1                                Search engine library
ii  libxau6                                   1:1.0.4-2                               X11 authorisation library
ii  libxaw7                                   2:1.0.6-1                               X11 Athena Widget library
ii  libxcb-render-util0                       0.3.5-1                                 utility libraries for X C Binding -- render-
ii  libxcb-render0                            1.4-1                                   X C Binding, render extension
ii  libxcb1                                   1.4-1                                   X C Binding
ii  libxcomposite1                            1:0.4.0-4                               X11 Composite extension library
ii  libxcursor1                               1:1.1.9-1build1                         X cursor management library
ii  libxdamage1                               1:1.1.1-4                               X11 damaged region extension library
ii  libxdmcp6                                 1:1.0.2-3                               X11 Display Manager Control Protocol library
ii  libxext6                                  2:1.0.99.1-0ubuntu3                     X11 miscellaneous extension library
ii  libxfixes3                                1:4.0.3-2build1                         X11 miscellaneous 'fixes' extension library
ii  libxfont1                                 1:1.4.0-1ubuntu1                        X11 font rasterisation library
ii  libxft2                                   2.1.13-3ubuntu1                         FreeType-based font drawing library for X
ii  libxi6                                    2:1.2.1-2ubuntu1                        X11 Input extension library
ii  libxinerama1                              2:1.0.3-2                               X11 Xinerama extension library
ii  libxkbfile1                               1:1.0.5-1ubuntu2                        X11 keyboard file manipulation library
ii  libxml2                                   2.7.3.dfsg-1ubuntu1                     GNOME XML library
ii  libxmu6                                   2:1.0.4-1build1                         X11 miscellaneous utility library
ii  libxmuu1                                  2:1.0.4-1build1                         X11 miscellaneous micro-utility library
ii  libxpm4                                   1:3.5.7-2                               X11 pixmap library
ii  libxrandr2                                2:1.3.0-2                               X11 RandR extension library
ii  libxrender1                               1:0.9.4-2                               X Rendering Extension client library
ii  libxt6                                    1:1.0.5-3ubuntu1                        X11 toolkit intrinsics library
ii  libxtrap6                                 2:1.0.0-5build1                         X11 event trapping extension library
ii  libxtst6                                  2:1.0.3-1ubuntu2                        X11 Testing -- Resource extension library
ii  libxv1                                    2:1.0.4-1                               X11 Video extension library
ii  libxvmc1                                  2:1.0.4-2ubuntu1                        X11 Video extension library
ii  libxxf86dga1                              2:1.0.2-1build1                         X11 Direct Graphics Access extension library
ii  libxxf86misc1                             1:1.0.1-3                               X11 XFree86 miscellaneous extension library
ii  libxxf86vm1                               1:1.0.2-1                               X11 XFree86 video mode extension library
ii  linux-image-2.6.30-chromeos-intel-menlow  002                                     Linux kernel binary image for version 2.6.30
ii  linux-sound-base                          1.0.20+dfsg-1ubuntu4                    base package for ALSA and OSS sound systems
ii  locales                                   2.9+git20090617-1                       common files for locale support
ii  lockfile-progs                            0.1.13                                  Programs for locking and unlocking files and
ii  login                                     1:4.1.4.1-1ubuntu2                      system login tools
ii  lsb-base                                  4.0-0ubuntu2                            Linux Standard Base 4.0 init script function
ii  lsb-release                               4.0-0ubuntu2                            Linux Standard Base version reporting utilit
ii  lsof                                      4.81.dfsg.1-1                           List open files
ii  lzma                                      4.43-14ubuntu1                          Compression method of 7z format in 7-Zip pro
ii  make                                      3.81-6                                  An utility for Directing compilation.
ii  makedev                                   2.3.1-88                                creates device files in /dev
ii  mawk                                      1.3.3-14ubuntu1                         a pattern scanning and text processing langu
ii  memento-updater                           0.2                                     Memento Autoupdater
ii  mime-support                              3.46-1                                  MIME files 'mime.types' & 'mailcap', and sup
ii  module-init-tools                         3.10-2                                  tools for managing Linux kernel modules
ii  mount                                     2.16-1ubuntu1                           Tools for mounting and manipulating filesyst
ii  ncurses-base                              5.7+20090607-1ubuntu1                   basic terminal type definitions
ii  ncurses-bin                               5.7+20090607-1ubuntu1                   terminal-related programs and man pages
ii  net-tools                                 1.60-23ubuntu1                          The NET-3 networking toolkit
ii  netbase                                   4.35ubuntu1                             Basic TCP/IP networking system
ii  netcat                                    1.10-38                                 TCP/IP swiss army knife -- transitional pack
ii  netcat-traditional                        1.10-38                                 TCP/IP swiss army knife
ii  ntp                                       1:4.2.4p6+dfsg-1ubuntu4                 Network Time Protocol daemon and utility pro
ii  ntpdate                                   1:4.2.4p6+dfsg-1ubuntu2                 client for setting system time from NTP serv
ii  openjdk-6-jre-headless                    6b16~pre5-0ubuntu2                      OpenJDK Java runtime, using Hotspot JIT (hea
ii  openjdk-6-jre-lib                         6b16~pre5-0ubuntu2                      OpenJDK Java runtime (architecture independe
ii  openssh-client                            1:5.1p1-6ubuntu1                        secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server                            1:5.1p1-6ubuntu1                        secure shell server, an rshd replacement
ii  openssl                                   0.9.8g-16ubuntu2                        Secure Socket Layer (SSL) binary and related
ii  passwd                                    1:4.1.4.1-1ubuntu2                      change and administer password and group dat
ii  pciutils                                  1:3.0.0-4ubuntu11                       Linux PCI Utilities
ii  perl                                      5.10.0-24ubuntu2                        Larry Wall's Practical Extraction and Report
ii  perl-base                                 5.10.0-24ubuntu2                        minimal Perl system
ii  perl-modules                              5.10.0-24ubuntu2                        Core Perl modules
ii  policykit-1                               0.94-0ubuntu1                           framework for managing administrative polici
ii  procps                                    1:3.2.8-1ubuntu2                        /proc file system utilities
ii  python                                    2.6.2-0ubuntu1                          An interactive high-level object-oriented la
ii  python-central                            0.6.11ubuntu7                           register and build utility for Python packag
ii  python-dbus                               0.83.0-1ubuntu2                         simple interprocess messaging system (Python
ii  python-gobject                            2.18.0-0ubuntu1                         Python bindings for the GObject library
ii  python-minimal                            2.6.2-0ubuntu1                          A minimal subset of the Python language (def
ii  python-support                            1.0.3ubuntu1                            automated rebuilding support for Python modu
ii  python2.6                                 2.6.2-0ubuntu3                          An interactive high-level object-oriented la
ii  python2.6-minimal                         2.6.2-0ubuntu3                          A minimal subset of the Python language (ver
ii  readline-common                           6.0-0ubuntu1                            GNU readline and history libraries, common f
ii  rhino                                     1.7R2-1ubuntu1                          JavaScript engine written in Java
ii  rsyslog                                   4.2.0-1ubuntu2                          enhanced multi-threaded syslogd
ii  sed                                       4.2.1-1                                 The GNU sed stream editor
ii  sgml-base                                 1.26                                    SGML infrastructure and SGML catalog file su
ii  shared-mime-info                          0.60-2                                  FreeDesktop.org shared MIME database and spe
ii  slim                                      1.3.1-chromeos3                         desktop-independent graphical login manager 
ii  sudo                                      1.7.0-1ubuntu2                          Provide limited super user privileges to spe
ii  sysv-rc                                   2.86.ds1-61ubuntu16                     System-V-like runlevel change mechanism
ii  sysvinit-utils                            2.86.ds1-61ubuntu16                     System-V-like utilities
ii  tar                                       1.22-1                                  GNU version of the tar archiving utility
ii  tasksel                                   2.73ubuntu20                            Tool for selecting tasks for installation on
ii  tasksel-data                              2.73ubuntu20                            Official tasks used for installation of Debi
ii  tcpd                                      7.6.q-16                                Wietse Venema's TCP wrapper utilities
ii  tsconf                                    1.0-7                                   touch screen library common files
ii  ttf-dejavu                                2.29-2                                  Metapackage to pull in ttf-dejavu-core and t
ii  ttf-dejavu-core                           2.29-2                                  Vera font family derivate with additional ch
ii  ttf-dejavu-extra                          2.29-2                                  Vera font family derivate with additional ch
ii  ttf-droid                                 1.00~b112+dfsg+1-0ubuntu1               handheld device font with extensive style an
ii  tzdata                                    2009k-2                                 time zone and daylight-saving time data
ii  tzdata-java                               2009k-2                                 time zone and daylight-saving time data for 
ii  ubuntu-keyring                            2008.03.04                              GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                            1.158                                   Minimal core of Ubuntu
ii  ucf                                       3.0018                                  Update Configuration File: preserve user cha
ii  udev                                      145-1                                   rule-based device node and kernel event mana
ii  upstart                                   0.6.3-1                                 event-based init daemon
ii  util-linux                                2.16-1ubuntu1                           Miscellaneous system utilities
ii  vim-common                                2:7.2.148-2ubuntu2                      Vi IMproved - Common files
ii  vim-tiny                                  2:7.2.148-2ubuntu2                      Vi IMproved - enhanced vi editor - compact v
ii  wget                                      1.11.4-2ubuntu1                         retrieves files from the web
ii  whiptail                                  0.52.10-4                               Displays user-friendly dialog boxes from she
ii  wireless-tools                            29-2ubuntu3                             Tools for manipulating Linux Wireless Extens
ii  x-ttcidfont-conf                          32                                      TrueType and CID fonts configuration for X
ii  x11-common                                1:7.4+3ubuntu5                          X Window System (X.Org) infrastructure
ii  x11-utils                                 7.4+1build1                             X11 utilities
ii  x11-xkb-utils                             7.4+3                                   X11 XKB utilities
ii  x11-xserver-utils                         7.4+2                                   X server utilities
ii  xauth                                     1:1.0.3-2                               X authentication utility
ii  xbitmaps                                  1.0.1-2ubuntu1                          Base X bitmaps
ii  xdg-utils                                 1.0.2-6.1                               desktop integration utilities from freedeskt
ii  xfonts-encodings                          1:1.0.2-3                               Encodings for X.Org fonts
ii  xfonts-utils                              1:7.4+1ubuntu1                          X Window System font utility programs
ii  xkb-data                                  1.6-1ubuntu1                            X Keyboard Extension (XKB) configuration dat
ii  xml-core                                  0.12                                    XML infrastructure and XML catalog file supp
ii  xscreensaver                              5.0.8-chromeos2                         Screen locker for Chrome OS
ii  xserver-common                            2:1.6.3-1ubuntu1                        common files used by various X servers
ii  xserver-xorg                              1:7.4+3ubuntu5                          the X.Org X server
ii  xserver-xorg-core                         2:1.6.3-1ubuntu2                        Xorg X server - core server
ii  xserver-xorg-input-all                    1:7.4+3ubuntu5                          the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-evdev                  1:2.2.2-1ubuntu2                        X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                    1:1.3.2-3                               X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse                  1:1.4.0-2                               X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics              1.1.2-1ubuntu5                          Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-wacom                  1:0.8.3.2-1ubuntu1                      X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                    1:7.4+3ubuntu5                          the X.Org X server -- output driver metapack
ii  xserver-xorg-video-apm                    1:1.2.1-2                               X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                    1:0.7.1-2                               X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                    1:6.12.99+git20090629.f39cafc5-0ubuntu5 X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-chips                  1:1.2.1-3                               X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                 1:1.3.1-1                               X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                  1:0.4.0-4                               X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                  2.11.3-1                                X.Org server -- Geode GX2/LX display driver
ii  xserver-xorg-video-i128                   1:1.3.2-1                               X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740                   1:1.3.0-1                               X.Org X server -- i740 display driver
ii  xserver-xorg-video-intel                  2:2.8.0-0ubuntu3                        X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-mach64                 6.8.0+git20090201.d394e0b8-2            X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                    1:1.4.10.dfsg-1                         X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic               1:1.2.3-1                               X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nv                     1:2.1.14-2ubuntu2                       X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome             1:0.2.903+svn758-0ubuntu1               X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128                   6.8.0+git20090201.08d56c88-2            X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                 1:6.12.99+git20090629.f39cafc5-0ubuntu5 X.Org X server -- ATI Radeon display driver
ii  xserver-xorg-video-rendition              1:4.2.1-1                               X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                     1:0.6.2-1                               X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                1:1.10.2-2                              X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                 1:2.3.0-1                               X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion          1:1.7.2-1                               X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-video-sis                    1:0.10.1-2                              X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                 1:0.9.1-1                               X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                   1:1.4.1-1                               X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                1:1.3.1-1                               X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                  1:1.2.1-1                               X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                    1:0.2.0-3ubuntu1                        X.Org X server -- Video 4 Linux display driv
ii  xserver-xorg-video-vesa                   1:2.2.0-1                               X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                 1:10.16.7-1                             X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                 1:1.2.2-1                               X.Org X server -- Voodoo display driver
ii  xterm                                     243-1ubuntu1                            X terminal emulator
ii  zlib1g                                    1:1.2.3.3.dfsg-13ubuntu1                compression library - runtime
```Here's uname -a```
Linux localhost 2.6.30-chromeos-intel-menlow #1 SMP Fri Nov 20 01:27:51 UTC 2009 i686 GNU/Linux
```And df -h```
Filesystem            Size  Used Avail Use% Mounted on
rootfs                936M  589M  299M  67% /
udev                  376M  376M     0 100% /dev
/dev/disk/by-label/C-ROOT
                      936M  589M  299M  67% /
/tmp                  376M  8.0K  376M   1% /tmp
shmfs                 376M  140K  376M   1% /dev/shm
/dev/sda1             936M   22M  867M   3% /mnt/stateful_partition
/dev/sda1             936M   22M  867M   3% /var/cache
/dev/sda1             936M   22M  867M   3% /var/log
vartmp                376M   20K  376M   1% /var/tmp
/dev/sda1             936M   22M  867M   3% /home
varrun                376M   44K  376M   1% /var/run
varlock               376M     0  376M   0% /var/lock
/media                376M     0  376M   0% /media
/dev/mapper/cryptohome
                      376M   15M  362M   4% /home/chronos
tmpfs                 376M   15M  362M   4% /home/chronos
```

---

### Post by jmmL on 2009-11-19
> **DillByrne said:**
> il seed it !, cant promise il always be on but il be happy to seed along with #! and karmic, and give back!
I'm just trying to figure out how to split it into multiple archives. If anyone has any guides, that'd really speed things up. Shouldn't take long to upload once that's done though.

---

### Post by Dougie187 on 2009-11-19
You could do it with tar, or rar. Thought with rar I don't know how to. But with Tar you have to use -M -L, for the use of them you should look it up in the man page.

-L has to be followed by the archive size.

---

### Post by Tipped OuT on 2009-11-19
Finally! Screen shots! I think we just made history here guys. :D

---

### Post by obscurant1st on 2009-11-19
hey pls upload it to Rapidshare, if u r having difficulties on splitting it i cn help u..

---

### Post by jmmL on 2009-11-19
> **Dougie187 said:**
> You could do it with tar, or rar. Thought with rar I don't know how to. But with Tar you have to use -M -L, for the use of them you should look it up in the man page.

-L has to be followed by the archive size.

Okay, thanks for the pointer. I'm uploading "ide.vmdk" which is the image for chromiumOS. The root password on this image is "chromium05", but I couldn't figure out how to get to a terminal, so it might be of limited use for the time being!

Links:
[http://rapidshare.com/files/309484345/chromiumOS-1.tar](http://rapidshare.com/files/309484345/chromiumOS-1.tar)
[http://rapidshare.com/files/309485808/chromiumOS-2.tar](http://rapidshare.com/files/309485808/chromiumOS-2.tar)
[http://rapidshare.com/files/309487192/chromiumOS-3.tar](http://rapidshare.com/files/309487192/chromiumOS-3.tar)
[http://rapidshare.com/files/309488963/chromiumOS-4.tar](http://rapidshare.com/files/309488963/chromiumOS-4.tar)

Here is what you need to do, with what you need to type in bold:
```
:~$ **tar -x -M --file=chromiumOS-1.tar ide.vmdk**
Prepare volume #2 for `chromiumOS.tar' and hit return: **n chromiumOS-2.tar**
Prepare volume #3 for `chromiumOS-2.tar' and hit return: **n chromiumOS-3.tar**
Prepare volume #4 for `chromiumOS-3.tar' and hit return: **n chromiumOS-4.tar**
```That will give you ide.vmdk in your home folder. I did a test run with mine and md5summed to check there weren't any errors.

I would have liked to use rar, just because it seems more simple to extract. Tar will do for the time being.

The Google documentation on building it from start to finish was absolutely fantastic. Everything went without a hitch (or at least, so I can tell!).

---

### Post by etnlIcarus on 2009-11-19
Anyone else feel claustrophobic just looking at those screen shots?

---

### Post by Islington on 2009-11-19
> **etnlIcarus said:**
> Anyone else feel claustrophobic just looking at those screen shots?

not really, screenspace is for use, are you the one with the ridiculously/amazingly complex window oranization xfce setup?

---

### Post by FuturePilot on 2009-11-19
> **etnlIcarus said:**
> Anyone else feel claustrophobic just looking at those screen shots?

yes

---

### Post by lovinglinux on 2009-11-19
> **Tipped OuT said:**
> Finally! Screen shots! I think we just made history here guys. :D

You can see a demo at [http://www.youtube.com/user/googlechrome](http://www.youtube.com/user/googlechrome)

The direct link to the demo video is [http://www.youtube.com/watch?v=ANMrzw7JFzA](http://www.youtube.com/watch?v=ANMrzw7JFzA)


> **obscurant1st said:**
> hey pls upload it to Rapidshare, if u r having difficulties on splitting it i cn help u..

Why not create a torrent?

---

### Post by jmmL on 2009-11-19
> **etnlIcarus said:**
> Anyone else feel claustrophobic just looking at those screen shots?

If you're talking about the resolution, then that's just because it was run in a 640x480 box - pretty small compared to most of the screens today. It looks like it makes a really efficient use of space to me. There's a full-screen mode as well - it does what it says on the tin.

---

### Post by Sealbhach on 2009-11-19
[FONT=Book Antiqua][SIZE=1]> **etnlIcarus said:**
> Anyone else feel claustrophobic just looking at those screen shots?

Yes. Claustrophobic, limited and very much owned, as if I was a Google employee or something.[/SIZE][/FONT][FONT=Book Antiqua]

.
[/FONT]

---

### Post by The Funkbomb on 2009-11-19
I doubt it but I'm wondering if ChromeOS will support the GMA500 gpu in my netbook.

---

### Post by etnlIcarus on 2009-11-19
> **Islington said:**
> not really, screenspace is for use, are you the one with the ridiculously/amazingly complex window oranization xfce setup?wut? 

> **jmmL said:**
> If you're talking about the resolution, then that's just because it was run in a 640x480 box - pretty small compared to most of the screens today. It looks like it makes a really efficient use of space to me. There's a full-screen mode as well - it does what it says on the tin.

I'm talking about the 'everything is the web browser' design. It's bringing back traumatic memories of Windows 9.x, when applications just wouldn't close, resize, minimise, give up focus and, assuming they hadn't frozen, your only real choice was to go on using them.

---

### Post by Tipped OuT on 2009-11-19
> **etnlIcarus said:**
> wut? 


Yes.

---

### Post by jmmL on 2009-11-19
I've collated as much as possible into the first post.
Now, sleep!

---

### Post by ctrlmd on 2009-11-19
> **etnlIcarus said:**
> Anyone else feel claustrophobic just looking at those screen shots?
yes i took back my hopes and add them to ubuntu it was 60% ubuntu to 40% to google 
now my hopes back lol 100% ubuntu

---

### Post by julianb on 2009-11-19
> **ctrlmd said:**
> yes i took back my hopes and add them to ubuntu it was 60% ubuntu to 40% to google 
now my hopes back lol 100% ubuntu

Put your hopes in something that takes the best from Chromium, Ubuntu, LXDE/ Masonux, Moblin. 

One of the great things about open source software is that it's easier to get favorite features from a lot of different software. 

None of the setups I mention above have everything I want, but if you put all of their advantages together you've got something pretty spectacular.

---

### Post by andrewabc on 2009-11-19
> **lovinglinux said:**
> 
Why not create a torrent?

Yes someone please create a torrent for those who don't want to deal with rapidshare. (don't compress the file or anything unless it makes a huge difference).
How big is the virtual thing?

Also, make sure the one you posted is fresh and not with you logged into your gmail...

At first look at screenshot I thought of Moblin.
And they are not officially releaseing it until 1/2 way through 2010? Hopefully they make lots of improvements by then.

---

### Post by Aflack on 2009-11-19
has this even been released yet? i thought it was for solid slate drives only?

---

### Post by andrewabc on 2009-11-19
> **Aflack said:**
> has this even been released yet? i thought it was for solid slate drives only?

Not officially released, they just released source code.
I have a SSD.

But I see no reason why it can't run on hard drives, even though google disabled that for some stupid reason. If not run on hard drive where is the OS installed to? Or did they mean no apps are on hard drive?
Wouldn't that mean you'd have to download the OS/apps every time you turn on computer? Or are they stored in ram/swap file? Doesn't make sense.

---

### Post by Aflack on 2009-11-19
> **andrewabc said:**
> Not officially released, they just released source code.
I have a SSD.

But I see no reason why it can't run on hard drives, even though google disabled that for some stupid reason. If not run on hard drive where is the OS installed to? Or did they mean no apps are on hard drive?
Wouldn't that mean you'd have to download the OS/apps every time you turn on computer? Or are they stored in ram/swap file? Doesn't make sense.

Im confused. Ithought  i saw something on this google os today that was just released not too long ago. claiming to only run for google certified systems... boots up in 1-7 seconds or something...

nvm got it.

---

### Post by andrewabc on 2009-11-19
> **Aflack said:**
> Im confused. Ithought  i saw something on this google os today that was just released not too long ago. claiming to only run for google certified systems... boots up in 1-7 seconds or something...

Yes that is what they say.

But they released source code so people can do whatever they want. I think the press release was more of a discussion about google partnering with some computer manufacturers to make the OS run good on certain hardware only. Kinda like apple does.

---

### Post by jmmL on 2009-11-19
> **andrewabc said:**
> Yes someone please create a torrent for those who don't want to deal with rapidshare. (don't compress the file or anything unless it makes a huge difference).
How big is the virtual thing?

**Also, make sure the one you posted is fresh and not with you logged into your gmail...**

At first look at screenshot I thought of Moblin.
And they are not officially releaseing it until 1/2 way through 2010? Hopefully they make lots of improvements by then.

I'll second the torrent. I can't here, for network policy reasons.
There's no compression in the tars, so still approx. 720MB.

Make sure the torrent is a completely un-used one. I rebuilt the image before I uploaded it, so it didn't contain any gmail stuff. Once I logged in the image grew a bit, so it's writing data of some sort - I don't know if it's storing anything personal though.

The source for chromiumOS was released today. ChromeOS is due this time next year. There doesn't really appear to be restrictions on what hardware it will run on at a code-level - as long as your hardware is supported by the 2.6.30 kernel (this is the kernel it uses), chromium OS will boot on it. Google have stated however that only solid-state devices will be come pre-installed with chromeOS - but I'm sure the community will have their own versions that anyone can put on any computer.

Sleep is over-rated.

---

### Post by Wiebelhaus on 2009-11-20
I like you very much jmml! I was just about to do it myself , Thanks for offering everyone another method of exploration into this very exciting ARM alternative.

---

### Post by CJ Master on 2009-11-20
> **etnlIcarus said:**
> I'm talking about the 'everything is the web browser' design. It's bringing back traumatic memories of Windows 9.x, when applications just wouldn't close, resize, minimise, give up focus and, assuming they hadn't frozen, your only real choice was to go on using them.

Please. Windows 98 wasn't anything like Chrome OS is now. We're talking over 10 years difference on a better foundation, here. Also, in my experiences of using regular chrome when a tab crashes I can easily exit out of the tab without closing the browser.

---

### Post by phrostbyte on 2009-11-20
Maybe this can be forked into something more flexible, like Ubuntu Chromium Remix. I mean Google made it all FOSS and they said in the webcast explicitly that they are cool with forks.

---

### Post by Sealbhach on 2009-11-20
> **andrewabc said:**
> Not officially released, they just released source code.
I have a SSD.

But I see no reason why it can't run on hard drives, even though google disabled that for some stupid reason. If not run on hard drive where is the OS installed to?

I wonder if it can be installed onto a USB drive?

.

---

### Post by phrostbyte on 2009-11-20
> **Sealbhach said:**
> I wonder if it can be installed onto a USB drive?

.

Anything is possible with open source! :popcorn:

But seriously the code is quite rough around the edges so any kind of cool stuff will involve some kind of work.

---

### Post by jmmL on 2009-11-20
> **phrostbyte said:**
> Anything is possible with open source! :popcorn:

But seriously the code is quite rough around the edges so any kind of cool stuff will involve some kind of work.

There's a script included in chromiumos/src/scripts called image_to_usb.sh that will do this for you. See [http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions#TOC-Copy-the-image-to-a-USB-key](http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions#TOC-Copy-the-image-to-a-USB-key)

---

### Post by phrostbyte on 2009-11-20
> **jmmL said:**
> There's a script included in chromiumos/src/scripts called image_to_usb.sh that will do this for you. See [http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions#TOC-Copy-the-image-to-a-USB-key](http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions#TOC-Copy-the-image-to-a-USB-key)

Nice find. :D

---

### Post by themusicalduck on 2009-11-20
Just found this - [http://www.techcrunch.com/2009/11/19/guide-install-google-chrome-os/](http://www.techcrunch.com/2009/11/19/guide-install-google-chrome-os/)

And it links to a healthy torrent too for a VM image. Gonna give it a go once it downloads.

---

### Post by hellmet on 2009-11-20
I don't have a RapidShare account, and I won't be able to download 720 MB in a day! I'd really appreciate a torrent here... 

And to jmmL : Thanks a lot man! Nice work, and I can't wait to get my hands onto it.

---

### Post by jmmL on 2009-11-20
> **hellmet said:**
> I don't have a RapidShare account, and I won't be able to download 720 MB in a day! I'd really appreciate a torrent here... 

And to jmmL : Thanks a lot man! Nice work, and I can't wait to get my hands onto it.

No worries. I've updated the original post to include alternative sources. If better ones appear or those ones stop working for some reason, I'll amend as appropriate.

---

### Post by renkinjutsu on 2009-11-20
dang it! .. i tried building it myself before i stumbled onto this thread! I managed to get a rootfs.image, but no mbr.image? no idea what i did wrong...


i'm gonna download the torrent on techChrunch

---

### Post by hellmet on 2009-11-20
Damn buggy... Login worked once. Trying another login fails - No network. But the previous login works (stored login info) and Internet works within the account. Just won't let me login using another..
Still testing it.. Chrome OS is probably the first OS that would have a seriously huge market share even before official launch.. and within the first day!

Update: Apparently "Network not available" = "Invalid Password" 
And what the heck is Google Short Links.. The menu needs a Google.com account!! Never heard of it. I get this:
"Google short links uses your Google.com account for sign-in"

---

### Post by jmmL on 2009-11-20
These are screenshots to show the terminal in action, and proof of sudo. I've edited the first post to add details.

Also, hellmet, I had similar problems the first few times I logged in. Haven't had them since for some reason.

Edit: Added keyboard shortcut screens.
Edit2: Added shot of window overview, accessed by using F12.

---

### Post by etnlIcarus on 2009-11-20
> **CJ Master said:**
> Please. Windows 98 wasn't anything like Chrome OS is now. We're talking over 10 years difference on a better foundation, here. Also, in my experiences of using regular chrome when a tab crashes I can easily exit out of the tab without closing the browser.
...it's as if you didn't even read the post. I wasn't being that literal, geez.
> **phrostbyte said:**
> Maybe this can be forked into something more flexible, like Ubuntu Chromium Remix. I mean Google made it all FOSS and they said in the webcast explicitly that they are cool with forks.
Forks aren't an 'easy' solution. You either end up duplicating a lot of work to maintain feature parity, or you take the less expensive but less flexible route of maintaining downstream bug fixes.

---

### Post by zagz on 2009-11-20
Oh my goodness, it ships with Chrome browser???

The EU will have a field day with them.

---

### Post by jmmL on 2009-11-20
Now that I have terminal access: what do people want / need to know?

Also, chromiumOS comes with flash out-of-the-box.

---

### Post by gioz on 2009-11-20
downloaded from torrent ([https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2](https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2))
and i get this error with sun virtualbox

```
Failed to open the hard disk /home/gio/chromeos-image-999.999.32309.211410-a1.vmdk.
Cannot register the hard disk '/home/gio/chromeos-image-999.999.32309.211410-a1.vmdk' with UUID {1d70d848-4eed-4321-83bc-5c1c86c2593b} because a CD/DVD image '/home/gio/chromeos-image-999.999.32309.211410-a1.vmdk' with UUID {439c6e21-3223-488c-9230-40bb0cac5844} already exists in the media registry ('/home/gio/.VirtualBox/VirtualBox.xml').
```

---

### Post by Nerd King on 2009-11-20
Honestly it's nothing more than splashtop with a google logo on it. Nothing exciting, honestly no innovation. It's a massive disappointment frankly.

---

### Post by Johnsie on 2009-11-20
Yay, everything you do with your computer will now be monitored by third parties... This is an awesome technology (not). But being a techie, I'm still gonna try it out of curiousity.

I just think that Internet companies have become a little bit to invasive.

---

### Post by jmmL on 2009-11-20
> **gioz said:**
> downloaded from torrent ([https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2](https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2))
and i get this error with sun virtualbox

```
Failed to open the hard disk /home/gio/chromeos-image-999.999.32309.211410-a1.vmdk.
Cannot register the hard disk '/home/gio/chromeos-image-999.999.32309.211410-a1.vmdk' with UUID {1d70d848-4eed-4321-83bc-5c1c86c2593b} because a CD/DVD image '/home/gio/chromeos-image-999.999.32309.211410-a1.vmdk' with UUID {439c6e21-3223-488c-9230-40bb0cac5844} already exists in the media registry ('/home/gio/.VirtualBox/VirtualBox.xml').
```

Looks like you've already tried to register the hard disk before. Go File > Virtual Media Manager and remove all the hard disks in there (unless you have any that you know you need). Then try again. It should work this time.

As a bonus here's a bootchart (it comes pre-installed) from chromium. For some reason the forum software has converted it to a poor quality jpg. Hmm.

---

### Post by Paqman on 2009-11-20
> **hellmet said:**
> Damn buggy... Login worked once. Trying another login fails - No network.

I can't get in at all, not using my own Google account, and not using a throwaway one I just registered.

:(

---

### Post by jmmL on 2009-11-20
> **Paqman said:**
> I can't get in at all, not using my own Google account, and not using a throwaway one I just registered.

:(

I had a slight hiccup with logging before I realised that the keyboard defaults to en-US, so some characters on the keyboard have different mappings. Don't know if this is relevant or not. Who's build are you using?

---

### Post by Tibuda on 2009-11-20
> **zagz said:**
> Oh my goodness, it ships with Chrome browser???

The EU will have a field day with them.
no, it doesnt ship with crhome browser, it IS chrome browser.

---

### Post by gioz on 2009-11-20
> **jmmL said:**
> Looks like you've already tried to register the hard disk before. Go File > Virtual Media Manager and remove all the hard disks in there (unless you have any that you know you need). Then try again. It should work this time.

Thanks! now it works.

---

### Post by maxrisc on 2009-11-20
Anyone got a USB image of this?  I'd like to give it a try on my Aspire A150.

---

### Post by marchwarden on 2009-11-20
> **danielrmt said:**
> no, it doesnt ship with crhome browser, it IS chrome browser.

Nor is there market control or influence...yet.

---

### Post by Paqman on 2009-11-20
> **jmmL said:**
> I had a slight hiccup with logging before I realised that the keyboard defaults to en-US, so some characters on the keyboard have different mappings. Don't know if this is relevant or not. Who's build are you using?

Shouldn't make a difference with what i'm putting in. My build is 999.999.32309.211.410

---

### Post by markc on 2009-11-20
Anyone know what the password is for the chronos user with this image?

[https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2](https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2)

---

### Post by Enjoy Incubus on 2009-11-20
Couldn't login with my GMail account. Don't really know why, I'm using the same network configuration from another VMs where internet connection works fine. Any help plz?

---

### Post by walterav on 2009-11-20
> markc  	
Re: Chromium OS compiled - VMWare image made
Anyone know what the password is for the chronos user with this image?

[https://thepiratebay.org/torrent/517...10-a1.vmdk.bz2](https://thepiratebay.org/torrent/517...10-a1.vmdk.bz2)

Did you try:
un:'mark'
pw:'onle'
sudo:'chromeos'

?

---

### Post by zagz on 2009-11-20
It uses x.org so no changes there, if you can get a command line to find what toolkit it uses (QT,GTK)?

---

### Post by zagz on 2009-11-20
> **markc said:**
> Anyone know what the password is for the chronos user with this image?

[https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2](https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2)


Shared user password (for sudo, etc is 'chromeos')



From your link.

---

### Post by t0p on 2009-11-20
> **gioz said:**
> downloaded from torrent ([https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2](https://thepiratebay.org/torrent/5170843/chromeos-image-999.999.32309.211410-a1.vmdk.bz2))
and i get this error with sun virtualbox

```
Failed to open the hard disk /home/gio/chromeos-image-999.999.32309.211410-a1.vmdk.
Cannot register the hard disk '/home/gio/chromeos-image-999.999.32309.211410-a1.vmdk' with UUID {1d70d848-4eed-4321-83bc-5c1c86c2593b} because a CD/DVD image '/home/gio/chromeos-image-999.999.32309.211410-a1.vmdk' with UUID {439c6e21-3223-488c-9230-40bb0cac5844} already exists in the media registry ('/home/gio/.VirtualBox/VirtualBox.xml').
```

Will VMWare .vmdk images work in VirtualBox?  I did a search and found a bunch of links to stuff like these: [link1]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool#Converting%20your%20existing%20.vmdk%20Virtual%20Disc%20Image%20To%20a%20.vdi%20File") [link2]("http://stackoverflow.com/questions/1505021/virtualbox-and-vmdk-vmx-files").  These all say that to get a VMWare virtual machine to work on VirtualBox, you need to convert the .vmdk image to .vdi format.  Is this no longer true?

---

### Post by Tibuda on 2009-11-20
> **zagz said:**
> It uses x.org so no changes there, if you can get a command line to find what toolkit it uses (QT,GTK)?

Chrome/ium for Linux have alwasys used Gtk+, I don't think the ChromeOS version changed that. It don't really matter, because all apps will use HTML as a toolkit.

---

### Post by HappinessNow on 2009-11-20
> **jmmL said:**
> These are screenshots to show the terminal in action, and proof of sudo. I've edited the first post to add details.

Also, hellmet, I had similar problems the first few times I logged in. Haven't had them since for some reason.

Edit: Added keyboard shortcut screens.
Edit2: Added shot of window overview, accessed by using F12.
visually reminds me of Haiku

---

### Post by Regenweald on 2009-11-20
> **&#20170 said:**
> visually reminds me of Haiku
If I were a Haiku dev, I'd track you down for saying that :D

---

### Post by lastelement0 on 2009-11-20
Is there any way to get those rapidshare links up on megaupload as well?

---

### Post by Wiebelhaus on 2009-11-20
> **lastelement0 said:**
> Is there any way to get those rapidshare links up on megaupload as well?

Eh , someone already [linked this]("http://www.techcrunch.com/2009/11/19/guide-install-google-chrome-os/")but here ya go much faster and safer option.

---

### Post by gioz on 2009-11-20
> **t0p said:**
> Will VMWare .vmdk images work in VirtualBox?  I did a search and found a bunch of links to stuff like these: [link1]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool#Converting%20your%20existing%20.vmdk%20Virtual%20Disc%20Image%20To%20a%20.vdi%20File") [link2]("http://stackoverflow.com/questions/1505021/virtualbox-and-vmdk-vmx-files").  These all say that to get a VMWare virtual machine to work on VirtualBox, you need to convert the .vmdk image to .vdi format.  Is this no longer true?

Yes  my .vmdk image works in VirtualBox. I didn't convert it to .vdi format. 

you can follow these steps ; [http://www.techcrunch.com/2009/11/19/guide-install-google-chrome-os/](http://www.techcrunch.com/2009/11/19/guide-install-google-chrome-os/)

[http://img44.imageshack.us/img44/3883/19526757.png](http://img44.imageshack.us/img44/3883/19526757.png)

---

### Post by holas on 2009-11-20
Does anyone have an iso image??
THX

---

### Post by sdowney717 on 2009-11-20
[http://gdgt.com/google/chrome-os/download/](http://gdgt.com/google/chrome-os/download/)

i got it from here as a vmware image

---

### Post by holas on 2009-11-20
thx but I would like to install it on a SD card and I do not know how to do it from vmdk image

---

### Post by sdowney717 on 2009-11-20
it is fairly easy to install. you need vmware player, create a linux vm
then edit it by adding in the vmdk file as another hard drive. Delete the original blank vmdk hard drive. set networking to bridged.
Start up machine and login with your gmail account info

however, imo the image says it all to me. this is very primitive so far.
chrome will do everything from a browser window

---

### Post by holas on 2009-11-20
I know how to use vmdk with vmware or virtualbox but I would like to install it on a SD CARD and boot my netbook from it. For this I need an iso (bin, img, isz, etc) image file.

Anyway THX.

---

### Post by jmmL on 2009-11-20
> **holas said:**
> I know how to use vmdk with vmware or virtualbox but I would like to install it on a SD CARD and boot my netbook from it. For this I need an iso (bin, img, isz, etc) image file.

Anyway THX.

If you're willing to compile everything yourself, there's an option to copy the images (which are in .image format, don't know if this helps) to a USB stick (or really any external device, like an SD card or portable hard-drive). So you could do it this way. I don't know how to convert the .vmdk into a liveUSB image for booting. So unfortunately you might have to wait for the time being..

Just to confirm the vmdks work fine on virtualbox - no need to convert them to anything else.

And someone was asking about whether chromium uses gtk/qt . Here's the installed gtk libraries:
```

libgtk2.0-0 (2.17.6-0ubuntu2) 
libgtk2.0-bin (2.17.6-0ubuntu2)
libgtk2.0-common (2.17.6-0ubuntu2)
```Couldn't find any qt ones.

Any other requests?
Are the people with log-in trouble still having problems?

---

### Post by zackiv31 on 2009-11-20
What OS should we install under in VirtualBox? (does it matter?)

---

### Post by jakal323 on 2009-11-20
> **zackiv31 said:**
> What OS should we install under in VirtualBox? (does it matter?)

It just sets the cosmetic option in the hypervisor frontend and suggests some presets for memory, HD size (though that's not really valid here), and other settings.

I would use Ubuntu myself, as this is the closest thing.

---

### Post by andrewabc on 2009-11-20
I tried the torrent virtual machine, and the OS is crap. I didn't sign in to the 3rd party website as they would datamine me and get my email address, and they are not affiliated with google.

Much better off using/testing Moblin.

---

### Post by Enjoy Incubus on 2009-11-20
> **sdowney717 said:**
> it is fairly easy to install. you need vmware player, create a linux vm
then edit it by adding in the vmdk file as another hard drive. Delete the original blank vmdk hard drive. set networking to bridged.
Start up machine and login with your gmail account info

however, imo the image says it all to me. this is very primitive so far.
chrome will do everything from a browser window
Tried out that way also. Couldn't login either.

---

### Post by t0p on 2009-11-20
> **andrewabc said:**
> I tried the torrent virtual machine, and the OS is crap.

Well it's still very early days.  This is a very early beta, maybe an alpha.  It's been [released primarily for developers - it's due to be released for consumers next year.]("http://googleblog.blogspot.com/2009/11/releasing-chromium-os-open-source.html")

---

### Post by jmmL on 2009-11-20
> **t0p said:**
> Well it's still very early days.  This is a very early beta, maybe an alpha.  It's been [released primarily for developers - it's due to be released for consumers next year.]("http://googleblog.blogspot.com/2009/11/releasing-chromium-os-open-source.html")
It really is early on in chrome's development. At this stage, it's basically a stripped down ubuntu karmic, with a slightly modified 2.6.30 kernel, a bleeding-edge build of chromium-browser and possibly a custom window manager; chromeos-wm, although I don't actually know whether it's just a branch of another wm, or google have developed it from scratch.

I've updated the first post with information about mounting root as rw.

---

### Post by AndyOfLinux on 2009-11-20
I really got tired of the 800x600 screen resolution of Chromium OS in the VMWare image.  I went into a terminal Ctl+Alt+T and started looking at X configuration files.  I could not find the usual settings so tried some x commands. "/usr/bin/xrandr" with no parameters will show available screen resolutions. "/usr/bin/xrandr --size 1280x960" changes the VMWare window (and all things Chrome) size to 1280x960.  Works well for me!

Another tip you might already be aware of: F12 shows selectable thumbnails of windows (browser tabs and terminal windows) Under VMWare Fusion, you need to use the "Virtual Machine -> Send key..." menu.

- Andy

---

### Post by LuboBa on 2009-11-20
Please share on rapid the two build files in the image directory .....
then I can make the USB image and share it .... I cannot find the USB image anywhere yet

thanks

---

### Post by Regenweald on 2009-11-20
[http://gdgt.com/google/chrome-os/download/](http://gdgt.com/google/chrome-os/download/)

---

### Post by m4tic on 2009-11-21
Bootstrap?

---

### Post by teachop on 2009-11-21
The build process is well documented - it must be, because I was able to do it.  As advertised, it is a system with pretty much nothing but the browser, although you can drop into the terminal.  It will be interesting to watch how it develops.

Here is a good OT bug, I am sure it isn't Chromium OS fault.  It runs fine on my wired network, but on my wireless, it drags so slow it is unusable, and quickly the ancient wireless router I have crashes.  Hmmm...  Must be time for new equipment.

---

### Post by YosefKaro on 2009-11-21
Unfortunately (at least for me) chromium OS has to 'see' that one is connected to the internet in order to even be able to log in to use the OS.  That sucks: it doesn't even give me the chance to get in and tweak with it to 'make' it 'see' my internet connection. :( The problem that I have is that I cannot connect through network manager because I use a broadband dongle and for that reason, virtualbox doesn't 'see' that I am connected to a network.  And I've been looking forward to trying out google chrome OS on my lappy for quite some time now. :(  Oh well.

-Yos

---

### Post by YosefKaro on 2009-11-21
Everything you need to know about chrome os [here]("http://gizmodo.com/5408504/everything-you-need-to-know-about-chrome-os/")  The one thing that doesn't sit well with me is that 'You'll have to buy a Chrome OS device'.

-Yos

---

### Post by CaveMole on 2009-11-21
[QUOTE=renkinjutsu;8352679]dang it! .. i tried building it myself before i stumbled onto this thread! I managed to get a rootfs.image, but no mbr.image? no idea what i did wrong...

Same problem here.
I wanted to try it on an eeePC 900.
I had to comment out some of the wireless stuff, it would not build.
After that, all went according to plan, except that I have no mbr.image.

any idea where to get one?

I could guess that this is a fairly standard image.
A very minimalist bootloader that might not even use disk partitions?

---

### Post by jmmL on 2009-11-21
> **CaveMole said:**
> 
Same problem here.
I wanted to try it on an eeePC 900.
I had to comment out some of the wireless stuff, it would not build.
After that, all went according to plan, except that I have no mbr.image.

any idea where to get one?

I could guess that this is a fairly standard image.
A very minimalist bootloader that might not even use disk partitions?
I've attached my one.

Edit: Links for the mbr and the rootfs are now in the first post. Should be useful if anyone wants to build a USB image.

---

### Post by provoko on 2009-11-21
Thanks jmml for the USB image.  So what happens when you try the option to install it from a USB stick?  The Chrome OS site says it'll "nuke your drive".

---

### Post by jmmL on 2009-11-21
> **provoko said:**
> Thanks jmml for the USB image.  So what happens when you try the option to install it from a USB stick?  The Chrome OS site says it'll "nuke your drive".

I haven't tried anything with the USB image myself. I don't actually have a working USB stick to hand..
Well I'm guessing it's just like any other LiveUSB, except that it doesn't sound like it'll give you the option to install along-side another OS (or at least, not without some tweaking on the user's part).

In other developments, it looks like the "desktop" screen of chromium has gone live. Yesterday, you needed an @google.com address, today any old google account will work.

Almost all of the icons are just shortcuts to other websites. The Chess one is weird - with the html5 capabilities of chromium, I though perhaps google would use this. Instead the shortcut is just to a 3rd-party flash-based site.

Calculator, to-do list and notebook don't seem to be working yet. Contacts opens up google talk. It lets me sign in, but I don't know if it works because I don't actually have any contacts that use the service.

---

### Post by vorcigernix on 2009-11-23
I was able to compile and run from usb without problem. Unfortunately, all my hardware is nvidia or ati, did someone succeeded in adding oss drivers? 
There is description how to add package ([http://www.chromium.org/chromium-os/how-tos-and-troubleshooting/add-a-new-package](http://www.chromium.org/chromium-os/how-tos-and-troubleshooting/add-a-new-package)), but it still doesn't work (I assume it is not needed to install package or change xorg.conf)

---

### Post by EnlistedSquire on 2009-11-23
Hi,

I've got the VM running in Virtualbox on Ubuntu 9.10 runningand can login fine.

However, I can't get any of the non-standard keyboard shortcuts to work. By that I mean the normal browser shortcuts work (F5, F6, CTRL-T etc.) but F8, F12, CTRL-ALT-T don't do anything for me.

Did anyone else find this and did you solve it?

Thanks.

---

### Post by Gadgetech on 2009-11-24
> **EnlistedSquire said:**
> Hi,

I've got the VM running in Virtualbox on Ubuntu 9.10 runningand can login fine.

However, I can't get any of the non-standard keyboard shortcuts to work. By that I mean the normal browser shortcuts work (F5, F6, CTRL-T etc.) but F8, F12, CTRL-ALT-T don't do anything for me.

Did anyone else find this and did you solve it?

Thanks.

VirtualBox uses the Host Key (right Ctrl on your keyboard is default) as Ctrl+Alt. So if you want to open a terminal with Ctrl+Alt+T, use RightCtrl+T.

---

### Post by Gadgetech on 2009-11-24
Has anyone gotten this to work in VirtualBox on Hardy? I compiled it myself and tried the torrent. I get the login screen, but after I log in I just get a blank blue screen.  The same build that I compiled works fine from USB on my netbook.

---

### Post by PhoHammer on 2009-11-24
> **YosefKaro said:**
> Unfortunately (at least for me) chromium OS has to 'see' that one is connected to the internet in order to even be able to log in to use the OS.  That sucks: it doesn't even give me the chance to get in and tweak with it to 'make' it 'see' my internet connection. :( The problem that I have is that I cannot connect through network manager because I use a broadband dongle and for that reason, virtualbox doesn't 'see' that I am connected to a network.  And I've been looking forward to trying out google chrome OS on my lappy for quite some time now. :(  Oh well.

-Yos

If you use the username "chronos" to sign in, it will let you even without a live connection (there's no password for that user)

> Everything you need to know about chrome os here The one thing that doesn't sit well with me is that 'You'll have to buy a Chrome OS device'.

Obviously not. You see, it is **open source**. Therefore, you can do what you want with it. It just might be up to you to get exotic hardware working. 
But that's why we were born to be Linux users, right? :)
 
BTW: I have written an "Install Chrome OS to USB" guide [[COLOR="Blue"]_here_[/COLOR]]("http://chrometecha.blogspot.com/2009/11/install-chrome-os-to-usb.html"). I am posting from Chrome OS booted via USB right now ;)

---

### Post by toupeiro on 2009-11-24
OP:

Great work, and thanks especially for providing the links to the source!  I think I am going to try it from scratch just to get a feel for their procedure.  Looking forward to testing this!

---

### Post by toupeiro on 2009-11-24
Well, I was having problems with the source.  seems the libuuid package somehow got banged up and I couldn't create the local repository.  

So, I hit google (the search engine) and a little while later, I have a keychain drive bootable version of chromiumOS, but not from source!

Heres what I did:

Step 1:
[http://www.makeuseof.com/tag/download-google-chrome-os-and-run-on-a-real-computer/](http://www.makeuseof.com/tag/download-google-chrome-os-and-run-on-a-real-computer/)

Go here and grab the usb image torrent file.

Step 2: extract it, and ditch their instructions on how to write the image file that are provided as they pertain to windows..  Unzip the file, then gzip the .img file (this may not be necessary in the big picture, but for the sake of the tool I used, I did it.)

Step 3: Insert a blank keychain drive and determine its physical path (you can type mount at a command line to see what the automounter mounted it to)  Mine happened to be /dev/sdf1.  Make sure its unmounted before you continue. (sudo umount /dev/sdf1 for me, /dev/somethingelse for you)

Step 4: chmod 666 your keychain drive (sudo chmod 666 /dev/sdf) (you can change it back later by chmodding it to 660)

Step 5: type: sudo zcat chrome_os.img.gz > /dev/sdf (or whatever your usb drive is)

Voala!  Keychain bootable chrome OS.

EDIT:  anyone find a power-off button in the OS yet???? :P

---

### Post by EnlistedSquire on 2009-11-25
> **Gadgetech said:**
> VirtualBox uses the Host Key (right Ctrl on your keyboard is default) as Ctrl+Alt. So if you want to open a terminal with Ctrl+Alt+T, use RightCtrl+T.

Still nothing. I also changed the Host key to Left Shift and tried varying combinations of keys with no luck.

---

### Post by Bölvaður on 2009-11-25
> **EnlistedSquire said:**
> Still nothing. I also changed the Host key to Left Shift and tried varying combinations of keys with no luck.

same for me.
and everything lags like hell. But I guess it's just like that on the virtual machine isn't it?

---

### Post by zagz on 2009-11-25
If you wants the iso (for DVD) then let us know.

---

### Post by fromthehill on 2009-11-25
my google account doesn't work with chrome

a couple of things was wondering about:
[LIST]
[*]most netbooks(at least here) don't come with 3g. you have to buy a usb-stick with a subscription(which is really expensive). without 3g you can't start the os
[*]an other option (for most people the only option) is connecting with a wifi network. how are you supposed to select your network when you cant even log in the os.
[*] the only way to connect properly is via wired connection, but doesn't that defeat the whole purpose of netbooks?
[/LIST].
it should at least let you see the difference between "no connection" and wrong login:D

---

### Post by Johnsie on 2009-11-25
I ran it and it was very slow. Needless to say I was unimpressed as it only appears to be a browser. Using this operating system makes me feel like my every move is being tracked. Yes, that may sound paranoid, but working in the software industry I know that companies do whatever they can to collect information about people and measure trends.

---

### Post by snadrus on 2009-11-25
To put a VMDK into a physical drive:
- Attach to the VMWare image your HD in a USB enclosure. 
- Boot the VM onto an ubuntu CD (or anything with Gparted).
- copy the partition to your physical drive using gparted. 
- Fix the bootloader with grub-install (somehow).

---

### Post by jmans25 on 2009-12-02
WHAT IS THE ROOT PASSWORD?

I am afraid to use my google account with this unofficial os. thanks!

---

### Post by jmmL on 2009-12-02
> **jmans25 said:**
> WHAT IS THE ROOT PASSWORD?

I am afraid to use my google account with this unofficial os. thanks!
I believe that using "chronos" as a username should let you log in without a google account. "chromium05" is the root password for my build.

---

### Post by jmans25 on 2009-12-02
> **jmmL said:**
> I believe that using "chronos" as a username should let you log in without a google account. "chromium05" is the root password for my build.
  thanks bro!

---

### Post by HarshReality on 2009-12-16
Ive read the compile tutorials and done some source builds in the past but this one is greek to me.. would love to setup a script to autod/l and build but need to get an exact step by step for a d/l and build from a clean install of ubuntu to do it.

---

### Post by shashi859 on 2009-12-26
hi everyone.......
i intsalled chrome os on usb just by extracting a built usb image using image writer and it all went well.First i had the problem of wifi connection but later by reading a post i just coppied the */lib/firmware* of ubuntu on primary hard disk to chrome on usb and now its alright except sound.
i am unable to hear any sound of any webites -youyube,magnatune.......etc
can anyone help me to correct it.......
and have anyone installed chrome to hard disk with other os

---

### Post by shashi859 on 2009-12-28
Now i am back after facing a great **DISASTER**:(:( when playing with chrome os.

The disaster goes like this ___ After reading a instruction in a blog about installation of chrome into hard disk , i decided to rum *sudo /usr/sbin/chrome-install* .In blog he said it will give on screen instructions *but* it neither gave any instruction or help it **straight  away removed partitions and created new partition table in a fraction of mins** and all of a sudden i was shocked and hit *ctrl+z * to end up process
      after reboot it showed as '* missing operating system*' and my friends 5 year old laptop with Original XP and Ubuntu installed just 2 years back and most importantly the documents accumulated over period got completely **cleared for the first time.**:(:(

Now i am looking for data recovery through the same chrome os and exams are nearer ,i cant spend more time before it ...
Hence BEWARE before you try to install it to hard disk.......

---

### Post by sandyd on 2009-12-28
> **jmmL said:**
> I'm just trying to figure out how to split it into multiple archives. If anyone has any guides, that'd really speed things up. Shouldn't take long to upload once that's done though.
use megaupload. they have a 500mb file size limit.

---

### Post by jmmL on 2009-12-28
> **carlee said:**
> use megaupload. they have a 500mb file size limit.

I've got my latest version down to under 200MB, so hopefully this shouldn't be an issue anymore. Thanks for the pointer though.

At the moment I'm aiming to publish builds every month or so, but the one I compiled a few days ago (the first one I've done since the first build) isn't working. It appears to build successfully and the image is converted to a .vdi seemingly without issue, but upon boot it does nothing.

I'll post an update here when I make progress.

---

### Post by sandyd on 2009-12-31
p.s.
anyone who wants to compile their own version, but doesn't really want to look through the google build instructions....

-> [http://ubuntuforums.org/showthread.php?p=8588761#post8588761](http://ubuntuforums.org/showthread.php?p=8588761#post8588761)

---

### Post by mvalviar on 2010-01-14
how to I use the usb image to boot from usb?

---

### Post by ipguy on 2010-02-04
anyone know where i can find an bootable ISO ?

---

