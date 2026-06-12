---
title: "Owncloud X files deleted after &quot;apt autoremove&quot;"
date: 2017-12-18
forum: Server Platforms
---

### Post by aquilescrespo on 2017-12-18
Hello there,

I ran into a little problem.... After the updating the Ubuntu server 16.04 i ran "apt autoremove", after this process removed all the Owncloud file at /var/www/owncloud

Is there any explanation to this behavior, and/or a way to reverse this situation?

thanks in advance 
Aquiles dos Santos Crespo

---

### Post by LHammonds on 2017-12-18
I don't think it was "apt autoremove" that trashed your owncloud folder.  That simply isn't what autoremove does.

LHammonds

---

### Post by aquilescrespo on 2017-12-19
I was the hole time thinking in that, but in the end after doing the autoremove the files have vanished, only the owncloud-files, the Data from users was not touched.
That i did after the upgrade, actually 3 days after the upgrade (a small system update)and one of the updates were this owncloud-files (the upgrade from 9 to 10) package. 
I am a little bit confused with this because is the first time that something like this happen to me with the autoremove. I can only think that in the update the added the owncloud-files package to the removal....
is that possibel?

---

### Post by LHammonds on 2017-12-19
Well, lets step back and look at how you installed owncloud in the 1st place.

Did you install version 9 via repository and later install version 10 manually?

I could see a scenario like the above where v9 files were originally placed there via apt...then later you manually lay v10 down and somewhere along the line apt is told owncloud v9 is no longer installed and thus auto-remove takes out the v9 files..which v10 shares the same filenames if overlayed in the same location.

[My installation method]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=234") is about doing it manually in order to have the most-current version available.  However, I plan on switching to NextCloud as soon as they support moving from my upgraded v10.0.3 install (I have 2 servers at v10.0.3)

APT has nevered touch my owncloud files because they know nothing about any files under /var/www.

LHammonds

---

### Post by aquilescrespo on 2017-12-21
hello [COLOR=#000000]LHammonds,[/COLOR]

First of all thanks for your reply's....

the installation and update from Owncloud like every other service on this server was made by the repositories. There is only one thing that i added to the Owncloud was a Theme and also replaced images after the installation.

```



Start-Date: 2017-12-06  00:31:00
Commandline: /usr/bin/unattended-upgrade
Upgrade: libxml2:amd64 (2.9.3+dfsg1-1ubuntu0.3, 2.9.3+dfsg1-1ubuntu0.4), linux-firmware:amd64 (1.157.13, 1.157.14)
End-Date: 2017-12-06  00:46:45


Start-Date: 2017-12-08  04:28:43
Commandline: /usr/bin/unattended-upgrade
Install: linux-headers-4.4.0-103:amd64 (4.4.0-103.126, automatic), linux-image-4.4.0-103-generic:amd64 (4.4.0-103.126, automatic), linux-signed-image-4.4.0-103-generic:amd64 (4.4.0-103.126, automatic), linux-image-extra-4.4.0-103-generic:amd64 (4.4.0-103.126, automatic), linux-headers-4.4.0-103-generic:amd64 (4.4.0-103.126, automatic)
Upgrade: linux-headers-generic:amd64 (4.4.0.101.106, 4.4.0.103.108), linux-signed-image-generic:amd64 (4.4.0.101.106, 4.4.0.103.108), linux-signed-generic:amd64 (4.4.0.101.106, 4.4.0.103.108), rsync:amd64 (3.1.1-3ubuntu1, 3.1.1-3ubuntu1.1)
End-Date: 2017-12-08  04:34:13


Start-Date: 2017-12-12  00:49:33
Commandline: /usr/bin/unattended-upgrade
Upgrade: openssl:amd64 (1.0.2g-1ubuntu4.9, 1.0.2g-1ubuntu4.10), libssl1.0.0:amd64 (1.0.2g-1ubuntu4.9, 1.0.2g-1ubuntu4.10)
End-Date: 2017-12-12  00:49:53


Start-Date: 2017-12-14  07:48:29
Commandline: apt-get dist-upgrade
Requested-By: whmcloud (1000)
Upgrade: cryptsetup-bin:amd64 (2:1.6.6-5ubuntu2, 2:1.6.6-5ubuntu2.1), lxc-common:amd64 (2.0.7-0ubuntu1~16.04.2, 2.0.8-0ubuntu1~16.04.2), libdns-export162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), libisccfg140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), update-manager-core:amd64 (1:16.04.6, 1:16.04.10), uuid-runtime:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), libfdisk1:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), libapt-inst2.0:amd64 (1.2.20, 1.2.24), python3-software-properties:amd64 (0.96.20.6, 0.96.20.7), cloud-initramfs-dyn-netconf:amd64 (0.27ubuntu1.3, 0.27ubuntu1.4), update-notifier-common:amd64 (3.168.4, 3.168.5), libgnutls-openssl27:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), libsystemd0:amd64 (229-4ubuntu17, 229-4ubuntu21), grub-common:amd64 (2.02~beta2-36ubuntu3.9, 2.02~beta2-36ubuntu3.14), apt:amd64 (1.2.20, 1.2.24), mdadm:amd64 (3.3-2ubuntu7.2, 3.3-2ubuntu7.6), libkmod2:amd64 (22-1ubuntu4, 22-1ubuntu5), libmount1:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), snapd:amd64 (2.24.1, 2.28.5), vlan:amd64 (1.9-3.2ubuntu1.16.04.1, 1.9-3.2ubuntu1.16.04.4), bind9-host:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4, 1:1.2.8.dfsg-2ubuntu4.1), snap-confine:amd64 (2.24.1, 2.28.5), lshw:amd64 (02.17-1.1ubuntu3.2, 02.17-1.1ubuntu3.4), open-iscsi:amd64 (2.0.873+git0.3b4b4500-14ubuntu3.3, 2.0.873+git0.3b4b4500-14ubuntu3.4), dnsutils:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), sudo:amd64 (1.8.16-0ubuntu1.4, 1.8.16-0ubuntu1.5), dnsmasq-base:amd64 (2.75-1ubuntu0.16.04.3, 2.75-1ubuntu0.16.04.4), ubuntu-standard:amd64 (1.361, 1.361.1), util-linux:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), coreutils:amd64 (8.25-2ubuntu2, 8.25-2ubuntu3~16.04), openssh-sftp-server:amd64 (1:7.2p2-4ubuntu2.1, 1:7.2p2-4ubuntu2.2), grub2-common:amd64 (2.02~beta2-36ubuntu3.9, 2.02~beta2-36ubuntu3.14), libisc160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), udev:amd64 (229-4ubuntu17, 229-4ubuntu21), plymouth-theme-ubuntu-text:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), resolvconf:amd64 (1.78ubuntu4, 1.78ubuntu5), ubuntu-server:amd64 (1.361, 1.361.1), libklibc:amd64 (2.0.4-8ubuntu1.16.04.3, 2.0.4-8ubuntu1.16.04.4), isc-dhcp-common:amd64 (4.3.3-5ubuntu12.6, 4.3.3-5ubuntu12.7), grub-legacy-ec2:amd64 (0.7.9-90-g61eb03fe-0ubuntu1~16.04.1, 17.1-46-g7acc9e68-0ubuntu1~16.04.1), libapt-pkg5.0:amd64 (1.2.20, 1.2.24), initramfs-tools-bin:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), kmod:amd64 (22-1ubuntu4, 22-1ubuntu5), libudev1:amd64 (229-4ubuntu17, 229-4ubuntu21), libapparmor1:amd64 (2.10.95-0ubuntu2.6, 2.10.95-0ubuntu2.7), lxd:amd64 (2.0.9-0ubuntu1~16.04.2, 2.0.11-0ubuntu1~16.04.4), libplymouth4:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), mount:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), liblxc1:amd64 (2.0.7-0ubuntu1~16.04.2, 2.0.8-0ubuntu1~16.04.2), gcc-5-base:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), ubuntu-minimal:amd64 (1.361, 1.361.1), apport:amd64 (2.20.1-0ubuntu2.13, 2.20.1-0ubuntu2.14), owncloud-files:amd64 (9.1.4-1.1, 10.0.4-1.1), libblkid1:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), dpkg:amd64 (1.18.4ubuntu1.2, 1.18.4ubuntu1.3), libapparmor-perl:amd64 (2.10.95-0ubuntu2.6, 2.10.95-0ubuntu2.7), libisc-export160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu3.9, 2.02~beta2-36ubuntu3.14), python3-distupgrade:amd64 (1:16.04.21, 1:16.04.23), xfsprogs:amd64 (4.3.0+nmu1ubuntu1, 4.3.0+nmu1ubuntu1.1), python3-update-manager:amd64 (1:16.04.6, 1:16.04.10), ubuntu-release-upgrader-core:amd64 (1:16.04.21, 1:16.04.23), python3-apport:amd64 (2.20.1-0ubuntu2.13, 2.20.1-0ubuntu2.14), systemd-sysv:amd64 (229-4ubuntu17, 229-4ubuntu21), libuuid1:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), liblwres141:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), ubuntu-core-launcher:amd64 (2.24.1, 2.28.5), libpam-systemd:amd64 (229-4ubuntu17, 229-4ubuntu21), distro-info-data:amd64 (0.28ubuntu0.3, 0.28ubuntu0.5), libdrm2:amd64 (2.4.70-1~ubuntu16.04.1, 2.4.76-1~ubuntu16.04.1), systemd:amd64 (229-4ubuntu17, 229-4ubuntu21), libsmartcols1:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), libcryptsetup4:amd64 (2:1.6.6-5ubuntu2, 2:1.6.6-5ubuntu2.1), openssh-server:amd64 (1:7.2p2-4ubuntu2.1, 1:7.2p2-4ubuntu2.2), apt-utils:amd64 (1.2.20, 1.2.24), iproute2:amd64 (4.3.0-1ubuntu3, 4.3.0-1ubuntu3.16.04.2), openssh-client:amd64 (1:7.2p2-4ubuntu2.1, 1:7.2p2-4ubuntu2.2), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu3.9, 2.02~beta2-36ubuntu3.14), sosreport:amd64 (3.2+git276-g7da50d6-3ubuntu1, 3.4-1~ubuntu16.04.1), shim-signed:amd64 (1.27~16.04.1+0.9+1474479173.6c180c6-1ubuntu1, 1.32~16.04.1+0.9+1474479173.6c180c6-1ubuntu1), bsdutils:amd64 (1:2.27.1-6ubuntu3.2, 1:2.27.1-6ubuntu3.3), libdns162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), plymouth:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libxml2:amd64 (2.9.3+dfsg1-1ubuntu0.4, 2.9.3+dfsg1-1ubuntu0.5), grub-efi-amd64-signed:amd64 (1.66.9+2.02~beta2-36ubuntu3.9, 1.66.14+2.02~beta2-36ubuntu3.14), logrotate:amd64 (3.8.7-2ubuntu2, 3.8.7-2ubuntu2.16.04.2), libgnutls30:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), unattended-upgrades:amd64 (0.90ubuntu0.3, 0.90ubuntu0.8), btrfs-tools:amd64 (4.4-1, 4.4-1ubuntu1), apparmor:amd64 (2.10.95-0ubuntu2.6, 2.10.95-0ubuntu2.7), libisccc140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), apt-transport-https:amd64 (1.2.20, 1.2.24), libbind9-140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.8, 1:9.10.3.dfsg.P4-8ubuntu1.9), overlayroot:amd64 (0.27ubuntu1.3, 0.27ubuntu1.4), cloud-initramfs-copymods:amd64 (0.27ubuntu1.3, 0.27ubuntu1.4), libstdc++6:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), isc-dhcp-client:amd64 (4.3.3-5ubuntu12.6, 4.3.3-5ubuntu12.7), klibc-utils:amd64 (2.0.4-8ubuntu1.16.04.3, 2.0.4-8ubuntu1.16.04.4), cryptsetup:amd64 (2:1.6.6-5ubuntu2, 2:1.6.6-5ubuntu2.1), python3-problem-report:amd64 (2.20.1-0ubuntu2.13, 2.20.1-0ubuntu2.14), lxd-client:amd64 (2.0.9-0ubuntu1~16.04.2, 2.0.11-0ubuntu1~16.04.4), initramfs-tools-core:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), initramfs-tools:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), less:amd64 (481-2.1ubuntu0.1, 481-2.1ubuntu0.2), base-files:amd64 (9.4ubuntu4.4, 9.4ubuntu4.5), lxcfs:amd64 (2.0.6-0ubuntu1~16.04.1, 2.0.8-0ubuntu1~16.04.2), software-properties-common:amd64 (0.96.20.6, 0.96.20.7)
Remove: owncloud:amd64 (9.1.4-1.1)
End-Date: 2017-12-14  07:57:31


Start-Date: 2017-12-15  06:03:04
Commandline: /usr/bin/unattended-upgrade
Install: linux-headers-4.4.0-104:amd64 (4.4.0-104.127, automatic), linux-image-4.4.0-104-generic:amd64 (4.4.0-104.127, automatic), linux-signed-image-4.4.0-104-generic:amd64 (4.4.0-104.127, automatic), linux-image-extra-4.4.0-104-generic:amd64 (4.4.0-104.127, automatic), linux-headers-4.4.0-104-generic:amd64 (4.4.0-104.127, automatic)
Upgrade: linux-headers-generic:amd64 (4.4.0.103.108, 4.4.0.104.109), linux-signed-image-generic:amd64 (4.4.0.103.108, 4.4.0.104.109), linux-signed-generic:amd64 (4.4.0.103.108, 4.4.0.104.109)
End-Date: 2017-12-15  06:08:01


Start-Date: 2017-12-18  23:15:32
Commandline: apt-get install -y php-apcu php-redis redis-server php7.0-ldap php-smbclient
Requested-By: whmcloud (1000)
Install: libldb1:amd64 (2:1.1.24-1ubuntu3, automatic), libcups2:amd64 (2.1.3-4ubuntu0.3, automatic), php-igbinary:amd64 (1.2.1-10-ge0e66b9+1.2.1-2, automatic), libwbclient0:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.12, automatic), libavahi-common-data:amd64 (0.6.32~rc+dfsg-1ubuntu2, automatic), libavahi-common3:amd64 (0.6.32~rc+dfsg-1ubuntu2, automatic), libpython2.7:amd64 (2.7.12-1ubuntu0~16.04.2, automatic), libtalloc2:amd64 (2.1.5-2, automatic), python-talloc:amd64 (2.1.5-2, automatic), samba-libs:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.12, automatic), redis-tools:amd64 (2:3.0.6-1, automatic), php7.0-ldap:amd64 (7.0.22-0ubuntu0.16.04.1), libsmbclient:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.12, automatic), libjemalloc1:amd64 (3.6.0-9ubuntu1, automatic), libtdb1:amd64 (1.3.8-2, automatic), php-redis:amd64 (2.2.7-389-g2887ad1+2.2.7-1), php-smbclient:amd64 (0.8.0~rc1-2build1), redis-server:amd64 (2:3.0.6-1), libavahi-client3:amd64 (0.6.32~rc+dfsg-1ubuntu2, automatic), libtevent0:amd64 (0.9.28-0ubuntu0.16.04.1, automatic)
End-Date: 2017-12-18  23:20:36


Start-Date: 2017-12-21  07:33:14
Commandline: apt install aptitude
Requested-By: whmcloud (1000)
Install: libparse-debianchangelog-perl:amd64 (1.2.0-8, automatic), libsigc++-2.0-0v5:amd64 (2.6.2-1, automatic), libsub-name-perl:amd64 (0.14-1build1, automatic), aptitude-common:amd64 (0.7.4-2ubuntu2, automatic), libio-string-perl:amd64 (1.08-3, automatic), libcwidget3v5:amd64 (0.5.17-4ubuntu2, automatic), libboost-iostreams1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1, automatic), aptitude:amd64 (0.7.4-2ubuntu2), libclass-accessor-perl:amd64 (0.34-1, automatic), libxapian22v5:amd64 (1.2.22-2, automatic)
End-Date: 2017-12-21  07:33:41



```

 [ATTACH=CONFIG]277904[/ATTACH][ATTACH=CONFIG]277905[/ATTACH]


I only think that is a bit strange, because it was the first time i saw "apt autoremove" doing something like this, i never had so a problem...:-k

i am happy that i had a system backup from the night before.... :p 
And also today somehow after some other installations and a apt-get clean, now i get this output
[ATTACH=CONFIG]277906[/ATTACH]

I actually think that the theme folder and images changed were responsible for that, because, in the day of the update it came out a error saying that the theme folder and core/img could not be changed by the update....:-k


So everything is going well now. In the Future I just have to pay attention before i confirm something before removals or upgrades...


Many Thanks from

Aquiles dos Santos Crespo

---

### Post by LHammonds on 2017-12-22
> **aquilescrespo said:**
> 
I actually think that the theme folder and images changed were responsible for that, because, in the day of the update it came out a error saying that the theme folder and core/img could not be changed by the update....:-k

If the update could not modify specific folders, then you have permission problems.

Anytime you touch something on a web site, you have to fix the file ownership and permissions so that the web service and system can maintain control over them.

I actually have a script that runs on an automated basis that fixes all the permissions how they are supposed to be on the website so that even if I forget, the server will automatically correct it for me.  [My Script](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=234#p539)

LHammonds

---

### Post by dunwich42 on 2018-02-08
I've just had the same thing happen to me - and luckily I've still got my history.

Firstly I did a normal upgrade

```

# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  owncloud-files
The following packages will be upgraded:
  apparmor cloud-guest-utils cloud-image-utils cloud-utils grub-common grub-pc grub-pc-bin grub2-common
  libapache2-mod-php7.0 libapparmor-perl libapparmor1 libparted2 parted php7.0 php7.0-cli php7.0-common php7.0-curl
  php7.0-gd php7.0-imap php7.0-intl php7.0-json php7.0-mbstring php7.0-mcrypt php7.0-mysql php7.0-opcache php7.0-pgsql
  php7.0-readline php7.0-sqlite3 php7.0-xml php7.0-zip
30 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 8,497 kB of archives.
After this operation, 10.2 kB of additional disk space will be used.
Do you want to continue? [Y/n] y

```

Then because something was held back I ran a dist-upgrade.

```

# apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libc-client2007e libmcrypt4 libpq5 libzip4 mlock owncloud-deps-php7.0 owncloud-files php7.0-curl php7.0-imap
  php7.0-intl php7.0-mbstring php7.0-mcrypt php7.0-mysql php7.0-pgsql php7.0-sqlite3 php7.0-xml php7.0-zip
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  owncloud
The following packages will be upgraded:
  owncloud-files
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 34.3 MB of archives.
After this operation, 16.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y

```

In my case I assumed that owncloud was replacing owncloud-files, so went ahead with the autoremove which removed all of the owncloud application files.

I needed to install owncloud-files back again and everything was fine.

---

### Post by richardwe on 2018-11-10
Thanks that worked for me too, after autoremove owncloud-files was removed.
The folder /var/www/owncloud had just three folders left. (data, config, apps)
After reinstalling owncloud-files the /var/www/owncloud folder was repopulated with the php scripts, but the apache config was gone.
I had additionally to follow this guide 
[https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html#apache-configuration-label](https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html#apache-configuration-label)

which basically adds a file owncloud.conf to sites-available of apache2:
Alias /owncloud "/var/www/owncloud/"

<Directory /var/www/owncloud/>
  Options +FollowSymlinks
  AllowOverride All

 <IfModule mod_dav.c>
  Dav off
 </IfModule>

 SetEnv HOME /var/www/owncloud
 SetEnv HTTP_HOME /var/www/owncloud

</Directory>
After enabling this site and restarting apache owncloud was back again like before.

---

