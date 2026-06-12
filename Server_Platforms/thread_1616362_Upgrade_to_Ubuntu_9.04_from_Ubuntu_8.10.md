---
title: "Upgrade to Ubuntu 9.04 from Ubuntu 8.10"
date: 2010-11-08
forum: Server Platforms
---

### Post by laurie112 on 2010-11-08
Hi

I'm attempting to upgrade to Ubuntu 9.04 from Ubuntu 8.10. I have been using the following guide: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

All attempts have failed as the following sources do not include all of the require packages to simply bring 8.10 completely up to date.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse

The missing packages are mainly in the security/main area for i386.

I only have command line access and seems I cannot even upgrade 8.10 to a point that it is ready to run: do-release-upgrade

If I was to download: [http://releases.ubuntu.com/jaunty/ubuntu-9.04-server-i386.iso](http://releases.ubuntu.com/jaunty/ubuntu-9.04-server-i386.iso) mount this image could I use this as source for the upgrade?

I want to upgrade rather than clean install in order to maintain the network configuration etc as I only have command line access.

The issue as I see it is Ubuntu 8.10 is not completely up to date and whilst aptitude update can see updates on attempting to install the required packages these cannot be found!

Would upgrading onto my current system from a iso source solve this issue?

Also one thing I am a little unclear about is, have I comprimised my system in attempting an upgrade and the upgrade failing? Does a horrible suprise await me if I reboot the server?

Many thanks in advance...

---

### Post by laurie112 on 2010-11-08
Sadly my prior comment - below, proved not to be the case... Please see next post help still required!!!

In the age old tradition of maybe finding the answer after you ask for help... I have found this: [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/264181](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/264181) which may well be causing my issue...

Sadly I did not keep a record of the output of the failures so I will need to test to confirm. I will do this as soon as I can...

Any feedback in general or specifically is still greatly accepted

---

### Post by laurie112 on 2010-11-08
Okay I have just tried to bring Ubuntu 8.10 up to date so I may upgrade to 9.04...

I ran "apt-get update" using the source.list of original and this returns a great deal of Not Found Errors...

I then changed the source.list to use the old-release sources as provided in the EOLupgrades guide...

apt-get update returns perfectly... But running apt-get upgrade shows the following failures - see below...

The issue is that I need to upgrade to 9.04 and but I am stuck if I am unable to upgrade 8.10 to the most recent versions...

Can I upgrade to 9.04 without having 8.10 completely up to date?

Could I use "Alternate install CD" to upgrade without having 8.10 completely up to date, would this solve the issue?

Can someone provide a solution to my problem?

Do I need to compile all of the missing from source!!!!!

I rent this dedicated server and the installation of Ubuntu has clearly fallen far to out of date... To make matters worse even if I use the ISP's system to wipe the server it will be returned to an out of date version of Ubuntu 8.10, assumably more out of date than the current version given that key sources no longer hold the required packages...

Output from apt-get update & apt-get upgrade using old-release sources...

root@server:/etc/apt# apt-get update
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/main Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/restricted Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/universe Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/multiverse Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/main Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/universe Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security Release.gpg
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports Release.gpg
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/main Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/restricted Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/universe Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/multiverse Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/main Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/restricted Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/universe Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/multiverse Translation-en_GB
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-proposed/multiverse Packages
Reading package lists... Done

All seems fine...

root@server:/etc/apt# apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9 bind9-host bind9utils dnsutils libbind9-40 libdns43 libisc44 libisccc40 libisccfg40 liblwres40
  linux-restricted-modules-generic
The following packages will be upgraded:
  dpkg fuse-utils gzip libapache2-mod-php5 libexpat1 libfuse2 libgd2-xpm libhtml-parser-perl libkrb53
  libmysqlclient15off libpng12-0 libpq5 libssl0.9.8 mysql-client-5.0 mysql-server-5.0 ntp ntpdate openssl php5
  php5-cgi php5-common php5-curl php5-gd php5-mysql python2.5 python2.5-minimal sudo
27 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 56.3MB/56.3MB of archives.
After this operation, 344kB disk space will be freed.
Do you want to continue [Y/n]? Y
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-backports/main libpq5 8.4.2-1~intrepid1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main dpkg 1.14.20ubuntu6.3
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main gzip 1.3.12-6ubuntu2.8.10.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libmysqlclient15off 5.0.67-0ubuntu6.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main mysql-client-5.0 5.0.67-0ubuntu6.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main mysql-server-5.0 5.0.67-0ubuntu6.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libssl0.9.8 0.9.8g-10.1ubuntu2.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main python2.5 2.5.2-11.1ubuntu1.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main python2.5-minimal 2.5.2-11.1ubuntu1.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libkrb53 1.6.dfsg.4~beta1-3ubuntu0.4
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main fuse-utils 2.7.3-4ubuntu2.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libfuse2 2.7.3-4ubuntu2.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main php5-cgi 5.2.6-2ubuntu4.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main php5-mysql 5.2.6-2ubuntu4.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main php5-curl 5.2.6-2ubuntu4.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libpng12-0 1.2.27-1ubuntu0.2
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1.8.10.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main php5-gd 5.2.6-2ubuntu4.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libapache2-mod-php5 5.2.6-2ubuntu4.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main php5-common 5.2.6-2ubuntu4.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libexpat1 2.0.1-4ubuntu0.8.10.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main libhtml-parser-perl 3.56-1ubuntu2.1
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main ntp 1:4.2.4p4+dfsg-6ubuntu2.4
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main ntpdate 1:4.2.4p4+dfsg-6ubuntu2.4
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main openssl 0.9.8g-10.1ubuntu2.6
  404 Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main sudo 1.6.9p17-1ubuntu2.3
  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6.3_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6.3_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.12-6ubuntu2.8.10.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.12-6ubuntu2.8.10.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.67-0ubuntu6.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.67-0ubuntu6.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client-5.0_5.0.67-0ubuntu6.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client-5.0_5.0.67-0ubuntu6.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.67-0ubuntu6.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.67-0ubuntu6.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-10.1ubuntu2.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-10.1ubuntu2.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.2-11.1ubuntu1.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.2-11.1ubuntu1.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-11.1ubuntu1.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-11.1ubuntu1.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.4~beta1-3ubuntu0.4_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.4~beta1-3ubuntu0.4_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.7.3-4ubuntu2.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.7.3-4ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.7.3-4ubuntu2.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.7.3-4ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-cgi_5.2.6-2ubuntu4.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-cgi_5.2.6-2ubuntu4.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.2.6-2ubuntu4.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.2.6-2ubuntu4.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6-2ubuntu4.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6-2ubuntu4.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.27-1ubuntu0.2_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.27-1ubuntu0.2_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3ubuntu1.8.10.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3ubuntu1.8.10.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.6-2ubuntu4.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.6-2ubuntu4.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.6-2ubuntu4.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.6-2ubuntu4.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.6-2ubuntu4.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.6-2ubuntu4.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_2.0.1-4ubuntu0.8.10.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_2.0.1-4ubuntu0.8.10.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.56-1ubuntu2.1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.56-1ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/p/postgresql-8.4/libpq5_8.4.2-1~intrepid1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/p/postgresql-8.4/libpq5_8.4.2-1~intrepid1_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p4+dfsg-6ubuntu2.4_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p4+dfsg-6ubuntu2.4_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p4+dfsg-6ubuntu2.4_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p4+dfsg-6ubuntu2.4_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-10.1ubuntu2.6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-10.1ubuntu2.6_i386.deb)  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p17-1ubuntu2.3_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p17-1ubuntu2.3_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I also ran with --fix-missing... no joy

---

### Post by arrrghhh on 2010-11-09
Well that's a lot of 404's... Can you hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) from the machine?  Just try to ping it.

Also might be helpful, first use [ code ] braces around code-stuff ;)

Please put your sources.list in code braces... Perhaps something is wrong in there (assuming you can hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)...)

Also, did you follow [this](https://help.ubuntu.com/community/EOLUpgrades/Intrepid) guide?

---

### Post by wilee-nilee on 2010-11-09
Intrepid has EOL end of Life.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You would be better served by backing up what you have and finding a OS that is still in release that works and you can upgrade from in the future. Fresh install are the key words here.

---

