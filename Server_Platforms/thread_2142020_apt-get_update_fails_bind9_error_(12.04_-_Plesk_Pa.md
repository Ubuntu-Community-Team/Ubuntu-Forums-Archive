---
title: "apt-get update fails bind9 error (12.04 - Plesk Panel v11.0.9)"
date: 2013-05-04
forum: Server Platforms
---

### Post by chj-se on 2013-05-04
I am having issues with bind9 in a Plesk Server.

Running:
Parallels Plesk Panel v11.0.9_build110120608.16 os_Ubuntu 12.04

On:
Ubuntu 12.04.2 LTS

Any assistance is appreciated as this is a live server.


```

root@web01:/usr/local/psa/bin# apt-get upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  bind9
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 340 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://no.archive.ubuntu.com/ubuntu/ precise-updates/main bind9 amd64 1:9.8.1.dfsg.P1-4ubuntu0.6 [340 kB]
Fetched 340 kB in 0s (770 kB/s)
dpkg: dependency problems prevent configuration of bind9:
 bind9 depends on libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of libbind9-80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
 bind9 depends on libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of libdns81 on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
 bind9 depends on libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of libisc83 on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
 bind9 depends on libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of libisccc80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
 bind9 depends on libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of libisccfg82 on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
 bind9 depends on liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of liblwres80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
 bind9 depends on bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of bind9utils on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.
dpkg: error processing bind9 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by SeijiSensei on 2013-05-04
>  bind9 depends on bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.3); however:
  Version of bind9utils on system is 1:9.8.1.dfsg.P1-4ubuntu0.6.

This looks like a packaging error to me as the dependencies all require specific versions.  Usually packagers set a minimum version number and accept packages like yours with versions more recent than the requirement.

I noticed the error about holding back the kernel updates.  Have you considered trying "sudo apt-get dist-upgrade" and then giving bind9 a try?

---

