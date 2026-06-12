---
title: "webmin issue"
date: 2009-05-23
forum: Server Platforms
---

### Post by salim.madni on 2009-05-23
dear gurus

i have a new test installation server ubbuntu 8.10 server

so i try to install webmin it give me this error below

root@test:/software# dpkg --install webmin_1.470_all.deb
(Reading database ... 51279 files and directories currently installed.)
Preparing to replace webmin 1.470 (using webmin_1.470_all.deb) ...
Unpacking replacement webmin ...
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

then i found documentation on internet that below package installed also some packages i cant find, can some one look into it.

root@test:/software# apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl is already the newest version.
perl set to manually installed.
Package libnet-ssleay-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libnet-ssleay-perl has no installation candidate

kindly advise for all above how to fixed, how to get. internet is working, can i install above package from cd-rom or not?

regards
salim

---

### Post by Aearenda on 2009-05-23
After you finished installation, did you successfully run ```
sudo apt-get update
```with main, universe and multiverse enabled?
It sounds as though your server does not know about the repositories. Please post the contents of /etc/apt/sources.list if the above did not help.

EDIT: This is from the Webmin installation [instructions]("http://webmin.com/deb.html"): > If you are installing on Ubuntu and the apt-get command reports that some of the packages cannot be found, edit /etc/apt/sources.list and make sure the lines ending with universe are not commented out.So it sounds like it does not need multiverse. It won't be on the CD though.

---

