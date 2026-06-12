---
title: "What linux distro to use for minimal virtual guest machines?"
date: 2016-12-04
forum: Virtualisation
---

### Post by loyhz2ayj-jeff on 2016-12-04
I had been in the habit of running certain services in a minimal virtual machine on Ubuntu Server, and i used Ubuntu Server for the guest OS as well.  Now with Xenial it puts LXC/LXD on every system, which clearly makes Ubuntu Server unsuitable for use a guest operating system.  It also no longer fits on a 2GB virtual disk.

I know containers are the the thing and in fact I'm using Docker for almost everything these days but for some things I still need a virtual server.  What should I use?

---

### Post by &amp;KyT$0P# on 2016-12-04
I've no idea what you "should" use.  No one aside you can answer that.

But the way I did my local server sounds similar to what you want.  And I used Debian jessie.

It is a bit of a pain to get set up initially, but after that it gets pretty similar to Ubuntu.

---

### Post by KillerKelvUK on 2016-12-05
Have just tested with the minimal install .iso to create a Xenial guest with a 2GB virtual disk which worked fine, not much space left to be fair but it works. ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

Partitioning:-
```

Disk /dev/vda: 2 GiB, 2147483648 bytes, 4194304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x19065ed7


Device     Boot   Start     End Sectors  Size Id Type
/dev/vda1  *       2048  487423  485376  237M 83 Linux
/dev/vda2        487424 3612671 3125248  1.5G 83 Linux
/dev/vda3       3612672 4192255  579584  283M 82 Linux swap / Solaris

```

Filesystem directly after install:
```

Filesystem            Size  Used Avail Use% Mounted on
udev                  983M     0  983M   0% /dev
tmpfs                 201M  3.1M  197M   2% /run
/dev/vda2             1.5G  975M  404M  71% /
tmpfs                1001M     0 1001M   0% /dev/shm
tmpfs                 5.0M     0  5.0M   0% /run/lock
tmpfs                1001M     0 1001M   0% /sys/fs/cgroup
/dev/vda1             230M   52M  166M  24% /boot

```

Default packages installed (as part of the install tasksel was prompted with a default option checked that I removed):-
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                      Architecture Description
+++-==================================-============================-============-===============================================================================
ii  accountsservice                    0.6.40-2ubuntu11.3           amd64        query and manipulate user account information
ii  adduser                            3.113+nmu3ubuntu4            all          add and remove users and groups
ii  apt                                1.2.15                       amd64        commandline package manager
ii  apt-utils                          1.2.15                       amd64        package management related utility programs
ii  base-files                         9.4ubuntu4.3                 amd64        Debian base system miscellaneous files
ii  base-passwd                        3.5.39                       amd64        Debian base system master password and group files
ii  bash                               4.3-14ubuntu1.1              amd64        GNU Bourne Again SHell
ii  bsdutils                           1:2.27.1-6ubuntu3.1          amd64        basic utilities from 4.4BSD-Lite
ii  busybox-initramfs                  1:1.22.0-15ubuntu1           amd64        Standalone shell setup for initramfs
ii  bzip2                              1.0.6-8                      amd64        high-quality block-sorting file compressor - utilities
ii  console-setup                      1.108ubuntu15.2              all          console font and keymap setup program
ii  console-setup-linux                1.108ubuntu15.2              all          Linux specific part of console-setup
ii  coreutils                          8.25-2ubuntu2                amd64        GNU core utilities
ii  cpio                               2.11+dfsg-5ubuntu1           amd64        GNU cpio -- a program to manage archives of files
ii  crda                               3.13-1                       amd64        wireless Central Regulatory Domain Agent
ii  cron                               3.0pl1-128ubuntu2            amd64        process scheduling daemon
ii  dash                               0.5.8-2.1ubuntu2             amd64        POSIX-compliant shell
ii  dbus                               1.10.6-1ubuntu3.1            amd64        simple interprocess messaging system (daemon and utilities)
ii  debconf                            1.5.58ubuntu1                all          Debian configuration management system
ii  debconf-i18n                       1.5.58ubuntu1                all          full internationalization support for debconf
ii  debianutils                        4.7                          amd64        Miscellaneous utilities specific to Debian
ii  dh-python                          2.20151103ubuntu1.1          all          Debian helper tools for packaging Python libraries and applications
ii  dictionaries-common                1.26.3                       all          spelling dictionaries - common utilities
ii  diffutils                          1:3.3-3                      amd64        File comparison utilities
ii  discover                           2.1.2-7ubuntu1               amd64        hardware identification system
ii  discover-data                      2.2013.01.11                 all          Data lists for Discover hardware detection system
ii  distro-info-data                   0.28ubuntu0.2                all          information about the distributions' releases (data files)
ii  dmidecode                          3.0-2ubuntu0.1               amd64        SMBIOS/DMI table decoder
ii  dpkg                               1.18.4ubuntu1.1              amd64        Debian package management system
ii  e2fslibs:amd64                     1.42.13-1ubuntu1             amd64        ext2/ext3/ext4 file system libraries
ii  e2fsprogs                          1.42.13-1ubuntu1             amd64        ext2/ext3/ext4 file system utilities
ii  eject                              2.1.5+deb1+cvs20081104-13.1  amd64        ejects CDs and operates CD-Changers under Linux
ii  emacsen-common                     2.0.8                        all          Common facilities for all emacsen
ii  file                               1:5.25-2ubuntu1              amd64        Determines file type using "magic" numbers
ii  findutils                          4.6.0+git+20160126-2         amd64        utilities for finding files--find, xargs
ii  gcc-5-base:amd64                   5.4.0-6ubuntu1~16.04.4       amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-6-base:amd64                   6.0.1-0ubuntu1               amd64        GCC, the GNU Compiler Collection (base package)
ii  gettext-base                       0.19.7-2ubuntu3              amd64        GNU Internationalization utilities for the base system
ii  gir1.2-glib-2.0:amd64              1.46.0-3ubuntu1              amd64        Introspection data for GLib, GObject, Gio and GModule
ii  gnupg                              1.4.20-1ubuntu3.1            amd64        GNU privacy guard - a free PGP replacement
ii  gpgv                               1.4.20-1ubuntu3.1            amd64        GNU privacy guard - signature verification tool
ii  grep                               2.25-1~16.04.1               amd64        GNU grep, egrep and fgrep
ii  grub-common                        2.02~beta2-36ubuntu3.2       amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists              0.7                          amd64        GRUB gfxpayload blacklist
ii  grub-pc                            2.02~beta2-36ubuntu3.2       amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                        2.02~beta2-36ubuntu3.2       amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                       2.02~beta2-36ubuntu3.2       amd64        GRand Unified Bootloader (common files for version 2)
ii  gzip                               1.6-4ubuntu1                 amd64        GNU compression utilities
ii  hostname                           3.16ubuntu2                  amd64        utility to set/show the host name or domain name
ii  ifupdown                           0.8.10ubuntu1.1              amd64        high level tools to configure network interfaces
ii  init                               1.29ubuntu3                  amd64        System-V-like init utilities - metapackage
ii  init-system-helpers                1.29ubuntu3                  all          helper tools for all init systems
ii  initramfs-tools                    0.122ubuntu8.5               all          generic modular initramfs generator (automation)
ii  initramfs-tools-bin                0.122ubuntu8.5               amd64        binaries used by initramfs-tools
ii  initramfs-tools-core               0.122ubuntu8.5               all          generic modular initramfs generator (core tools)
ii  initscripts                        2.88dsf-59.3ubuntu2          amd64        scripts for initializing and shutting down the system
ii  insserv                            1.14.0-5ubuntu3              amd64        boot sequence organizer using LSB init.d script dependency information
ii  installation-report                2.60ubuntu1                  all          system installation report
ii  iproute2                           4.3.0-1ubuntu3               amd64        networking and traffic control tools
ii  iputils-ping                       3:20121221-5ubuntu2          amd64        Tools to test the reachability of network hosts
ii  isc-dhcp-client                    4.3.3-5ubuntu12.4            amd64        DHCP client for automatically obtaining an IP address
ii  isc-dhcp-common                    4.3.3-5ubuntu12.4            amd64        common files used by all of the isc-dhcp packages
ii  iso-codes                          3.65-1                       all          ISO language, territory, currency, script codes and their translations
ii  iw                                 3.17-1                       amd64        tool for configuring Linux wireless devices
ii  kbd                                1.15.5-1ubuntu5              amd64        Linux console font and keytable utilities
ii  keyboard-configuration             1.108ubuntu15.2              all          system-wide keyboard preferences
ii  klibc-utils                        2.0.4-8ubuntu1.16.04.2       amd64        small utilities built with klibc for early boot
ii  kmod                               22-1ubuntu4                  amd64        tools for managing Linux kernel modules
ii  language-pack-en                   1:16.04+20161009             all          translation updates for language English
ii  language-pack-en-base              1:16.04+20160627             all          translations for language English
ii  language-pack-gnome-en             1:16.04+20161009             all          GNOME translation updates for language English
ii  language-pack-gnome-en-base        1:16.04+20160627             all          GNOME translations for language English
ii  language-selector-common           0.165.4                      all          Language selector for Ubuntu
ii  laptop-detect                      0.13.7ubuntu2                amd64        attempt to detect a laptop
ii  less                               481-2.1ubuntu0.1             amd64        pager program similar to more
ii  libaccountsservice0:amd64          0.6.40-2ubuntu11.3           amd64        query and manipulate user account information - shared libraries
ii  libacl1:amd64                      2.2.52-3                     amd64        Access control list shared library
ii  libapparmor1:amd64                 2.10.95-0ubuntu2.5           amd64        changehat AppArmor library
ii  libapt-inst2.0:amd64               1.2.15                       amd64        deb package format runtime library
ii  libapt-pkg5.0:amd64                1.2.15                       amd64        package management runtime library
ii  libasprintf0v5:amd64               0.19.7-2ubuntu3              amd64        GNU library to use fprintf and friends in C++
ii  libatm1:amd64                      1:2.5.1-1.5                  amd64        shared library for ATM (Asynchronous Transfer Mode)
ii  libattr1:amd64                     1:2.4.47-2                   amd64        Extended attribute shared library
ii  libaudit-common                    1:2.4.5-1ubuntu2             all          Dynamic library for security auditing - common files
ii  libaudit1:amd64                    1:2.4.5-1ubuntu2             amd64        Dynamic library for security auditing
ii  libblkid1:amd64                    2.27.1-6ubuntu3.1            amd64        block device ID library
ii  libbsd0:amd64                      0.8.2-1                      amd64        utility functions from BSD systems - shared library
ii  libbz2-1.0:amd64                   1.0.6-8                      amd64        high-quality block-sorting file compressor library - runtime
ii  libc-bin                           2.23-0ubuntu4                amd64        GNU C Library: Binaries
ii  libc6:amd64                        2.23-0ubuntu4                amd64        GNU C Library: Shared libraries
ii  libcap-ng0:amd64                   0.7.7-1                      amd64        An alternate POSIX capabilities library
ii  libcap2:amd64                      1:2.24-12                    amd64        POSIX 1003.1e capabilities (library)
ii  libcap2-bin                        1:2.24-12                    amd64        POSIX 1003.1e capabilities (utilities)
ii  libcomerr2:amd64                   1.42.13-1ubuntu1             amd64        common error description library
ii  libcryptsetup4:amd64               2:1.6.6-5ubuntu2             amd64        disk encryption support - shared library
ii  libdb5.3:amd64                     5.3.28-11                    amd64        Berkeley v5.3 Database Libraries [runtime]
ii  libdbus-1-3:amd64                  1.10.6-1ubuntu3.1            amd64        simple interprocess messaging system (library)
ii  libdbus-glib-1-2:amd64             0.106-1                      amd64        simple interprocess messaging system (GLib-based shared library)
ii  libdebconfclient0:amd64            0.198ubuntu1                 amd64        Debian Configuration Management System (C-implementation library)
ii  libdevmapper1.02.1:amd64           2:1.02.110-1ubuntu10         amd64        Linux Kernel Device Mapper userspace library
ii  libdiscover2                       2.1.2-7ubuntu1               amd64        hardware identification library
ii  libdns-export162                   1:9.10.3.dfsg.P4-8ubuntu1.3  amd64        Exported DNS Shared Library
ii  libestr0                           0.1.10-1                     amd64        Helper functions for handling strings (lib)
ii  libexpat1:amd64                    2.1.0-7ubuntu0.16.04.2       amd64        XML parsing C library - runtime library
ii  libfdisk1:amd64                    2.27.1-6ubuntu3.1            amd64        fdisk partitioning library
ii  libffi6:amd64                      3.2.1-4                      amd64        Foreign Function Interface library runtime
ii  libfreetype6:amd64                 2.6.1-0.1ubuntu2             amd64        FreeType 2 font engine, shared library files
ii  libfribidi0:amd64                  0.19.7-1                     amd64        Free Implementation of the Unicode BiDi algorithm
ii  libfuse2:amd64                     2.9.4-1ubuntu3.1             amd64        Filesystem in Userspace (library)
ii  libgcc1:amd64                      1:6.0.1-0ubuntu1             amd64        GCC support library
ii  libgcrypt20:amd64                  1.6.5-2ubuntu0.2             amd64        LGPL Crypto library - runtime library
ii  libgirepository-1.0-1:amd64        1.46.0-3ubuntu1              amd64        Library for handling GObject introspection data (runtime library)
ii  libglib2.0-0:amd64                 2.48.1-1~ubuntu16.04.1       amd64        GLib library of C routines
ii  libglib2.0-data                    2.48.1-1~ubuntu16.04.1       all          Common files for GLib library
ii  libgmp10:amd64                     2:6.1.0+dfsg-2               amd64        Multiprecision arithmetic library
ii  libgnutls-openssl27:amd64          3.4.10-4ubuntu1.1            amd64        GNU TLS library - OpenSSL wrapper
ii  libgnutls30:amd64                  3.4.10-4ubuntu1.1            amd64        GNU TLS library - main runtime library
ii  libgpg-error0:amd64                1.21-2ubuntu1                amd64        library for common error values and messages in GnuPG components
ii  libhogweed4:amd64                  3.2-1                        amd64        low level cryptographic library (public-key cryptos)
ii  libicu55:amd64                     55.1-7                       amd64        International Components for Unicode
ii  libidn11:amd64                     1.32-3ubuntu1.1              amd64        GNU Libidn library, implementation of IETF IDN specifications
ii  libisc-export160                   1:9.10.3.dfsg.P4-8ubuntu1.3  amd64        Exported ISC Shared Library
ii  libjson-c2:amd64                   0.11-4ubuntu2                amd64        JSON manipulation library - shared library
ii  libklibc                           2.0.4-8ubuntu1.16.04.2       amd64        minimal libc subset for use with initramfs
ii  libkmod2:amd64                     22-1ubuntu4                  amd64        libkmod shared library
ii  liblocale-gettext-perl             1.07-1build1                 amd64        module using libc functions for internationalization in Perl
ii  liblz4-1:amd64                     0.0~r131-2ubuntu2            amd64        Fast LZ compression algorithm library - runtime
ii  liblzma5:amd64                     5.1.1alpha+20120614-2ubuntu2 amd64        XZ-format compression library
ii  libmagic1:amd64                    1:5.25-2ubuntu1              amd64        File type determination library using "magic" numbers
ii  libmnl0:amd64                      1.0.3-5                      amd64        minimalistic Netlink communication library
ii  libmount1:amd64                    2.27.1-6ubuntu3.1            amd64        device mounting library
ii  libmpdec2:amd64                    2.4.2-1                      amd64        library for decimal floating point arithmetic (runtime library)
ii  libncurses5:amd64                  6.0+20160213-1ubuntu1        amd64        shared libraries for terminal handling
ii  libncursesw5:amd64                 6.0+20160213-1ubuntu1        amd64        shared libraries for terminal handling (wide character support)
ii  libnettle6:amd64                   3.2-1                        amd64        low level cryptographic library (symmetric and one-way cryptos)
ii  libnewt0.52:amd64                  0.52.18-1ubuntu2             amd64        Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnih1:amd64                      1.0.3-4.3ubuntu1             amd64        NIH Utility Library
ii  libnl-3-200:amd64                  3.2.27-1                     amd64        library for dealing with netlink sockets
ii  libnl-genl-3-200:amd64             3.2.27-1                     amd64        library for dealing with netlink sockets - generic netlink
ii  libp11-kit0:amd64                  0.23.2-5~ubuntu16.04.1       amd64        library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpam-modules:amd64               1.1.8-3.2ubuntu2             amd64        Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                 1.1.8-3.2ubuntu2             amd64        Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                     1.1.8-3.2ubuntu2             all          Runtime support for the PAM library
ii  libpam0g:amd64                     1.1.8-3.2ubuntu2             amd64        Pluggable Authentication Modules library
ii  libpci3:amd64                      1:3.3.1-1.1ubuntu1           amd64        Linux PCI Utilities (shared library)
ii  libpcre3:amd64                     2:8.38-3.1                   amd64        Perl 5 Compatible Regular Expression Library - runtime files
ii  libpng12-0:amd64                   1.2.54-1ubuntu1              amd64        PNG library - runtime
ii  libpolkit-gobject-1-0:amd64        0.105-14.1                   amd64        PolicyKit Authorization API
ii  libpopt0:amd64                     1.16-10                      amd64        lib for parsing cmdline parameters
ii  libprocps4:amd64                   2:3.3.10-4ubuntu2.2          amd64        library for accessing process information from /proc
ii  libpython3-stdlib:amd64            3.5.1-3                      amd64        interactive high-level object-oriented language (default python3 version)
ii  libpython3.5-minimal:amd64         3.5.2-2ubuntu0~16.04.1       amd64        Minimal subset of the Python language (version 3.5)
ii  libpython3.5-stdlib:amd64          3.5.2-2ubuntu0~16.04.1       amd64        Interactive high-level object-oriented language (standard library, version 3.5)
ii  libreadline6:amd64                 6.3-8ubuntu2                 amd64        GNU readline and history libraries, run-time libraries
ii  libseccomp2:amd64                  2.2.3-3ubuntu3               amd64        high level interface to Linux seccomp filter
ii  libselinux1:amd64                  2.4-3build2                  amd64        SELinux runtime shared libraries
ii  libsemanage-common                 2.3-1build3                  all          Common files for SELinux policy management libraries
ii  libsemanage1:amd64                 2.3-1build3                  amd64        SELinux policy management library
ii  libsepol1:amd64                    2.4-2                        amd64        SELinux library for manipulating binary security policies
ii  libslang2:amd64                    2.3.0-2ubuntu1               amd64        S-Lang programming library - runtime version
ii  libsmartcols1:amd64                2.27.1-6ubuntu3.1            amd64        smart column output alignment library
ii  libsqlite3-0:amd64                 3.11.0-1ubuntu1              amd64        SQLite 3 shared library
ii  libss2:amd64                       1.42.13-1ubuntu1             amd64        command-line interface parsing library
ii  libssl1.0.0:amd64                  1.0.2g-1ubuntu4.5            amd64        Secure Sockets Layer toolkit - shared libraries
ii  libstdc++6:amd64                   5.4.0-6ubuntu1~16.04.4       amd64        GNU Standard C++ Library v3
ii  libsystemd0:amd64                  229-4ubuntu12                amd64        systemd utility library
ii  libtasn1-6:amd64                   4.7-3ubuntu0.16.04.1         amd64        Manage ASN.1 structures (runtime)
ii  libtext-charwidth-perl             0.04-7build5                 amd64        get display widths of characters on the terminal
ii  libtext-iconv-perl                 1.7-5build4                  amd64        converts between character sets in Perl
ii  libtext-wrapi18n-perl              0.06-7.1                     all          internationalized substitute of Text::Wrap
ii  libtinfo5:amd64                    6.0+20160213-1ubuntu1        amd64        shared low-level terminfo library for terminal handling
ii  libudev1:amd64                     229-4ubuntu12                amd64        libudev shared library
ii  libusb-0.1-4:amd64                 2:0.1.12-28                  amd64        userspace USB programming library
ii  libusb-1.0-0:amd64                 2:1.0.20-1                   amd64        userspace USB programming library
ii  libustr-1.0-1:amd64                1.0.4-5                      amd64        Micro string library: shared library
ii  libuuid1:amd64                     2.27.1-6ubuntu3.1            amd64        Universally Unique ID library
ii  libxml2:amd64                      2.9.3+dfsg1-1ubuntu0.1       amd64        GNOME XML library
ii  libxtables11:amd64                 1.6.0-2ubuntu3               amd64        netfilter xtables library
ii  linux-base                         4.0ubuntu1                   all          Linux image base package
ii  linux-firmware                     1.157.5                      all          Firmware for Linux kernel drivers
ii  linux-generic                      4.4.0.51.54                  amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-51             4.4.0-51.72                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.51.54                  amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-51-generic       4.4.0-51.72                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic 4.4.0-51.72                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.51.54                  amd64        Generic Linux kernel image
ii  locales                            2.23-0ubuntu4                all          GNU C Library: National Language (locale) data [support]
ii  login                              1:4.2-3.1ubuntu5             amd64        system login tools
ii  logrotate                          3.8.7-2ubuntu2               amd64        Log rotation utility
ii  lsb-base                           9.20160110ubuntu0.2          all          Linux Standard Base init script functionality
ii  lsb-release                        9.20160110ubuntu0.2          all          Linux Standard Base version reporting utility
ii  makedev                            2.3.1-93ubuntu1              all          creates device files in /dev
ii  mawk                               1.3.3-17ubuntu2              amd64        a pattern scanning and text processing language
ii  mime-support                       3.59ubuntu1                  all          MIME files 'mime.types' & 'mailcap', and support programs
ii  mount                              2.27.1-6ubuntu3.1            amd64        tools for mounting and manipulating filesystems
ii  multiarch-support                  2.23-0ubuntu4                amd64        Transitional package to ensure multiarch compatibility
ii  ncurses-base                       6.0+20160213-1ubuntu1        all          basic terminal type definitions
ii  ncurses-bin                        6.0+20160213-1ubuntu1        amd64        terminal-related programs and man pages
ii  net-tools                          1.60-26ubuntu1               amd64        NET-3 networking toolkit
ii  netbase                            5.3                          all          Basic TCP/IP networking system
ii  netcat-openbsd                     1.105-7ubuntu1               amd64        TCP/IP swiss army knife
ii  os-prober                          1.70ubuntu3                  amd64        utility to detect other OSes on a set of drives
ii  passwd                             1:4.2-3.1ubuntu5             amd64        change and administer password and group data
ii  pciutils                           1:3.3.1-1.1ubuntu1           amd64        Linux PCI Utilities
ii  perl-base                          5.22.1-9                     amd64        minimal Perl system
ii  procps                             2:3.3.10-4ubuntu2.2          amd64        /proc file system utilities
ii  python-apt-common                  1.1.0~beta1build1            all          Python interface to libapt-pkg (locales)
ii  python3                            3.5.1-3                      amd64        interactive high-level object-oriented language (default python3 version)
ii  python3-apt                        1.1.0~beta1build1            amd64        Python 3 interface to libapt-pkg
ii  python3-dbus                       1.2.0-3                      amd64        simple interprocess messaging system (Python 3 interface)
ii  python3-gi                         3.20.0-0ubuntu1              amd64        Python 3 bindings for gobject-introspection libraries
ii  python3-minimal                    3.5.1-3                      amd64        minimal subset of the Python language (default python3 version)
ii  python3.5                          3.5.2-2ubuntu0~16.04.1       amd64        Interactive high-level object-oriented language (version 3.5)
ii  python3.5-minimal                  3.5.2-2ubuntu0~16.04.1       amd64        Minimal subset of the Python language (version 3.5)
ii  readline-common                    6.3-8ubuntu2                 all          GNU readline and history libraries, common files
ii  resolvconf                         1.78ubuntu2                  all          name server information handler
ii  rsyslog                            8.16.0-1ubuntu3              amd64        reliable system and kernel logging daemon
ii  sed                                4.2.2-7                      amd64        The GNU sed stream editor
ii  sensible-utils                     0.0.9                        all          Utilities for sensible alternative selection
ii  sgml-base                          1.26+nmu4ubuntu1             all          SGML infrastructure and SGML catalog file support
ii  shared-mime-info                   1.5-2ubuntu0.1               amd64        FreeDesktop.org shared MIME database and spec
ii  sudo                               1.8.16-0ubuntu1.2            amd64        Provide limited super user privileges to specific users
ii  systemd                            229-4ubuntu12                amd64        system and service manager
ii  systemd-sysv                       229-4ubuntu12                amd64        system and service manager - SysV links
ii  sysv-rc                            2.88dsf-59.3ubuntu2          all          System-V-like runlevel change mechanism
ii  sysvinit-utils                     2.88dsf-59.3ubuntu2          amd64        System-V-like utilities
ii  tar                                1.28-2.1ubuntu0.1            amd64        GNU version of the tar archiving utility
ii  tasksel                            3.34ubuntu3                  all          tool for selecting tasks for installation on Debian systems
ii  tasksel-data                       3.34ubuntu3                  all          official tasks used for installation of Debian systems
ii  tzdata                             2016h-0ubuntu0.16.04         all          time zone and daylight-saving time data
ii  ubuntu-keyring                     2012.05.19                   all          GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                     1.361                        amd64        Minimal core of Ubuntu
ii  ucf                                3.0036                       all          Update Configuration File(s): preserve user changes to config files
ii  udev                               229-4ubuntu12                amd64        /dev/ and hotplug management daemon
ii  ureadahead                         0.100.0-19                   amd64        Read required files in advance
ii  usbutils                           1:007-4                      amd64        Linux USB utilities
ii  util-linux                         2.27.1-6ubuntu3.1            amd64        miscellaneous system utilities
ii  vim-common                         2:7.4.1689-3ubuntu1.2        amd64        Vi IMproved - Common files
ii  vim-tiny                           2:7.4.1689-3ubuntu1.2        amd64        Vi IMproved - enhanced vi editor - compact version
ii  wamerican                          7.1-1                        all          American English dictionary words for /usr/share/dict
ii  wbritish                           7.1-1                        all          British English dictionary words for /usr/share/dict
ii  whiptail                           0.52.18-1ubuntu2             amd64        Displays user-friendly dialog boxes from shell scripts
ii  wireless-regdb                     2015.07.20-1ubuntu1          all          wireless regulatory database
ii  xdg-user-dirs                      0.15-2ubuntu6                amd64        tool to manage well known user directories
ii  xkb-data                           2.16-1ubuntu1                all          X Keyboard Extension (XKB) configuration data
ii  xml-core                           0.13+nmu2                    all          XML infrastructure and XML catalog file support
ii  zlib1g:amd64                       1:1.2.8.dfsg-2ubuntu4        amd64        compression library - runtime

```

---

### Post by loyhz2ayj-jeff on 2016-12-14
Thanks for the link to the mini isos.

---

