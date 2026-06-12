---
title: "error to remove tftpd-hpa"
date: 2008-09-03
forum: Server Platforms
---

### Post by jpgeerets on 2008-09-03
hi folks,

this morning i tryed to make a apt-get dist-upgrade to upgrade from 610 (edgy) to 804.

during this upgrade, i get an error message:
> 
Preparing to replace tftpd-hpa 0.42-1ubuntu2 (using .../tftpd-hpa_0.43-1ubuntu2_i386.deb) ...
Stopping HPA's tftpd: in.tftpdinvoke-rc.d: initscript tftpd-hpa, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping HPA's tftpd: in.tftpdinvoke-rc.d: initscript tftpd-hpa, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/tftpd-hpa_0.43-1ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting HPA's tftpd: in.tftpdinvoke-rc.d: initscript tftpd-hpa, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 66
Errors were encountered while processing:
 /var/cache/apt/archives/tftpd-hpa_0.43-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


it seems due to the failer of tftpd-hpa my distupgrade will not work too. 
someone can give me advice on how to remove the tftpd-hpa?

thanks in advaced!

Jean-Paul

---

