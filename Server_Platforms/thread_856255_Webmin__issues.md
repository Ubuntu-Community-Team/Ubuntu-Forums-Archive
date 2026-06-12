---
title: "Webmin  issues"
date: 2008-07-11
forum: Server Platforms
---

### Post by bad8174 on 2008-07-11
Ok, I installed webmin the way another site told me to install it. I think it installed correctly, because if I go to a web browser it gives me the message "It Works". But I cannot do anything past this. I want to use Ubuntu to host our website, so I need a web interface to configure it. Im really new to Ubuntu and Linux, and Im trying to keep this server headless. Do I need to load modules? If so what modules do I load and what are the cmds?

---

### Post by godhead1772 on 2008-07-11
silly question but did you add the port to the url?


https://yourserver:10000

---

### Post by magicplayr2000 on 2008-07-11
Go to the web browser and type https://<your ip or server name>:10000

Webmin listens on port 10000 by default instead of port 80

---

### Post by bad8174 on 2008-07-11
Yea, I tried that but I get a page cannot be displayed. So maybe the webmin didnt install correctly?

---

### Post by bad8174 on 2008-07-11
Ok I did a port scan from the desktop interface and I dont show a port 10000 open. So Im guessing the port 80 is actually there from the default apache install. So now, how do I install the webmin?

---

### Post by bad8174 on 2008-07-11
Ok, I think im on the right track. Im getting another error now Here is the output copy

root@Web:/home/bobby# sudo apt-get install perl libnet-ssleay openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl is already the newest version.
perl set to manually installed.
E: Couldn't find package libnet-ssleay
root@Web:/home/bobby# wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb)
--10:11:29--  [http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb)
           => `webmin_1.340_all.deb'
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://voxel.dl.sourceforge.net/sourceforge/webadmin/webmin_1.340_all.deb](http://voxel.dl.sourceforge.net/sourceforge/webadmin/webmin_1.340_all.deb) [following]
--10:11:30--  [http://voxel.dl.sourceforge.net/sourceforge/webadmin/webmin_1.340_all.deb](http://voxel.dl.sourceforge.net/sourceforge/webadmin/webmin_1.340_all.deb)
           => `webmin_1.340_all.deb'
Resolving voxel.dl.sourceforge.net... 208.122.28.18, 208.122.28.3, 208.122.28.2
Connecting to voxel.dl.sourceforge.net|208.122.28.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,532,434 (15M) [application/x-debian-package]

100%[====================================>] 15,532,434   177.10K/s    ETA 00:00

10:13:00 (173.67 KB/s) - `webmin_1.340_all.deb' saved [15532434/15532434]

root@Web:/home/bobby# sudo dpkg -i webmin_1.340_all.deb
(Reading database ... 98185 files and directories currently installed.)
Unpacking webmin (from webmin_1.340_all.deb) ...
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

---

