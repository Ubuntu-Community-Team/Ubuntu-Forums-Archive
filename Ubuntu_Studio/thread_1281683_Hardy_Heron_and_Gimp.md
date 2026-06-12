---
title: "Hardy Heron and Gimp"
date: 2009-10-03
forum: Ubuntu Studio
---

### Post by th1bill on 2009-10-03
I followed some bad advise and tried to upgrade my Gimp t 2.6.  The following is what I did t get ito this mess;

th1bill@th1bill-desktop:~$ sudo apt-get remove gimp --purge
[sudo] password for th1bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnomescan0 libgutenprintui2-1 libgnomescanui-common libgnomescanui0
  libgnomescan-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flegita-gimp* gimp* gimp-gnomevfs* gimp-gutenprint* gimp-python*
  gimp-resynthesizer* gimp-texturize*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 13.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 216824 files and directories currently installed.)
Removing flegita-gimp ...
Removing gimp-texturize ...
Removing gimp-resynthesizer ...
Removing gimp-gutenprint ...
Removing gimp-python ...
Removing gimp-gnomevfs ...
Removing gimp ...
Purging configuration files for gimp ...
th1bill@th1bill-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
th1bill@th1bill-desktop:~$ sudo su
root@th1bill-desktop:/home/th1bill# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnomescan0 libgutenprintui2-1 libgnomescanui-common libgnomescanui0
  libgnomescan-common
The following packages will be REMOVED:
  libgnomescan-common libgnomescan0 libgnomescanui-common libgnomescanui0
  libgutenprintui2-1
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 1147kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 216503 files and directories currently installed.)
Removing libgnomescanui0 ...
Removing libgnomescan0 ...
Removing libgnomescan-common ...
Removing libgnomescanui-common ...
Removing libgutenprintui2-1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@th1bill-desktop:/home/th1bill# ~$ wget [http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb](http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb)
bash: ~$: command not found
root@th1bill-desktop:/home/th1bill# wget [http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb](http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb)
--12:45:18--  [http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb](http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb)
           => `libgimp2.0_2.6.0-1~getdeb1_i386.deb'
Resolving cesium.di.uminho.pt... 193.136.19.148
Connecting to cesium.di.uminho.pt|193.136.19.148|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,032,442 (1008K) [application/octet-stream]

100%[====================================>] 1,032,442     37.08K/s    ETA 00:00

12:45:40 (47.99 KB/s) - `libgimp2.0_2.6.0-1~getdeb1_i386.deb' saved [1032442/1032442]

root@th1bill-desktop:/home/th1bill# dpkg -i  libgimp2.0_2.6.0-1~getdeb1_i386.deb
(Reading database ... 216446 files and directories currently installed.)
Preparing to replace libgimp2.0 2.4.5-1ubuntu2 (using libgimp2.0_2.6.0-1~getdeb1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
Setting up libgimp2.0 (2.6.0-1~getdeb1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@th1bill-desktop:/home/th1bill# wget [http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb](http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb)
--12:50:51--  [http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb](http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb)
           => `libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb'
Resolving getdeb.agetta.de... 62.146.32.89
Connecting to getdeb.agetta.de|62.146.32.89|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:50:52 ERROR 404: Not Found.

root@th1bill-desktop:/home/th1bill# wget [http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb](http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb)
--12:51:41--  [http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb](http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb)
           => `libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb'
Resolving getdeb.agetta.de... 62.146.32.89
Connecting to getdeb.agetta.de|62.146.32.89|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:51:42 ERROR 404: Not Found.

root@th1bill-desktop:/home/th1bill# dpkg -i libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb
dpkg: error processing libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb
root@th1bill-desktop:/home/th1bill# apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (< 2.4.5-z) but 2.6.0-1~getdeb1 is to be installed
E: Broken packages
root@th1bill-desktop:/home/th1bill# apt-get install libgimp2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgimp2.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@th1bill-desktop:/home/th1bill# apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (< 2.4.5-z) but 2.6.0-1~getdeb1 is to be installed
E: Broken packages
root@th1bill-desktop:/home/th1bill# apt-get install gimp
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@th1bill-desktop:/home/th1bill# apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (< 2.4.5-z) but 2.6.0-1~getdeb1 is to be installed
E: Broken packages
 Is the a way out of this without a reinstall of my complete OS?

---

### Post by ibuclaw on 2009-10-03
```

sudo aptitude purge libgimp2.0
sudo apt-get install gimp

```

Regards
Iain

---

### Post by ibuclaw on 2009-10-03
FYI, do don't need a terminal to upgrade GIMP: [http://www.getdeb.net/app/GIMP](http://www.getdeb.net/app/GIMP)

---

### Post by th1bill on 2009-10-03
Thank you very, very much.  The other advice seems to have left out the purge and I was lost.  I took your advise and downloaded the five pkgs. and the foud the proper order for installation on tombuntu.

---

