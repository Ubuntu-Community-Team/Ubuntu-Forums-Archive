---
title: "Alternate 14.4+ GUI"
date: 2014-06-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Toptyg on 2014-06-21
Hello all,

I have downloaded alternate Version of Ubuntu 14.04 (I use PXE for installation on PC).

How can I add the GUI for automatic installation (wonna Ubuntu-desktop package )

seed file
====
d-i netcfg/get_hostname seen false
d-i mirror/country string manual
d-i mirror/protocol select ftp
d-i mirror/ftp/hostname string [ftp.serv.com]("ftp://ftp.serv.com")
d-i mirror/ftp/directory string /pub/Linux/STP/14.04/x86
d-i debian-installer/language string ru
d-i debian-installer/country string RU
d-i debian-installer/locale string ru_RU.UTF-8
d-i localechooser/supported-locales multiselect ru_RU.UTF-8, en_US.UTF-8, be_BY.UTF-8 
d-i passwd/make-user boolean true
d-i passwd/user-fullname string Student User
d-i passwd/username string student
d-i passwd/user-password password password
d-i passwd/user-password-again password password
d-i user-setup/allow-password-weak boolean true
d-i console-setup/layoutcode string ru
tasksel tasksel/first multiselect standard, ubuntu-desktop
d-i pkgsel/language-packs multiselect en, ru
d-i apt-setup/restricted boolean false
d-i time/zone select Europe/Moscow
clock-setup clock-setup/ntp boolean true
clock-setup clock-setup/ntp-server string ntp.serv.com
apt-mirror-setup apt-setup/universe boolean false
apt-mirror-setup apt-setup/multiverse boolean false
apt-mirror-setup apt-setup/contrib boolean false
apt-mirror-setup apt-setup/restricted boolean false
apt-mirror-setup apt-setup/backports boolean false
apt-mirror-setup apt-setup/proposed boolean false
apt-mirror-setup apt-setup/partner boolean false
apt-mirror-setup apt-setup/non-free boolean false
apt-mirror-setup apt-setup/extras boolean false
====


Thanks.

---

### Post by ajgreeny on 2014-06-21
I don't think the Alternate Install CD version is available any more, except for Lubuntu, so I presume you mean that you have the Minimal install CD from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

That should allow you to install to a command line and then, with a cable network connection for ease and speed, simply use command ```
sudo apt-get install ubuntu-desktop
```You should then end up with a fully working and completely normal and updated version of Ubuntu trusty.

Are you having problems at the moment or simply asking for info before you start?

---

