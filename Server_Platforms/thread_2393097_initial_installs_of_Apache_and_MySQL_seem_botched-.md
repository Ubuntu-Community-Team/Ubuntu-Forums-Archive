---
title: "initial installs of Apache and MySQL seem botched--next steps?"
date: 2018-05-29
forum: Server Platforms
---

### Post by megunticook on 2018-05-29
Working knowledge of Amazon Linux, new to Ubuntu. Setting up a local development server on my Windows 10 machine. Installed Ubuntu successfully. Then mistakenly installed MySQL first, seemed to go OK at first but then wouldn't start. Installed Apache and couldn't get that to start either. Need to remove both of them completely, then reinstall in correct order?

What's the proper way to do this in Ubuntu? 

Thanks! Looking forward to getting this dev environment up and running.

---

### Post by wildmanne39 on 2018-05-29
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by LHammonds on 2018-05-29
I assume you are running VirtualBox and installing Ubuntu inside that?

I have step-by-step instructions on how to setup production-quality, dedicated servers but you could glance over the partition and scripting sections straight to the steps for installing MariaDB.  I have various web applications I have documented that include Apache but none that are apache by itself.

I'll point you to my Ubuntu 16.04 instructions since I'm still creating the 18.04 variations.

[Ubuntu Server 16.04 LTS](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220)
[MariaDB on Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=225)
[MediaWiki on Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=241)
[NextCloud on Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=239)

LHammonds

---

### Post by megunticook on 2018-05-29
No VirtualBox, this is the Windows 10 Linux Subsystem with an Ubuntu distribution available through the Microsoft store ([https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)). It seemed to install flawlessly.

I followed the instructions in the Ubuntu documentation for installing MySQL ([https://help.ubuntu.com/lts/serverguide/mysql.html.en](https://help.ubuntu.com/lts/serverguide/mysql.html.en)) and Apache ([https://tutorials.ubuntu.com/tutorial/install-and-configure-apache#0](https://tutorials.ubuntu.com/tutorial/install-and-configure-apache#0)). 

I just tried starting Apache and was able to browse to the default Apache page, so that part seems resolved.

But when I try to start MySQL using:
```
sudo systemctl restart mysql.service
```

I get this:
```
Failed to connect to bus: no such file or directory.
```

Should I uninstall MySQL and reinstall? What is Ubuntu trying to tell me here exactly?

ps. tried:
```
mysql -u root -p
```

and got the MySQL command line. Phew! Onward and upward. 

Thanks for your help. I'm sure I'll have more questions as I learn Ubuntu.

---

### Post by megunticook on 2018-05-29
Just tried installing PHP and it seems like there are some components it wants to download from security.ubuntu.com but is getting 404 errors. Am I doing something wrong here or is there a temporary unavailability situation?

```
doctor@ED-Workstation:~$ sudo apt install php libapache2-mod-php
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libfreetype6
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libapache2-mod-php7.0 php-common php7.0 php7.0-cli php7.0-common php7.0-json php7.0-opcache php7.0-readline
Suggested packages:
  php-pear
The following NEW packages will be installed:
  libapache2-mod-php libapache2-mod-php7.0 php php-common php7.0 php7.0-cli php7.0-common php7.0-json php7.0-opcache
  php7.0-readline
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,472 kB of archives.
After this operation, 13.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 php-common all 1:35ubuntu6.1 [10.8 kB]
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-common amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Ign:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-json amd64 7.0.28-0ubuntu0.16.04.1
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-common amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Ign:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-opcache amd64 7.0.28-0ubuntu0.16.04.1
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-json amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-readline amd64 7.0.28-0ubuntu0.16.04.1
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-opcache amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-readline amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-cli amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-cli amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 libapache2-mod-php7.0 amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 libapache2-mod-php7.0 amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libapache2-mod-php all 1:7.0+35ubuntu6.1 [2,990 B]
Err:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0 all 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0 all 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 php all 1:7.0+35ubuntu6.1 [2,862 B]
Fetched 16.7 kB in 1s (10.6 kB/s)
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-common_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-common_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-json_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-json_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-opcache_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-opcache_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-readline_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-readline_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-cli_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-cli_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/libapache2-mod-php7.0_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/libapache2-mod-php7.0_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0_7.0.28-0ubuntu0.16.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0_7.0.28-0ubuntu0.16.04.1_all.deb)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
doctor@ED-Workstation:~$ sudo apt install php libapache2-mod-php --fix-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libfreetype6
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libapache2-mod-php7.0 php-common php7.0 php7.0-cli php7.0-common php7.0-json php7.0-opcache php7.0-readline
Suggested packages:
  php-pear
The following NEW packages will be installed:
  libapache2-mod-php libapache2-mod-php7.0 php php-common php7.0 php7.0-cli php7.0-common php7.0-json php7.0-opcache
  php7.0-readline
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,455 kB/3,472 kB of archives.
After this operation, 13.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-common amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-json amd64 7.0.28-0ubuntu0.16.04.1
Ign:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-opcache amd64 7.0.28-0ubuntu0.16.04.1
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-common amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Ign:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-readline amd64 7.0.28-0ubuntu0.16.04.1
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-json amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-cli amd64 7.0.28-0ubuntu0.16.04.1
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-opcache amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Ign:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 libapache2-mod-php7.0 amd64 7.0.28-0ubuntu0.16.04.1
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-readline amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0 all 7.0.28-0ubuntu0.16.04.1
Err:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0-cli amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 libapache2-mod-php7.0 amd64 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Err:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 php7.0 all 7.0.28-0ubuntu0.16.04.1
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Unable to correct missing packages.
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-common_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-common_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1360:8001::17 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-json_7.0.28-0ubuntu0.16.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-json_7.0.28-0ubuntu0.16.04.1_amd64.deb)  404  Not Found [IP: 2001:67c:1360:8001::17 80]
```


Never mind, I tried running
```
sudo apt-get update
``` 
And then ran the php install with --fix-missing and it looks like it worked.

---

### Post by SeijiSensei on 2018-05-30
By far, the simplest method for installing Apache, MySQL, and PHP is to use

```
sudo apt install lamp-server^
```

Note the circumflex ("^") at the end; it's required.

That will install the main applications and the various other needed pieces like the libapache2-mod-php module.

Since this is a virtual machine, and you just got started, I'd create a new clean VM from scratch, then install lamp-server.

More details: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by LHammonds on 2018-05-30
> **megunticook said:**
> No VirtualBox, this is the Windows 10 Linux Subsystem with an Ubuntu distribution available through the Microsoft store ([https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)). It seemed to install flawlessly.Oh, I'm not familiar with the Windows subsystem for Linux and the peculiarities that would come with it.

With VirtualBox, if I wanted to migrate a VM from VirtualBox (personal testing on my PC) to my Vmware environment (production on actual servers), it would be a simple matter to transfer.

LHammonds

---

### Post by megunticook on 2018-05-30
Appreciate the advice. Right now I can view the Apache test page and my phpinfo page. I installed MySQL already, and was able to log in as root earlier, but I hadn't yet run:
```
sudo mysql_secure_installation
```
When I tried, I was prompted for my password, which I entered, then got this:
```
doctor@ED-Workstation:~$ sudo mysql_secure_installation
[sudo] password for doctor:

Securing the MySQL server deployment.

Enter password for user root:
Error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

What am I doing wrong here?

Tried a few more things to troubleshoot and still not sure exactly what's going on:

```
doctor@ED-Workstation:~$ mysql -u root -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
doctor@ED-Workstation:~$ mysqld -u root -p status
mysqld: Can't change dir to '/var/lib/mysql/' (Errcode: 13 - Permission denied)
2018-05-31T02:55:21.646890Z 0 [Warning] Ignoring user change to 'root' because the user was set to 'mysql' earlier on the command line

2018-05-31T02:55:21.647762Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2018-05-31T02:55:21.648884Z 0 [Warning] Can't create test file /var/lib/mysql/ED-Workstation.lower-test
2018-05-31T02:55:21.649714Z 0 [Note] mysqld (mysqld 5.7.22-0ubuntu0.16.04.1) starting as process 84 ...
2018-05-31T02:55:21.665608Z 0 [Warning] Can't create test file /var/lib/mysql/ED-Workstation.lower-test
2018-05-31T02:55:21.665643Z 0 [Warning] Can't create test file /var/lib/mysql/ED-Workstation.lower-test
2018-05-31T02:55:21.667810Z 0 [Warning] One can only use the --user switch if running as root

2018-05-31T02:55:21.668158Z 0 [ERROR] failed to set datadir to /var/lib/mysql/
2018-05-31T02:55:21.671461Z 0 [ERROR] Aborting

2018-05-31T02:55:21.672417Z 0 [Note] Binlog end
2018-05-31T02:55:21.675834Z 0 [Note] mysqld: Shutdown complete
```

I checked the log located at \var\log\mysql:

```
2018-05-31T03:23:57.710225Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2018-05-31T03:23:57.725110Z 0 [ERROR] InnoDB: Linux Native AIO interface is not supported on this platform. Please check your OS documentation and install appropriate binary of InnoDB.
2018-05-31T03:23:57.725181Z 0 [Warning] InnoDB: Linux Native AIO disabled.
2018-05-31T03:23:58.388678Z 0 [Warning] InnoDB: New log files created, LSN=45790
2018-05-31T03:23:58.483293Z 0 [Warning] InnoDB: Creating foreign key constraint system tables.
2018-05-31T03:23:58.501041Z 0 [Warning] No existing UUID has been found, so we assume that this is the first time that this server has been started. Generating a new UUID: 0e67ce92-6482-11e8-92a2-4cedfb3ea3ba.
2018-05-31T03:23:58.506848Z 0 [Warning] Gtid table is not ready to be used. Table 'mysql.gtid_executed' cannot be opened.
2018-05-31T03:23:58.507505Z 1 [Warning] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
```

---

### Post by megunticook on 2018-05-31
This morning I gave it another go, this time making sure to launch Ubuntu using administrator privileges, and managed to run mysql_secure_installation successfully. I was also able to create a database and user in preparation for setting up WordPress.

I followed the Ubuntu 16.04 guidelines for setting up WordPress ([https://help.ubuntu.com/16.04/serverguide/wordpress.html](https://help.ubuntu.com/16.04/serverguide/wordpress.html)), and ran ```

sudo apt install wordpress
``` successfully. (results pasted in below).

However, the Ubuntu instructions say the next step is to open /etc/apache2/sites-available/wordpress.conf for editing but there is no such file. Any ideas here?

Thanks.

results of WordPress install:
```
doctor@ED-Workstation:~$ sudo apt install wordpress
[sudo] password for doctor:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  fontconfig-config fonts-dejavu-core javascript-common libao-common libao4 libflac8 libfontconfig1 libgd3 libjbig0
  libjpeg-turbo8 libjpeg8 libjs-cropper libjs-jquery libjs-mediaelement libjs-prototype libjs-scriptaculous libogg0
  libphp-phpmailer libspeex1 libtiff5 libvorbis0a libvorbisenc2 libvorbisfile3 libvpx3 libxpm4 php-gd php-getid3
  php-mysql php7.0-gd php7.0-mysql vorbis-tools wordpress-l10n wordpress-theme-twentysixteen
Suggested packages:
  libasound2 libaudio2 libesd0 | libesd-alsa0 libpulse0 libgd-tools mail-transport-agent php-league-oauth2-client
  php-league-oauth2-google speex php-ssh2
The following NEW packages will be installed:
  fontconfig-config fonts-dejavu-core javascript-common libao-common libao4 libflac8 libfontconfig1 libgd3 libjbig0
  libjpeg-turbo8 libjpeg8 libjs-cropper libjs-jquery libjs-mediaelement libjs-prototype libjs-scriptaculous libogg0
  libphp-phpmailer libspeex1 libtiff5 libvorbis0a libvorbisenc2 libvorbisfile3 libvpx3 libxpm4 php-gd php-getid3
  php-mysql php7.0-gd php7.0-mysql vorbis-tools wordpress wordpress-l10n wordpress-theme-twentysixteen
0 upgraded, 34 newly installed, 0 to remove and 15 not upgraded.
Need to get 12.6 MB of archives.
After this operation, 65.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 libao-common all 1.1.0-3ubuntu1 [6,392 B]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libao4 amd64 1.1.0-3ubuntu1 [32.2 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 libjpeg-turbo8 amd64 1.4.2-0ubuntu3 [111 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial/main amd64 libogg0 amd64 1.3.2-1 [17.2 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 libjbig0 amd64 2.1-3.1 [26.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 fonts-dejavu-core all 2.35-1 [1,039 kB]
Setting up wordpress (4.4.2+dfsg-1ubuntu1) ...
Added to /var/lib/wordpress/wp-content/plugins: akismet index.php
Added to /var/lib/wordpress/wp-content/languages: admin-ar.mo admin-bs_BA.mo admin-ca.mo admin-cy.mo admin-da_DK.mo admi
n-de_DE.mo admin-el.mo admin-es_ES.mo admin-es_PE.mo admin-et.mo admin-eu.mo admin-fa_IR.mo admin-fi.mo admin-fr_FR.mo a
dmin-gl_ES.mo admin-he_IL.mo admin-hr.mo admin-it_IT.mo admin-ja.mo admin-ko_KR.mo admin-my_MM.mo admin-network-ar.mo ad
min-network-bs_BA.mo admin-network-ca.mo admin-network-cy.mo admin-network-da_DK.mo admin-network-de_DE.mo admin-network
-el.mo admin-network-es_ES.mo admin-network-es_PE.mo admin-network-et.mo admin-network-fa_IR.mo admin-network-fi.mo admi
n-network-fr_FR.mo admin-network-gl_ES.mo admin-network-he_IL.mo admin-network-hr.mo admin-network-it_IT.mo admin-networ
k-ja.mo admin-network-ko_KR.mo admin-network-my_MM.mo admin-network-ru_RU.mo admin-network-sk_SK.mo admin-network-sl_SI.
mo admin-network-sq.mo admin-network-sr_RS.mo admin-network-sv_SE.mo admin-network-ug_CN.mo admin-network-zh_CN.mo admin
-network-zh_TW.mo admin-ru_RU.mo admin-sk_SK.mo admin-sl_SI.mo admin-sq.mo admin-sr_RS.mo admin-sv_SE.mo admin-ug_CN.mo
admin-zh_CN.mo admin-zh_TW.mo ar.mo bg_BG.mo bn_BD.mo bs_BA.mo ca.mo ckb.mo continents-cities-bg_BG.mo continents-cities
-bs_BA.mo continents-cities-cs_CZ.mo continents-cities-cy.mo continents-cities-da_DK.mo continents-cities-de_DE.mo conti
nents-cities-el.mo continents-cities-en_CA.mo continents-cities-es_PE.mo continents-cities-et.mo continents-cities-eu.mo
 continents-cities-fa_IR.mo continents-cities-fi.mo continents-cities-fr_FR.mo continents-cities-gd.mo continents-cities
-he_IL.mo continents-cities-hr.mo continents-cities-hu_HU.mo continents-cities-it_IT.mo continents-cities-ja.mo continen
ts-cities-ka_GE.mo continents-cities-ko_KR.mo continents-cities-lv.mo continents-cities-mk_MK.mo continents-cities-my_MM
.mo continents-cities-nb_NO.mo continents-cities-nn_NO.mo continents-cities-pl_PL.mo continents-cities-pt_BR.mo continen
ts-cities-pt_PT.mo continents-cities-ro_RO.mo continents-cities-ru_RU.mo continents-cities-sk_SK.mo continents-cities-sl
_SI.mo continents-cities-sq.mo continents-cities-sr_RS.mo continents-cities-su_ID.mo continents-cities-sv_SE.mo continen
ts-cities-ta_LK.mo continents-cities-tr_TR.mo continents-cities-ug_CN.mo continents-cities-vi.mo continents-cities-zh_CN
.mo continents-cities-zh_TW.mo cs_CZ.mo cy.mo da_DK.mo de_DE.mo el.mo en_CA.mo eo.mo es_CL.mo es_ES.mo es_PE.mo et.mo eu
.mo fa_IR.mo fi.mo fr_FR.mo gd.mo gl_ES.mo he_IL.mo hr.mo hu_HU.mo id_ID.mo it_IT.mo ja.mo jv_ID.mo ka_GE.mo ko_KR.mo lv
.mo mk_MK.mo ms_MY.mo my_MM.mo nb_NO.mo nl.mo nl_NL.mo pl_PL.mo pt_BR.mo pt_PT.mo ro_RO.mo ru_RU.mo ru_UA.mo si_LK.mo sk
_SK.mo sl_SI.mo sq.mo sr_RS.mo su_ID.mo sv_SE.mo sw.mo ta_LK.mo th.mo tr_TR.mo ug_CN.mo uk.mo ur.mo vi.mo zh_CN.mo zh_HK
.mo zh_TW.mo
Setting up wordpress-l10n (4.4.2+dfsg-1ubuntu1) ...
Setting up wordpress-theme-twentysixteen (4.4.2+dfsg-1ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for libapache2-mod-php7.0 (7.0.30-0ubuntu0.16.04.1) ...
```

---

### Post by SeijiSensei on 2018-05-31
I always install WordPress from the most recent ZIP file at wordpress.org.

Here's a good walk-through for creating a WordPress instance on Ubuntu using this method:  [https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04)

wordpress.conf would be a file dropped into your Apache instance that creates a virtual host or directory structure to support WordPress.  I looked at the [Ubuntu release of wordpress]("https://launchpad.net/ubuntu/+source/wordpress") and don't see that file.  It's not part of the default Apache installation either, of course.

I suggest you download [https://wordpress.org/latest.tar.gz](https://wordpress.org/latest.tar.gz) and follow the instructions in the guide above.

---

### Post by megunticook on 2018-05-31
I was able to get a WordPress site up and running on localhost. Thanks for all your help everyone, I'll go ahead and close this thread but I'm sure I'll have more questions as I play around with Ubuntu more. Thanks again for checking in with me.

---

