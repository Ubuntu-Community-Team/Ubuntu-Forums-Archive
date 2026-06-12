---
title: "Mirror ar.archive.ubuntu.com"
date: 2024-08-15
forum: Security
---

### Post by juan-sanchezo on 2024-08-15
Hi,
 This is normal? I try to update my system.

# apt-get update && apt-get dist-upgrade
Hit:1 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:3 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Hit:4 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) jammy-security InRelease
Hit:5 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) jammy-pgdg InRelease
Hit:6 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy InRelease
Hit:7 [https://deb.goaccess.io](https://deb.goaccess.io) jammy InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  python3-update-manager update-manager-core
The following packages will be upgraded:
  postgresql-client-common postgresql-common
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 335 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.


If I use JP or BR mirror:
=================
# apt-get update && apt-get dist-upgrade
Hit:1 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) jammy-pgdg InRelease
Hit:2 [https://deb.goaccess.io](https://deb.goaccess.io) jammy InRelease
Get:3 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy InRelease [270 kB]
Get:4 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates InRelease [128 kB]
Get:5 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports InRelease [127 kB]
Get:6 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security InRelease [129 kB]
Get:7 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages [1,395 kB]
Get:8 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/main Translation-en [510 kB]
Get:9 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/main amd64 c-n-f Metadata [30.3 kB]
Get:10 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/restricted amd64 Packages [129 kB]
Get:11 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/restricted Translation-en [18.6 kB]
Get:12 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/restricted amd64 c-n-f Metadata [488 B]
Get:13 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages [14.1 MB]
Hit:14 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy InRelease
Get:15 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/universe Translation-en [5,652 kB]
Get:16 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/universe amd64 c-n-f Metadata [286 kB]
Get:17 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/multiverse amd64 Packages [217 kB]
Get:18 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/multiverse Translation-en [112 kB]
Get:19 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy/multiverse amd64 c-n-f Metadata [8,372 B]
Get:20 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [1,946 kB]
Get:21 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/main Translation-en [344 kB]
Get:22 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 c-n-f Metadata [17.8 kB]
Get:23 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 Packages [2,322 kB]
Get:24 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/restricted Translation-en [400 kB]
Get:25 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 c-n-f Metadata [604 B]
Get:26 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages [1,111 kB]
Get:27 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/universe Translation-en [259 kB]
Get:28 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 c-n-f Metadata [25.9 kB]
Get:29 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/multiverse amd64 Packages [43.3 kB]
Get:30 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/multiverse Translation-en [10.8 kB]
Get:31 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-updates/multiverse amd64 c-n-f Metadata [444 B]
Get:32 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/main amd64 Packages [67.1 kB]
Get:33 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/main Translation-en [11.0 kB]
Get:34 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/main amd64 c-n-f Metadata [388 B]
Get:35 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/restricted amd64 c-n-f Metadata [116 B]
Get:36 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/universe amd64 Packages [28.8 kB]
Get:37 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/universe Translation-en [16.5 kB]
Get:38 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/universe amd64 c-n-f Metadata [672 B]
Get:39 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-backports/multiverse amd64 c-n-f Metadata [116 B]
Get:40 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/main amd64 Packages [1,727 kB]
Get:41 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/main Translation-en [286 kB]
Get:42 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/main amd64 c-n-f Metadata [13.1 kB]
Get:43 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/restricted amd64 Packages [2,247 kB]
Get:44 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/restricted Translation-en [387 kB]
Get:45 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/restricted amd64 c-n-f Metadata [572 B]
Get:46 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/universe amd64 Packages [890 kB]
Get:47 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/universe Translation-en [175 kB]
Get:48 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/universe amd64 c-n-f Metadata [19.0 kB]
Get:49 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/multiverse amd64 Packages [37.2 kB]
Get:50 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/multiverse Translation-en [7,588 B]
Get:51 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) jammy-security/multiverse amd64 c-n-f Metadata [228 B]
Fetched 35.5 MB in 9s (4,089 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-5.15.0-118 linux-headers-5.15.0-118-generic linux-image-5.15.0-118-generic linux-modules-5.15.0-118-generic linux-modules-extra-5.15.0-118-generic
The following packages have been kept back:
  python3-update-manager update-manager-core
The following packages will be upgraded:
  apache2 apache2-bin apache2-data apache2-utils apport bind9-dnsutils bind9-host bind9-libs busybox-initramfs busybox-static cloud-init curl graphviz gtk-update-icon-cache landscape-common libcdt5 libcgraph6 libcups2 libcurl3-gnutls
  libcurl4 libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin libgtk-3-common libgvc6 libgvpr2 libk5crypto3 libkrb5-3 libkrb5support0 liblab-gamut1 libldap-2.5-0 libldap-common libnetplan0 libnode-dev libnode72 libpathplan4 libpython3.10
  libpython3.10-minimal libpython3.10-stdlib libssl-dev libssl3 libtiff5 libvte-2.91-0 libvte-2.91-common linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev netplan.io nodejs nodejs-doc openjdk-11-jdk
  openjdk-11-jdk-headless openjdk-11-jre openjdk-11-jre-headless openssh-client openssh-server openssh-sftp-server openssl postgresql-client-common postgresql-common python3-apport python3-problem-report python3-zipp python3.10
  python3.10-minimal snapd tzdata ubuntu-advantage-tools ubuntu-minimal ubuntu-pro-client ubuntu-pro-client-l10n ubuntu-server ubuntu-server-minimal ubuntu-standard wget
77 upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 569 MB of archives.
After this operation, 587 MB of additional disk space will be used.
Do you want to continue? [Y/n]

AR mirror are worinking?

Thanks in advance?
Juan

---

