---
title: "errors: Ubuntu /sbin/ldconfig.real: is not a symbolic link on a VM with no GUI"
date: 2019-10-17
forum: Server Platforms
---

### Post by michael.gorn on 2019-10-17
```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial
```


[COLOR=#242729][FONT=Arial]Whenever I run apt-get upgrade on my Ubuntu 16 LTS, I get these errors:

[/FONT][/COLOR]
```
/sbin/ldconfig.real: /usr/lib/libext2fs.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libply.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libnl-3.so.200 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libply-splash-core.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libusb-0.1.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libseccomp.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libgcrypt.so.20 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libss.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpopt.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libkmod.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libsystemd.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpci.so.3 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libudev.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpcre.so.3 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/ld-linux-x86-64.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libhistory.so.5 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libcryptsetup.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libmnl.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libfdisk.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libdbus-1.so.3 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libtinfo.so.5 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpamc.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/liblzma.so.5 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libcgmanager.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libply-boot-client.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpng12.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libjson-c.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libisc-export.so.160 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libtirpc.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libreadline.so.6 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libxtables.so.11 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libparted.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libfuse.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libnih-dbus.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libsmartcols.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libe2p.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libntfs-3g.so.861 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libcom_err.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libdns-export.so.162 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libz.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libncursesw.so.5 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libip4tc.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libiptc.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libmount.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libacl.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libattr.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libuuid.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpcsclite.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libexpat.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/liblzo2.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libusb-1.0.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libcap.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libnl-genl-3.so.200 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libglib-2.0.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libprocps.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libhistory.so.6 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libply-splash-graphics.so.4 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libwrap.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libncurses.so.5 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libulockmgr.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libip6tc.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libreadline.so.5 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpam.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libnewt.so.0.52 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libapparmor.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libblkid.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libslang.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libnih.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libbsd.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libaudit.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libkeyutils.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libpam_misc.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libbz2.so.1.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libgpg-error.so.0 is not a symbolic link

```

[COLOR=#242729][FONT=Arial]What could be causing these and how to fix?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I upgraded to Ubuntu 18 using do-release-upgrade and still get exactly the same errors when running ldconfig. This on a command-line only VM with no graphics drivers - run-level 3.
[/FONT][/COLOR]
```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
```


[COLOR=#242729][FONT=Arial]Output of ldconfig -p and grep -r deb /etc/apt/source* is here: [https://gist.github.com/omegagx/551a62dfbc00c7e41a93d7eb1591b597](https://gist.github.com/omegagx/551a62dfbc00c7e41a93d7eb1591b597)[/FONT][/COLOR]

---

