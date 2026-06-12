---
title: "Precise | Synaptic Install (no internet)"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cates044 on 2012-04-06
I'm trying to uninstall the broadcom wifi drivers (bcmwl-kernal-source) on my dell inspiron 1501 so that I can install the correct drivers. The problem is I have no way of connecting to the internet to download synaptic package manager to do so. I have tried to manually install synaptic deb but I get an error "Dependency is not satisfiable: libept1.4.12".

How else can I remove the bcmwl drivers without internet and Synaptic? Or how can I get synaptic installed manually?


Thanks

Dell Inspiron 1501
Ubuntu 12.04 b2

---

### Post by jpeddicord on 2012-04-06
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by garvinrick4 on 2012-04-06
[https://launchpad.net/ubuntu/+source/b43-fwcutter/1:014-9/+build/2672932](https://launchpad.net/ubuntu/+source/b43-fwcutter/1:014-9/+build/2672932)

The link is for 32 bit if need 64 bit will be in launchpad.net also. 

Go to website above and download the built packages on any computer and copy to flash drive. 
These two built packages in .deb below.
b43 cutter.deb
firmware b43 installer all.deb

drag and drop to desktop from flash drive to desktop.
```
cd Desktop
``````
sudo dpkg -i *.deb
```Second line of code install all .deb on Desktop so make sure you only have on desktop what you want installed. 

Now reboot your computer and your b43 drivers should load no problem. 
When you do install Synaptic you can type b43 in search and will show your installed drivers.
Must have all other bcm drivers not installed. Type bcm in search in synaptic and make sure nothing installed only your b43 should be installed. 

####If you have a router should be able to wire from router to machine?? Can download from there??

```
sudo apt-get purge "name of package"
``` (without qoutes) will remove a package.

---

### Post by cates044 on 2012-04-06
Thank you very much for the response.

I downloaded and installed the deb files as you instructed, but after reboot wifi is still not working. There was an error after installing the debs
```
(Reading database ... 127288 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:014-9 (using b43-fwcutter_014-9_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Preparing to replace firmware-b43-installer 1:014-9 (using firmware-b43-installer_014-9_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Setting up b43-fwcutter (1:014-9) ...
Processing triggers for man-db ...
Setting up firmware-b43-installer (1:014-9) ...
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2012-04-06 20:32:37--  http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... failed: Name or service not known.
wget: unable to resolve host address `mirror2.openwrt.org'
dpkg: error processing firmware-b43-installer (--install):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
```

> ####If you have a router should be able to wire from router to machine?? Can download from there??
Unfortunately the ethernet port on my dell does not work.

> sudo apt-get purge "name of package"
When I try
```
sudo apt-get purge bcmwl-kernal-source
```
I get a ```
E: Unable to locate package bcmwl-kernal-source
```

---

