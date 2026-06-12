---
title: "LTSP-BUILD-CLIENT --arch i386 is not generating pxelinux.0 and config files"
date: 2011-07-09
forum: Server Platforms
---

### Post by Bakyt Niyazov on 2011-07-09
Hello I am running Ubuntu 11.04 64bit and was building ltsp-build-client --arch i386.

All went well and DHCP is working fine. The only issue is that the /var/lib/tftboot is just empty. There are no folders which should be generated like ltsp and ltsp/i386.

The clients are issuing "File Not Found" error.

The question is: How can I regenerate those files? the only image file is at /opt/ltsp/images/nbi.img but I think this is not related??

Thank you!

---

### Post by Bakyt Niyazov on 2011-07-09
UPDATE: But when I use just ltsp-build-client it creates the pxelinux.0 and all other files under /var/lib/tftpboot/ltsp/amd64.... so for some reasons it's not creating for i386... ;(

---

### Post by Bakyt Niyazov on 2011-07-10
I copied from /opt/ltsp/i386/boot to /var/lib/tftpboot/ltsp/i386
and everything is working fine now.

P.S: Still don't know why the files are not being generated as for amd64

---

