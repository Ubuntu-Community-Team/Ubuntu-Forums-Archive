---
title: "webmin / vps problem"
date: 2008-11-22
forum: Server Platforms
---

### Post by Bashed on 2008-11-22
Trying to install webmin on a Ubuntu vps using the debian package.


root@server:/# wget [http://internap.dl.sourceforge.net/s..._1.441_all.deb]("http://internap.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb")
--17:30:01--  [http://internap.dl.sourceforge.net/s..._1.441_all.deb]("http://internap.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb")
           => `webmin_1.441_all.deb'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,820,054 (13M) [text/plain]

100%[=======================================================================================================================================>] 13,820,054 1.11M/s ETA 00:00

17:30:13 (1.10 MB/s) - `webmin_1.441_all.deb' saved [13820054/13820054]



root@server:/# dpkg --install webmin_1.441_all.deb
dpkg: status database area is locked by another process
root@server:/# dpkg --install webmin_1.441_all.deb
Selecting previously deselected package webmin.
(Reading database ... 35536 files and directories currently installed.)
Unpacking webmin (from webmin_1.441_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin



root@server:/# apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
Reading package lists... Done
Building dependency tree... Done
perl is already the newest version.
Package libnet-ssleay-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libnet-ssleay-perl has no installation candidate
root@server:/# 


Anyone? Using Ubuntu 7.0.4 vps o/s (ez-template).

---

