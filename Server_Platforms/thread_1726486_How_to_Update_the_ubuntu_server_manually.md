---
title: "How to Update the ubuntu server manually"
date: 2011-04-11
forum: Server Platforms
---

### Post by thoufiq on 2011-04-11
I want to update the ubuntu server manually and i am installing packages or libraries manually (i.e in offline) in ubuntu server 10.10(32-bit). I had downloaded the files from _[COLOR=Red]http://packages.ubuntu.com/maverick/libs/[/COLOR]_, while installing these packages it shows error like this

root@dhcppc4:/opt/commonshare1/packages#[COLOR=Magenta]sudo dpkg --install libc-bin_2.12.1-0ubuntu10.1_i386.deb[/COLOR]
dpkg-deb: unexpected end of file in version number in libc-bin_2.12.1-0ubuntu10.1_i386.deb
dpkg: error processing libc-bin_2.12.1-0ubuntu10.1_i386.deb (--install):
subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
libc-bin_2.12.1-0ubuntu10.1_i386.deb

These are the packages or libraries i had downloaded:

              libapparmor1_2.5.1-0ubuntu0.10.10.3_i386.deb
              libbind9-60_9.7.1.dfsg.P2-2ubuntu0.2_i386.deb
              libblkid1_2.17.2-0ubuntu1.10.10.1_i386.deb
              libc6_2.12.1-0ubuntu10.1_i386.deb
              libcairo2_1.10.0-1ubuntu2_i386.deb
[COLOR=Magenta]               libc-bin_2.12.1-0ubuntu10.1_i386.deb[/COLOR]
              libdbus-1-3_1.4.0-0ubuntu1.1_i386.deb
              libdns66_9.7.1.dfsg.P2-2ubuntu0.2_i386.deb

Pls suggest me to overcome this error.

---

