---
title: "Home Server 10.04 - upgrade hangs on mysql"
date: 2010-08-11
forum: Server Platforms
---

### Post by MrWES on 2010-08-11
Been trying to upgrade home server for several days and it keeps hanging on the mysql upgrade. Here's the what apt-get says:

```
administrator@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt-transport-https apt-utils binutils byobu clamav clamav-base clamav-daemon clamav-freshclam cmake cmake-data cups cups-client cups-common cupsys cupsys-client
  dpkg-dev ghostscript ghostscript-cups gvfs gvfs-backends icedtea-6-jre-cacao krb5-multidev language-selector-common libatk1.0-0 libclamav6 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib1 libdbusmenu-gtk1 libgail18 libglib2.0-data libgnome-keyring0 libgs8 libgssapi-krb5-2 libgssrpc4
  libgtk2.0-0 libgtk2.0-common libgvfscommon0 libk5crypto3 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libkrb5-3 libkrb5-dev libkrb5support0 libldap-2.4-2 libldap2-dev
  libnotify1 libopenal1 libpam-runtime libpam0g libparted0debian1 libpcsclite1 libpng12-0 libpng12-dev libpoppler5 libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa
  libsnmp-base libsnmp15 libsoup-gnome2.4-1 libsoup2.4-1 libtiff4 libusb-0.1-4 linux-firmware linux-generic linux-generic-pae linux-image-generic linux-image-generic-pae
  linux-image-server linux-server mysql-server-5.1 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssh-client openssh-server parted poppler-utils python-apt
  ssh sudo udisks update-manager-core ureadahead w3m
91 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7,435kB/89.1MB of archives.
After this operation, 7,750kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libldap2-dev 2.4.21-0ubuntu5.2 [902kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libldap-2.4-2 2.4.21-0ubuntu5.2 [202kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-core 1:0.134.10 [199kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main w3m 0.5.2-2.1ubuntu1.1 [1,103kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main libclamav6 0.96.1+dfsg-3ubuntu5~lucid1 [3,705kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav-daemon 0.96.1+dfsg-3ubuntu5~lucid1 [404kB]                                                          
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav-base 0.96.1+dfsg-3ubuntu5~lucid1 [294kB]                                                            
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav-freshclam 0.96.1+dfsg-3ubuntu5~lucid1 [304kB]                                                       
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav 0.96.1+dfsg-3ubuntu5~lucid1 [322kB]                                                                 
Fetched 7,435kB in 10s (714kB/s)                                                                                                                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up apt (0.7.25.3ubuntu9.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 87542 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12 (using .../mysql-server-5.1_5.1.41-3ubuntu12.6_i386.deb) ...

```

---

### Post by hudsonl on 2010-08-11
> **MrWES said:**
> Been trying to upgrade home server for several days and it keeps hanging on the mysql upgrade. Here's the what apt-get says:

```
administrator@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt-transport-https apt-utils binutils byobu clamav clamav-base clamav-daemon clamav-freshclam cmake cmake-data cups cups-client cups-common cupsys cupsys-client
  dpkg-dev ghostscript ghostscript-cups gvfs gvfs-backends icedtea-6-jre-cacao krb5-multidev language-selector-common libatk1.0-0 libclamav6 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib1 libdbusmenu-gtk1 libgail18 libglib2.0-data libgnome-keyring0 libgs8 libgssapi-krb5-2 libgssrpc4
  libgtk2.0-0 libgtk2.0-common libgvfscommon0 libk5crypto3 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libkrb5-3 libkrb5-dev libkrb5support0 libldap-2.4-2 libldap2-dev
  libnotify1 libopenal1 libpam-runtime libpam0g libparted0debian1 libpcsclite1 libpng12-0 libpng12-dev libpoppler5 libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa
  libsnmp-base libsnmp15 libsoup-gnome2.4-1 libsoup2.4-1 libtiff4 libusb-0.1-4 linux-firmware linux-generic linux-generic-pae linux-image-generic linux-image-generic-pae
  linux-image-server linux-server mysql-server-5.1 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssh-client openssh-server parted poppler-utils python-apt
  ssh sudo udisks update-manager-core ureadahead w3m
91 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7,435kB/89.1MB of archives.
After this operation, 7,750kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libldap2-dev 2.4.21-0ubuntu5.2 [902kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libldap-2.4-2 2.4.21-0ubuntu5.2 [202kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-core 1:0.134.10 [199kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main w3m 0.5.2-2.1ubuntu1.1 [1,103kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main libclamav6 0.96.1+dfsg-3ubuntu5~lucid1 [3,705kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav-daemon 0.96.1+dfsg-3ubuntu5~lucid1 [404kB]                                                          
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav-base 0.96.1+dfsg-3ubuntu5~lucid1 [294kB]                                                            
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav-freshclam 0.96.1+dfsg-3ubuntu5~lucid1 [304kB]                                                       
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main clamav 0.96.1+dfsg-3ubuntu5~lucid1 [322kB]                                                                 
Fetched 7,435kB in 10s (714kB/s)                                                                                                                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up apt (0.7.25.3ubuntu9.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 87542 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12 (using .../mysql-server-5.1_5.1.41-3ubuntu12.6_i386.deb) ...

```


I just stops there ?  

Try stopping MySQL and then doing the upgrade ...

> sudo service mysql stop

Check to make sure that there are no instances of MySQL running
> ps aux | grep -i mysql

Then do the upgrade ... and restart MySQL if it completes.

---

### Post by FuturePilot on 2010-08-11
Ran into this myself a while ago. See this comment [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/574557/comments/6]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/574557/comments/6")

---

### Post by MrWES on 2010-08-11
Yah, I came across that bug after I posted. I fired up another terminal login and started mysql and then the upgrade resumed.

Thanks,
Bill

---

