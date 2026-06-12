---
title: "Unsupported memory accesses after Installing Xen On Ubuntu 8.04"
date: 2009-12-09
forum: Server Platforms
---

### Post by petervanbussel on 2009-12-09
HowTo used: [http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories]("[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories")(http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories"]http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories[/URL)]
on: Ubuntu 8.04. Server LTS on SuperMicro 5013C-MTB (P4, 4GB, RAID1(soft)2x250GB)
 
Dear all,
 
Despite of moving /lib/tls
```

mv /lib/tls /lib/tls.disabled

```
I get this warning:
```

***************************************************************
***************************************************************
** WARNING: Currently emulating unsupported memory accesses **
** in /lib/tls glibc libraries. The emulation is **
** slow. To ensure full performance you should **
** install a 'xen-friendly' (nosegneg) version of **
** the library, or disable tls support by executing **
** the following as root: **
** mv /lib/tls /lib/tls.disabled **
** Offending process: init (pid=2710) **
***************************************************************
***************************************************************

```
I looked at [_[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/246625[/COLOR][/SIZE][/COLOR][/SIZE]_]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/246625")
[SIZE=2]and [/SIZE][_[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260825[/COLOR][/SIZE][/COLOR][/SIZE]_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260825") :
 
I re-enabled /tls/tls and tried to load xen-friendly library but no luck (see below, no nosegneg for libc). I also tried version 2.6.24-19-xen and changed to hwcap 0 nosegneg but still no luck... Any suggestions (extra info see below)?
 
Regards, Peter
 
Info:
```

uname -r
2.6.24-26-xen

```
```

cat /proc/version_signature
Ubuntu 2.6.24-4.6-generic

```
```

ls /boot
abi-2.6.24-24-server initrd.img-2.6.24-26-xen.bak
config-2.6.24-19-xen lost+found
config-2.6.24-24-server memtest86+.bin
config-2.6.24-26-xen System.map-2.6.24-19-xen
grub
System.map-2.6.24-24-server
initrd.img-2.6.24-19-xen System.map-2.6.24-26-xen
initrd.img-2.6.24-19-xen.bak vmlinuz-2.6.24-19-xen
initrd.img-2.6.24-24-server vmlinuz-2.6.24-24-server
initrd.img-2.6.24-24-server.bak vmlinuz-2.6.24-26-xen
initrd.img-2.6.24-26-xen xen-3.2.gz

```
```

ldd /sbin/init 
linux-gate.so.1 => (0xf57fe000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e55000)
/lib/ld-linux.so.2 (0xb7fab000)

```
```

ldconfig -p
 
libusb-0.1.so.4 (libc6) => /usr/lib/libusb-0.1.so.4
        libuniquewm-1.0.so.0 (libc6) => /usr/lib/libuniquewm-1.0.so.0
        libulockmgr.so.1 (libc6) => /lib/libulockmgr.so.1
        libtiff.so.4 (libc6) => /usr/lib/libtiff.so.4
        libticw.so.5 (libc6) => /lib/libticw.so.5
        libtic.so.5 (libc6) => /lib/libtic.so.5
        libthread_db.so.1 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libthread_db.so.1
        libthread_db.so.1 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libthread_db.so.1
        libthread_db.so.1 (libc6, OS ABI: Linux 2.6.8) => /lib/libthread_db.so.1
        libthai.so.0 (libc6) => /usr/lib/libthai.so.0
        libtasn1.so.3 (libc6) => /usr/lib/libtasn1.so.3
        libsysfs.so.2 (libc6) => /lib/libsysfs.so.2
        libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
        libssl.so.0.9.8 (libc6, hwcap: 0x0008000000008000) => /usr/lib/i686/cmov/libssl.so.0.9.8
        libssl.so.0.9.8 (libc6, hwcap: 0x0004000000000000) => /usr/lib/i586/libssl.so.0.9.8
        libssl.so.0.9.8 (libc6, hwcap: 0x0002000000000000) => /usr/lib/i486/libssl.so.0.9.8
        libssl.so.0.9.8 (libc6) => /usr/lib/libssl.so.0.9.8
        libss.so.2 (libc6) => /lib/libss.so.2
        libsqlite3.so.0 (libc6) => /usr/lib/libsqlite3.so.0
        libslang.so.2 (libc6) => /lib/libslang.so.2
        libsigc-2.0.so.0 (libc6) => /usr/lib/libsigc-2.0.so.0
        libsepol.so.1 (libc6) => /lib/libsepol.so.1
        libselinux.so.1 (libc6) => /lib/libselinux.so.1
        libsasl2.so.2 (libc6) => /usr/lib/libsasl2.so.2
        libruby1.8.so.1.8 (libc6) => /usr/lib/libruby1.8.so.1.8
        librt.so.1 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/librt.so.1
        librt.so.1 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/librt.so.1
        librt.so.1 (libc6, OS ABI: Linux 2.6.8) => /lib/librt.so.1
        libresolv.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libresolv.so.2
        libresolv.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libresolv.so.2
        libresolv.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libresolv.so.2
        libreadline.so.5 (libc6) => /lib/libreadline.so.5
        libpython2.5.so.1.0 (libc6) => /usr/lib/libpython2.5.so.1.0
        libpython2.5.so (libc6) => /usr/lib/libpython2.5.so
        libpthread.so.0 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libpthread.so.0
        libpthread.so.0 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libpthread.so.0
        libpthread.so.0 (libc6, OS ABI: Linux 2.6.8) => /lib/libpthread.so.0
        libproc-3.2.7.so (libc6) => /lib/libproc-3.2.7.so
        libpopt.so.0 (libc6) => /lib/libpopt.so.0
        libpng12.so.0 (libc6) => /usr/lib/libpng12.so.0
        libpixman-1.so.0 (libc6) => /usr/lib/libpixman-1.so.0
        libperl.so.5.8 (libc6) => /usr/lib/libperl.so.5.8
        libpcreposix.so.3 (libc6) => /usr/lib/libpcreposix.so.3
        libpcre.so.3 (libc6) => /usr/lib/libpcre.so.3
        libpcprofile.so (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libpcprofile.so
        libpcprofile.so (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libpcprofile.so
        libpcprofile.so (libc6, OS ABI: Linux 2.6.8) => /lib/libpcprofile.so
        libpcap.so.0.8 (libc6) => /usr/lib/libpcap.so.0.8
        libparted-1.7.so.1 (libc6) => /lib/libparted-1.7.so.1
        libpangoxft-1.0.so.0 (libc6) => /usr/lib/libpangoxft-1.0.so.0
        libpangox-1.0.so.0 (libc6) => /usr/lib/libpangox-1.0.so.0
        libpangoft2-1.0.so.0 (libc6) => /usr/lib/libpangoft2-1.0.so.0
        libpangocairo-1.0.so.0 (libc6) => /usr/lib/libpangocairo-1.0.so.0
        libpango-1.0.so.0 (libc6) => /usr/lib/libpango-1.0.so.0
        libpanelw.so.5 (libc6) => /usr/lib/libpanelw.so.5
        libpanel.so.5 (libc6) => /usr/lib/libpanel.so.5
        libpamc.so.0 (libc6) => /lib/libpamc.so.0
        libpam_misc.so.0 (libc6) => /lib/libpam_misc.so.0
        libpam.so.0 (libc6) => /lib/libpam.so.0
        libopencdk.so.10 (libc6) => /usr/lib/libopencdk.so.10
        libopcodes-2.18.0.20080103.so (libc6) => /usr/lib/libopcodes-2.18.0.20080103.so
        libntfs-3g.so.23 (libc6) => /lib/libntfs-3g.so.23
        libnss_nisplus.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnss_nisplus.so.2
        libnss_nisplus.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnss_nisplus.so.2
        libnss_nisplus.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libnss_nisplus.so.2
        libnss_nis.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnss_nis.so.2
        libnss_nis.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnss_nis.so.2
        libnss_nis.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libnss_nis.so.2
        libnss_hesiod.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnss_hesiod.so.2
        libnss_hesiod.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnss_hesiod.so.2
        libnss_hesiod.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libnss_hesiod.so.2
        libnss_files.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnss_files.so.2
        libnss_files.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnss_files.so.2
        libnss_files.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libnss_files.so.2
        libnss_dns.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnss_dns.so.2
        libnss_dns.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnss_dns.so.2
        libnss_dns.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libnss_dns.so.2
        libnss_compat.so.2 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnss_compat.so.2
        libnss_compat.so.2 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnss_compat.so.2
        libnss_compat.so.2 (libc6, OS ABI: Linux 2.6.8) => /lib/libnss_compat.so.2
        libnsl.so.1 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libnsl.so.1
        libnsl.so.1 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libnsl.so.1
        libnsl.so.1 (libc6, OS ABI: Linux 2.6.8) => /lib/libnsl.so.1
        libnewt.so.0.52 (libc6) => /usr/lib/libnewt.so.0.52
        libncursesw.so.5 (libc6) => /lib/libncursesw.so.5
        libncurses.so.5 (libc6) => /lib/libncurses.so.5
        libmenuw.so.5 (libc6) => /usr/lib/libmenuw.so.5
        libmenu.so.5 (libc6) => /usr/lib/libmenu.so.5
        libmemusage.so (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libmemusage.so
        libmemusage.so (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libmemusage.so
        libmemusage.so (libc6, OS ABI: Linux 2.6.8) => /lib/libmemusage.so
        libmagic.so.1 (libc6) => /usr/lib/libmagic.so.1
        libm.so.6 (libc6, hwcap: 0x8028000000000000, OS ABI: Linux 2.6.8) => /lib/tls/i686/nosegneg/libm.so.6
        libm.so.6 (libc6, hwcap: 0x8008000000008000, OS ABI: Linux 2.6.8) => /lib/tls/i686/cmov/libm.so.6
        libm.so.6 (libc6, OS ABI: Linux 2.6.8) => /lib/libm.so.6
        liblzo2.so.2 (libc6) => /usr/lib/liblzo2.so.2
        liblwres.so.30 (libc6) => /usr/lib/liblwres.so.30
        libldap_r-2.4.so.2 (libc6) => /usr/lib/libldap_r-2.4.so.2
        liblber-2.4.so.2 (libc6) => /usr/lib/liblber-2.4.so.2
        libk5crypto.so.3 (libc6) => /usr/lib/libk5crypto.so.3
        libkrb5support.so.0 (libc6) => /usr/lib/libkrb5support.so.0
        libkrb5.so.3 (libc6) => /usr/lib/libkrb5.so.3
        libkrb4.so.2 (libc6) => /usr/lib/libkrb4.so.2
        libkeyutils.so.1 (libc6) => /lib/libkeyutils.so.1
        libjpeg.so.62 (libc6) => /usr/lib/libjpeg.so.62
        libiw.so.29 (libc6) => /lib/libiw.so.29
        libisccfg.so.30 (libc6) => /usr/lib/libisccfg.so.30
        libisccc.so.30 (libc6) => /usr/lib/libisccc.so.30
        libisc.so.35 (libc6) => /usr/lib/libisc.so.35
        libidn.so.11 (libc6) => /usr/lib/libidn.so.11
        libhistory.so.5 (libc6) => /lib/libhistory.so.5
        libhal.so.1 (libc6) => /usr/lib/libhal.so.1
        libhal-storage.so.1 (libc6) => /usr/lib/libhal-storage.so.1
        libgtk-x11-2.0.so.0 (libc6) => /usr/lib/libgtk-x11-2.0.so.0
        libgthread-2.0.so.0 (libc6) => /usr/lib/libgthread-2.0.so.0
        libgssapi_krb5.so.2 (libc6) => /usr/lib/libgssapi_krb5.so.2
        libgpm.so.1 (libc6) => /usr/lib/libgpm.so.1
        libgpg-error.so.0 (libc6) => /lib/libgpg-error.so.0
        libgobject-2.0.so.0 (libc6) => /usr/lib/libgobject-2.0.so.0
        libgnutls.so.13 (libc6) => /usr/lib/libgnutls.so.13
        libgnutls-openssl.so.13 (libc6) => /usr/lib/libgnutls-openssl.so.13
        libgnutls-extra.so.13 (libc6) => /usr/lib/libgnutls-extra.so.13
        libgnomevfs-2.so.0 (libc6) => /usr/lib/libgnomevfs-2.so.0
        libgnomeui-2.so.0 (libc6) => /usr/lib/libgnomeui-2.so.0
        libgnomecanvas-2.so.0 (libc6) => /usr/lib/libgnomecanvas-2.so.0
        libgnome-2.so.0 (libc6) => /usr/lib/libgnome-2.so.0
        libgnome-keyring.so.0 (libc6) => /usr/lib/libgnome-keyring.so.0
        libgmodule-2.0.so.0 (libc6) => /usr/lib/libgmodule-2.0.so.0
        libglib-2.0.so.0 (libc6) => /usr/lib/libglib-2.0.so.0
        libglade-2.0.so.0 (libc6) => /usr/lib/libglade-2.0.so.0
        libgio-2.0.so.0 (libc6) => /usr/lib/libgio-2.0.so.0
        libgdk_pixbuf_xlib-2.0.so.0 (libc6) => /usr/lib/libgdk_pixbuf_xlib-2.0.so.0
        libgdk_pixbuf-2.0.so.0 (libc6) => /usr/lib/libgdk_pixbuf-2.0.so.0
        libgdk-x11-2.0.so.0 (libc6) => /usr/lib/libgdk-x11-2.0.so.0
        libgdbm_compat.so.3 (libc6) => /usr/lib/libgdbm_compat.so.3
        libgdbm.so.3 (libc6) => /usr/lib/libgdbm.so.3
        libgcrypt.so.11 (libc6) => /lib/libgcrypt.so.11
        libgconf-2.so.4 (libc6) => /usr/lib/libgconf-2.so.4
        libgccpp.so.1 (libc6) => /usr/lib/libgccpp.so.1
        libgcc_s.so.1 (libc6) => /lib/libgcc_s.so.1
        libgc.so.1 (libc6) => /usr/lib/libgc.so.1
        libgamin-1.so.0 (libc6) => /usr/lib/libgamin-1.so.0
        libgailutil.so.18 (libc6) => /usr/lib/libgailutil.so.18
        libfusion-1.0.so.0 (libc6) => /usr/lib/libfusion-1.0.so.0
        libfuse.so.2 (libc6) => /lib/libfuse.so.2
        libfsimage.so.1.0 (libc6) => /usr/lib/libfsimage.so.1.0
        libfribidi.so.0 (libc6) => /usr/lib/libfribidi.so.0
        libfreetype.so.6 (libc6) => /usr/lib/libfreetype.so.6
        libformw.so.5 (libc6) => /usr/lib/libformw.so.5
        libform.so.5 (libc6) => /usr/lib/libform.so.5
        libfontconfig.so.1 (libc6) => /usr/lib/libfontconfig.so.1
        libflask.so.1.0 (libc6) => /usr/lib/libflask.so.1.0

```

---

