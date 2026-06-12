---
title: "FAM and Courier-IMAP"
date: 2005-09-26
forum: Server Platforms
---

### Post by skgu67 on 2005-09-26
Not that it's critical, but I was interested in allowing real-time updating of users IMAP folders via the EnhancedIdle setting and FAM (see [http://www.courier-mta.org/?imapd.html)](http://www.courier-mta.org/?imapd.html)). But the Ubuntu packages for courier-imap and fam seem to be mutually incompatible. Anybody have any thoughts?

Thanks in advance.

PS -- accidentally posted this in the Desktop portion of the forums first, sorry for the cross-post

---

### Post by mbwardle on 2005-10-07
Ubuntu replaced FAM with Gamin.  Install Gamin and it should work fine.

You can verify this with
```
$ apt-cache show courier-imap
Package: courier-imap
Priority: extra
Section: mail
Installed-Size: 2512
Maintainer: Stefan Hornburg (Racke) <racke@linuxia.de>
Architecture: i386
Source: courier (0.47-3ubuntu5)
Version: 3.0.8-3ubuntu5
Replaces: imap-server
Provides: imap-server
Depends: libc6 (>= 2.3.4-1), **libgamin0**, libgdbm3, postfix | mail-transport-agent, courier-base (>= 0.47), courier-authdaemon (>= 0.47), lsb-base (>= 1.3-9ubuntu3)
Suggests: courier-doc, imap-client, courier-imap-ssl
Conflicts: imap-server
Filename: pool/main/c/courier/courier-imap_3.0.8-3ubuntu5_i386.deb
Size: 930400
MD5sum: 7a67d05d77df472e008071b335434829
Description: Courier Mail Server - IMAP server
 The Courier IMAP server provides access to email stored in Maildirs.
 This server has an extremely small footprint, provides shared and
 virtual shared folders.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

```
$ apt-cache show libgamin0
Package: libgamin0
Priority: optional
Section: libs
Installed-Size: 112
Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: gamin
Version: 0.1.5-0ubuntu1
Replaces: libfam0c102, libfam0
Provides: libfam0c102, libfam0
Depends: libc6 (>= 2.3.4-1), gamin
Conflicts: **libfam0c102, libfam0**
Filename: pool/main/g/gamin/libgamin0_0.1.5-0ubuntu1_i386.deb
Size: 31922
MD5sum: 1251281bc8fbd68707fb636c39afc501
Description: Client library for the gamin file and directory monitoring system
 Client library for the gamin file and directory monitoring system
 .
 Gamin is a file and directory monitoring system defined to be a
 subset of the FAM (File Alteration Monitor) system.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: edubuntu-desktop
```

---

