---
title: "Debain package manager"
date: 2008-10-24
forum: Server Platforms
---

### Post by Alpha01 on 2008-10-24
Hello,

I'd find it strange by not be able to find a dpkg that will show the version number of a particular package. Similar to rpm -i. Its intreaged that something this simple isn't fully or well document

---

### Post by StickyStyle on 2008-10-24
It does, just with a capital "I".  It's in the man file.

```

administrator@vmx1:~$ dpkg -I dellomsa_5.4.0-1_i386.deb 
 new debian package, version 2.0.
 size 74281592 bytes: control archive= 1527 bytes.
     192 bytes,     8 lines      conffiles            
     370 bytes,    10 lines      control              
     376 bytes,    10 lines      control.amd64        
    1763 bytes,    88 lines   *  postinst             #!/bin/sh
     702 bytes,    42 lines   *  postrm               #!/bin/sh
 Package: dellomsa
 Version: 5.4.0-1
 Section: admin
 Priority: extra 
 Architecture: i386
 Depends: openipmi (>= 2.0.2), lsb-base, libxml2, libstdc++5, rpm, procmail
 Installed-Size: 221M
 Maintainer: Bas van der Vlies <basv@sara.nl> and Jaap Dijkshoorn <jaap@sara.nl>
 Description: Dell OpenManage Server Administrator 5.
  OMSA is a hardware monitoring and configuration tool.

```

---

