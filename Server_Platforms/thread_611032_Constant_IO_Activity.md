---
title: "Constant I/O Activity"
date: 2007-11-12
forum: Server Platforms
---

### Post by sasanf on 2007-11-12
I'm running 7.10.  There is constant activity on the HDD.  My Processors are running at around 60-80% all the time.  I've checked the Processes via the System Monitor and all processes are sleeping.  Could this be caused by a virus.  There is no reason for constant activity on the HDD.

---

### Post by pete.dawgg on 2007-11-13
you might check with lsof.

---

### Post by sasanf on 2007-11-13
What is lsof?  For the purpose of giving more information:

Inspiron 6400
Ubuntu 7.10

Third Party Software:

NDIS Wrapper (Windows version of Dell 1394 WLAN Driver)
Blender
VLC
Did have Rosegarden installed (just removed it via autoremove)
WINE
Thunderbird
Adobe Flash Player

As I am writing this my 2 Core CPU is getting hammered.

---

### Post by NilsHG on 2007-11-13
is your ram full and hdd access is caused by swap activity?
dunno how much blender takes up... just a thougt.

---

### Post by sasanf on 2007-11-13
lsof output:

gnome-ter 25631   superman  mem       REG        8,2      1128 1605727 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      2120 1605724 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      1216 1605714 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      8888 1605712 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2     11272 1605728 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      4672 1605684 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      3040 1605725 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      3296 1605689 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      2152 1605709 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2     17928 1605704 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2     16656 1605686 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      6528 1605702 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      8256 1605696 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      2120 1605721 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      2984 1605692 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      8744 1605690 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2     22840 1605688 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      1400 1605706 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2     29472 1611454 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      4320 1605707 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2     14016 1605713 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      8312 1605697 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
gnome-ter 25631   superman  mem       REG        8,2      1584 4506367 /usr/share/vte/termcap/xterm
gnome-ter 25631   superman  mem       REG        8,2   2167716 4375665 /usr/share/icons/hicolor/icon-theme.cache
gnome-ter 25631   superman  mem       REG        8,2   7726648 4377285 /usr/share/icons/gnome/icon-theme.cache
gnome-ter 25631   superman  mem       REG        8,2    155216 4112864 /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
gnome-ter 25631   superman  mem       REG        8,2     38420 4834259 /lib/tls/i686/cmov/libnss_files-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     34352 4834261 /lib/tls/i686/cmov/libnss_nis-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     30436 4834257 /lib/tls/i686/cmov/libnss_compat-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2      5384 1769705 /usr/lib/gconv/ISO8859-1.so
gnome-ter 25631   superman  mem       REG        8,2     15016 4112903 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-ter 25631   superman  mem       REG        8,2    254020 4113658 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-ter 25631   superman  mem       REG        8,2        54 4113663 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-ter 25631   superman  mem       REG        8,2      2451 4113666 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-ter 25631   superman  mem       REG        8,2    915322 4113657 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-ter 25631   superman  mem       REG        8,2       286 4113661 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-ter 25631   superman  mem       REG        8,2        52 4128820 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-ter 25631   superman  mem       REG        8,2        34 4113664 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-ter 25631   superman  mem       REG        8,2    219668 4800637 /lib/libsepol.so.1
gnome-ter 25631   superman  mem       REG        8,2    327244 4064791 /usr/lib/libgcrypt.so.11.2.3
gnome-ter 25631   superman  mem       REG        8,2     11436 4064898 /usr/lib/libgpg-error.so.0.3.0
gnome-ter 25631   superman  mem       REG        8,2     60916 4065266 /usr/lib/libtasn1.so.3.0.9
gnome-ter 25631   superman  mem       REG        8,2     83712 4834256 /lib/tls/i686/cmov/libnsl-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2    806112 4064619 /usr/lib/libasound.so.2.0.0
gnome-ter 25631   superman  mem       REG        8,2     26816 4064776 /usr/lib/libgailutil.so.18.0.1
gnome-ter 25631   superman  mem       REG        8,2    139768 4063976 /usr/lib/libpng12.so.0.15.0
gnome-ter 25631   superman  mem       REG        8,2    130364 4064754 /usr/lib/libexpat.so.1.0.0
gnome-ter 25631   superman  mem       REG        8,2     16616 4064563 /usr/lib/libXdmcp.so.6.0.0
gnome-ter 25631   superman  mem       REG        8,2      6988 4064552 /usr/lib/libXau.so.6.0.0
gnome-ter 25631   superman  mem       REG        8,2      9700 4834269 /lib/tls/i686/cmov/libutil-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     83516 4800636 /lib/libselinux.so.1
gnome-ter 25631   superman  mem       REG        8,2     67408 4834265 /lib/tls/i686/cmov/libresolv-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     59728 4064631 /usr/lib/libavahi-client.so.3.2.2
gnome-ter 25631   superman  mem       REG        8,2     41896 4064633 /usr/lib/libavahi-common.so.3.4.4
gnome-ter 25631   superman  mem       REG        8,2      9392 4064637 /usr/lib/libavahi-glib.so.1.0.1
gnome-ter 25631   superman  mem       REG        8,2    457092 4064894 /usr/lib/libgnutls.so.13.3.0
gnome-ter 25631   superman  mem       REG        8,2    213060 4064694 /usr/lib/libdbus-1.so.3.3.0
gnome-ter 25631   superman  mem       REG        8,2    110136 4064696 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-ter 25631   superman  mem       REG        8,2    273124 4800591 /lib/libncurses.so.5.6
gnome-ter 25631   superman  mem       REG        8,2     80504 4065330 /usr/lib/libz.so.1.2.3.3
gnome-ter 25631   superman  mem       REG        8,2    452396 4064768 /usr/lib/libfreetype.so.6.3.16
gnome-ter 25631   superman  mem       REG        8,2     43548 4063351 /usr/lib/libpangox-1.0.so.0.1800.3
gnome-ter 25631   superman  mem       REG        8,2    183644 4063349 /usr/lib/libpangoft2-1.0.so.0.1800.3
gnome-ter 25631   superman  mem       REG        8,2     24236 4063353 /usr/lib/libpangoxft-1.0.so.0.1800.3
gnome-ter 25631   superman  mem       REG        8,2     70164 4064573 /usr/lib/libXft.so.2.1.2
gnome-ter 25631   superman  mem       REG        8,2     17360 4064538 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-ter 25631   superman  mem       REG        8,2    140420 4064629 /usr/lib/libaudiofile.so.0.0.2
gnome-ter 25631   superman  mem       REG        8,2     41000 4064745 /usr/lib/libesd.so.0.2.38
gnome-ter 25631   superman  mem       REG        8,2     87440 4064524 /usr/lib/libICE.so.6.3.0
gnome-ter 25631   superman  mem       REG        8,2     28092 4064542 /usr/lib/libSM.so.6.0.0
gnome-ter 25631   superman  mem       REG        8,2    125316 4065040 /usr/lib/libjpeg.so.62.0.0
gnome-ter 25631   superman  mem       REG        8,2     55172 4064862 /usr/lib/libgnome-keyring.so.0.1.1
gnome-ter 25631   superman  mem       REG        8,2     30624 4834266 /lib/tls/i686/cmov/librt-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     14264 4064958 /usr/lib/libgthread-2.0.so.0.1400.1
gnome-ter 25631   superman  mem       REG        8,2     85024 4064617 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-ter 25631   superman  mem       REG        8,2    197120 4064872 /usr/lib/libgnomecanvas-2.so.0.2000.0
gnome-ter 25631   superman  mem       REG        8,2    378872 4064652 /usr/lib/libbonoboui-2.so.0.0.0
gnome-ter 25631   superman  mem       REG        8,2   1166856 4065324 /usr/lib/libxml2.so.2.6.30
gnome-ter 25631   superman  mem       REG        8,2      9684 4834253 /lib/tls/i686/cmov/libdl-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     10212 4064856 /usr/lib/libgmodule-2.0.so.0.1400.1
gnome-ter 25631   superman  mem       REG        8,2     14128 4064569 /usr/lib/libXfixes.so.3.1.0
gnome-ter 25631   superman  mem       REG        8,2    481048 4064656 /usr/lib/libcairo.so.2.11.5
gnome-ter 25631   superman  mem       REG        8,2      5992 4064561 /usr/lib/libXdamage.so.1.1.0
gnome-ter 25631   superman  mem       REG        8,2      6716 4064557 /usr/lib/libXcomposite.so.1.0.0
gnome-ter 25631   superman  mem       REG        8,2     32800 4064559 /usr/lib/libXcursor.so.1.0.2
gnome-ter 25631   superman  mem       REG        8,2     22136 4064587 /usr/lib/libXrandr.so.2.1.0
gnome-ter 25631   superman  mem       REG        8,2     29112 4064575 /usr/lib/libXi.so.6.0.0
gnome-ter 25631   superman  mem       REG        8,2      6464 4064577 /usr/lib/libXinerama.so.1.0.0
gnome-ter 25631   superman  mem       REG        8,2     56156 4064567 /usr/lib/libXext.so.6.4.0
gnome-ter 25631   superman  mem       REG        8,2    176144 4064760 /usr/lib/libfontconfig.so.1.2.0
gnome-ter 25631   superman  mem       REG        8,2     33456 4063347 /usr/lib/libpangocairo-1.0.so.0.1800.3
gnome-ter 25631   superman  mem       REG        8,2   1339816 4834250 /lib/tls/i686/cmov/libc-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2    112423 4834264 /lib/tls/i686/cmov/libpthread-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2    986540 4064546 /usr/lib/libX11.so.6.2.0
gnome-ter 25631   superman  mem       REG        8,2     28744 4064589 /usr/lib/libXrender.so.1.3.0
gnome-ter 25631   superman  mem       REG        8,2    772908 4064846 /usr/lib/libglib-2.0.so.0.1400.1
gnome-ter 25631   superman  mem       REG        8,2    241168 4064896 /usr/lib/libgobject-2.0.so.0.1400.1
gnome-ter 25631   superman  mem       REG        8,2    248248 4063345 /usr/lib/libpango-1.0.so.0.1800.3
gnome-ter 25631   superman  mem       REG        8,2    336936 4064534 /usr/lib/libORBit-2.so.0.1.0
gnome-ter 25631   superman  mem       REG        8,2    200484 4064789 /usr/lib/libgconf-2.so.4.1.2
gnome-ter 25631   superman  mem       REG        8,2    360096 4064888 /usr/lib/libgnomevfs-2.so.0.2000.0
gnome-ter 25631   superman  mem       REG        8,2    149332 4834254 /lib/tls/i686/cmov/libm-2.6.1.so
gnome-ter 25631   superman  mem       REG        8,2     93256 4064808 /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
gnome-ter 25631   superman  mem       REG        8,2    105312 4064625 /usr/lib/libatk-1.0.so.0.2009.1
gnome-ter 25631   superman  mem       REG        8,2    551944 4064806 /usr/lib/libgdk-x11-2.0.so.0.1200.0
gnome-ter 25631   superman  mem       REG        8,2   3680184 4064961 /usr/lib/libgtk-x11-2.0.so.0.1200.0
gnome-ter 25631   superman  mem       REG        8,2    739128 4065297 /usr/lib/libvte.so.9.2.13
gnome-ter 25631   superman  mem       REG        8,2     31308 4065258 /usr/lib/libstartup-notification-1.so.0.0.0
gnome-ter 25631   superman  mem       REG        8,2     86888 4064650 /usr/lib/libbonobo-activation.so.4.0.0
gnome-ter 25631   superman  mem       REG        8,2    371976 4064648 /usr/lib/libbonobo-2.so.0.0.0
gnome-ter 25631   superman  mem       REG        8,2     27144 4800626 /lib/libpopt.so.0.0.0
gnome-ter 25631   superman  mem       REG        8,2     85892 4064858 /usr/lib/libgnome-2.so.0.2000.0
gnome-ter 25631   superman  mem       REG        8,2    568132 4063675 /usr/lib/libgnomeui-2.so.0.2000.1
gnome-ter 25631   superman  mem       REG        8,2     95188 4064844 /usr/lib/libglade-2.0.so.0.0.7
gnome-ter 25631   superman  mem       REG        8,2     10580 4065052 /usr/lib/liblaunchpad-integration.so.0.0.0
gnome-ter 25631   superman  mem       REG        8,2        77 4113662 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-ter 25631   superman  mem       REG        8,2       155 4113656 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-ter 25631   superman  mem       REG        8,2        59 4113665 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-ter 25631   superman  mem       REG        8,2        23 4113660 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-ter 25631   superman  mem       REG        8,2     25486 1736705 /usr/lib/gconv/gconv-modules.cache
gnome-ter 25631   superman  mem       REG        8,2       373 4113659 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-ter 25631   superman  mem       REG        8,2    109148 4800525 /lib/ld-2.6.1.so
gnome-ter 25631   superman    0r      CHR        1,3              8799 /dev/null
gnome-ter 25631   superman    1w     FIFO        0,6             18167 pipe
gnome-ter 25631   superman    2w     FIFO        0,6             18167 pipe
gnome-ter 25631   superman    3u     unix 0xc6d49c40             53333 socket
gnome-ter 25631   superman    4r     FIFO        0,6             53335 pipe
gnome-ter 25631   superman    5w     FIFO        0,6             53335 pipe
gnome-ter 25631   superman    6r     FIFO        0,6             53336 pipe
gnome-ter 25631   superman    7w     FIFO        0,6             53336 pipe
gnome-ter 25631   superman    8r     FIFO        0,6             53337 pipe
gnome-ter 25631   superman    9w     FIFO        0,6             53337 pipe
gnome-ter 25631   superman   10u     unix 0xc6d49540             53338 socket
gnome-ter 25631   superman   11u     unix 0xc6d498c0             53348 socket
gnome-ter 25631   superman   12u     unix 0xe9969700             53350 /tmp/orbit-superman/linc-641f-0-2807633a85cfe
gnome-ter 25631   superman   13u     unix 0xe811f540             53353 /tmp/orbit-superman/linc-641f-0-2807633a85cfe
gnome-ter 25631   superman   14u     unix 0xc6d47e00             53357 /tmp/orbit-superman/linc-641f-0-2807633a85cfe
gnome-ter 25631   superman   15u     unix 0xe9ab41c0             53354 socket
gnome-ter 25631   superman   16u      CHR        5,2              4351 /dev/ptmx
gnome-ter 25631   superman   17r     FIFO        0,6             53372 pipe
gnome-ter 25631   superman   18u     unix 0xe9ab4700             53361 socket
gnome-ter 25631   superman   19w     FIFO        0,6             53372 pipe
gnome-ter 25631   superman   20r     FIFO        0,6             53373 pipe
gnome-ter 25631   superman   21w     FIFO        0,6             53373 pipe
gnome-pty 25634   superman  cwd   unknown                              /proc/25634/cwd (readlink: Permission denied)
gnome-pty 25634   superman  rtd   unknown                              /proc/25634/root (readlink: Permission denied)
gnome-pty 25634   superman  txt   unknown                              /proc/25634/exe (readlink: Permission denied)
gnome-pty 25634   superman NOFD                                        /proc/25634/fd (opendir: Permission denied)
bash      25635   superman  cwd       DIR        8,2      4096 1490962 /home/superman
bash      25635   superman  rtd       DIR        8,2      4096       2 /
bash      25635   superman  txt       REG        8,2    701680 4554757 /bin/bash
bash      25635   superman  mem       REG        8,2     38420 4834259 /lib/tls/i686/cmov/libnss_files-2.6.1.so
bash      25635   superman  mem       REG        8,2     34352 4834261 /lib/tls/i686/cmov/libnss_nis-2.6.1.so
bash      25635   superman  mem       REG        8,2     83712 4834256 /lib/tls/i686/cmov/libnsl-2.6.1.so
bash      25635   superman  mem       REG        8,2     30436 4834257 /lib/tls/i686/cmov/libnss_compat-2.6.1.so
bash      25635   superman  mem       REG        8,2    254020 4113658 /usr/lib/locale/en_US.utf8/LC_CTYPE
bash      25635   superman  mem       REG        8,2        54 4113663 /usr/lib/locale/en_US.utf8/LC_NUMERIC
bash      25635   superman  mem       REG        8,2      2451 4113666 /usr/lib/locale/en_US.utf8/LC_TIME
bash      25635   superman  mem       REG        8,2    915322 4113657 /usr/lib/locale/en_US.utf8/LC_COLLATE
bash      25635   superman  mem       REG        8,2       286 4113661 /usr/lib/locale/en_US.utf8/LC_MONETARY
bash      25635   superman  mem       REG        8,2        52 4128820 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
bash      25635   superman  mem       REG        8,2        34 4113664 /usr/lib/locale/en_US.utf8/LC_PAPER
bash      25635   superman  mem       REG        8,2   1339816 4834250 /lib/tls/i686/cmov/libc-2.6.1.so
bash      25635   superman  mem       REG        8,2      9684 4834253 /lib/tls/i686/cmov/libdl-2.6.1.so
bash      25635   superman  mem       REG        8,2    273124 4800591 /lib/libncurses.so.5.6
bash      25635   superman  mem       REG        8,2        77 4113662 /usr/lib/locale/en_US.utf8/LC_NAME
bash      25635   superman  mem       REG        8,2       155 4113656 /usr/lib/locale/en_US.utf8/LC_ADDRESS
bash      25635   superman  mem       REG        8,2        59 4113665 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
bash      25635   superman  mem       REG        8,2        23 4113660 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
bash      25635   superman  mem       REG        8,2     25486 1736705 /usr/lib/gconv/gconv-modules.cache
bash      25635   superman  mem       REG        8,2       373 4113659 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
bash      25635   superman  mem       REG        8,2    109148 4800525 /lib/ld-2.6.1.so
bash      25635   superman    0u      CHR      136,0                 2 /dev/pts/0
bash      25635   superman    1u      CHR      136,0                 2 /dev/pts/0
bash      25635   superman    2u      CHR      136,0                 2 /dev/pts/0
bash      25635   superman  255u      CHR      136,0                 2 /dev/pts/0
pdf_filte 25654   superman  cwd       DIR        8,2      4096 1490962 /home/superman
pdf_filte 25654   superman  rtd       DIR        8,2      4096       2 /
pdf_filte 25654   superman  txt       REG        8,2     80308 4554777 /bin/dash
pdf_filte 25654   superman  mem       REG        8,2   1339816 4834250 /lib/tls/i686/cmov/libc-2.6.1.so
pdf_filte 25654   superman  mem       REG        8,2    109148 4800525 /lib/ld-2.6.1.so
pdf_filte 25654   superman    0r      CHR        1,3              8799 /dev/null
pdf_filte 25654   superman    1w      CHR        1,3              8799 /dev/null
pdf_filte 25654   superman    2w      CHR        1,3              8799 /dev/null
pdf_filte 25654   superman   10r      REG        8,2        66 4196013 /usr/lib/tracker/filters/application/pdf_filter
pdftotext 25655   superman  cwd       DIR        8,2      4096 1490962 /home/superman
pdftotext 25655   superman  rtd       DIR        8,2      4096       2 /
pdftotext 25655   superman  txt       REG        8,2     13300 4064037 /usr/bin/pdftotext
pdftotext 25655   superman  mem       REG        8,2     22880 1605708 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      8280 1605722 /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     12424 1605705 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      1880 1605715 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      1168 1605695 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     10080 1605710 /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      3600 1605701 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     21816 1606164 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      7312 1605719 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     30352 1605723 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     20616 1605687 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      1624 1605693 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      7792 1605720 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     21672 1605717 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     13136 1605685 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      5184 1607776 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      1128 1605727 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      2120 1605724 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      1216 1605714 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      8888 1605712 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     11272 1605728 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      4672 1605684 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      3040 1605725 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      3296 1605689 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      2152 1605709 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     17928 1605704 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     16656 1605686 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      6528 1605702 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      8256 1605696 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      2120 1605721 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      2984 1605692 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      8744 1605690 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     22840 1605688 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     29472 1611454 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      9684 4834253 /lib/tls/i686/cmov/libdl-2.6.1.so
pdftotext 25655   superman  mem       REG        8,2    130364 4064754 /usr/lib/libexpat.so.1.0.0
pdftotext 25655   superman  mem       REG        8,2     80504 4065330 /usr/lib/libz.so.1.2.3.3
pdftotext 25655   superman  mem       REG        8,2    452396 4064768 /usr/lib/libfreetype.so.6.3.16
pdftotext 25655   superman  mem       REG        8,2   1166856 4065324 /usr/lib/libxml2.so.2.6.30
pdftotext 25655   superman  mem       REG        8,2    125316 4065040 /usr/lib/libjpeg.so.62.0.0
pdftotext 25655   superman  mem       REG        8,2    112423 4834264 /lib/tls/i686/cmov/libpthread-2.6.1.so
pdftotext 25655   superman  mem       REG        8,2   1339816 4834250 /lib/tls/i686/cmov/libc-2.6.1.so
pdftotext 25655   superman  mem       REG        8,2     42700 4800579 /lib/libgcc_s.so.1
pdftotext 25655   superman  mem       REG        8,2    149332 4834254 /lib/tls/i686/cmov/libm-2.6.1.so
pdftotext 25655   superman  mem       REG        8,2    970680 4065260 /usr/lib/libstdc++.so.6.0.9
pdftotext 25655   superman  mem       REG        8,2    176144 4064760 /usr/lib/libfontconfig.so.1.2.0
pdftotext 25655   superman  mem       REG        8,2   1651160 4065182 /usr/lib/libpoppler.so.2.0.0
pdftotext 25655   superman  mem       REG        8,2      1400 1605706 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      4320 1605707 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2     14016 1605713 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2      8312 1605697 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
pdftotext 25655   superman  mem       REG        8,2    109148 4800525 /lib/ld-2.6.1.so
pdftotext 25655   superman    0r      CHR        1,3              8799 /dev/null
pdftotext 25655   superman    1w      CHR        1,3              8799 /dev/null
pdftotext 25655   superman    2w      CHR        1,3              8799 /dev/null
pdftotext 25655   superman    3r      REG        8,2   4013223 3180680 /home/superman/Documents/How To's/11G Documentation/java.111/b31225.pdf
pdftotext 25655   superman    4w      REG        8,2    249856  671784 /tmp/Tracker-superman.5695/tmp_text_file_1IOI1T
lsof      25656   superman  cwd       DIR        8,2      4096 1490962 /home/superman
lsof      25656   superman  rtd       DIR        8,2      4096       2 /
lsof      25656   superman  txt       REG        8,2    106272 4063900 /usr/bin/lsof
lsof      25656   superman  mem       REG        8,2    254020 4113658 /usr/lib/locale/en_US.utf8/LC_CTYPE
lsof      25656   superman  mem       REG        8,2   1339816 4834250 /lib/tls/i686/cmov/libc-2.6.1.so
lsof      25656   superman  mem       REG        8,2     25486 1736705 /usr/lib/gconv/gconv-modules.cache
lsof      25656   superman  mem       REG        8,2    109148 4800525 /lib/ld-2.6.1.so
lsof      25656   superman    0u      CHR      136,0                 2 /dev/pts/0
lsof      25656   superman    1u      CHR      136,0                 2 /dev/pts/0
lsof      25656   superman    2u      CHR      136,0                 2 /dev/pts/0
lsof      25656   superman    3r      DIR        0,3         0       1 /proc
lsof      25656   superman    4r      DIR        0,3         0   53398 /proc/25656/fd
lsof      25656   superman    5w     FIFO        0,6             53401 pipe
lsof      25656   superman    6r     FIFO        0,6             53402 pipe
lsof      25657   superman  cwd       DIR        8,2      4096 1490962 /home/superman
lsof      25657   superman  rtd       DIR        8,2      4096       2 /
lsof      25657   superman  txt       REG        8,2    106272 4063900 /usr/bin/lsof
lsof      25657   superman  mem       REG        8,2    254020 4113658 /usr/lib/locale/en_US.utf8/LC_CTYPE
lsof      25657   superman  mem       REG        8,2   1339816 4834250 /lib/tls/i686/cmov/libc-2.6.1.so
lsof      25657   superman  mem       REG        8,2     25486 1736705 /usr/lib/gconv/gconv-modules.cache
lsof      25657   superman  mem       REG        8,2    109148 4800525 /lib/ld-2.6.1.so
lsof      25657   superman    4r     FIFO        0,6             53401 pipe
lsof      25657   superman    7w     FIFO        0,6             53402 pipe

---

