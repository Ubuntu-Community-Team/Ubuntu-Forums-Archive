---
title: "Installation of PHP fails"
date: 2018-04-03
forum: Repositories &amp; Backports
---

### Post by csdgbas on 2018-04-03
```
~$ sudo apt install php7.0-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  php-common php7.0-common php7.0-json php7.0-opcache php7.0-readline
Suggested packages:
  php-pear
The following NEW packages will be installed
  php-common php7.0-cli php7.0-common php7.0-json php7.0-opcache
  php7.0-readline
0 to upgrade, 6 to newly install, 0 to remove and 12 not to upgrade.
Need to get 2,238 kB of archives.
After this operation, 9,630 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Err:1 http://security.ubuntu.com/ubuntu zesty-security/main amd64 php7.0-common amd64 7.0.22-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:2 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 php-common all 1:49
  404  Not Found [IP: 91.189.88.162 80]
Err:3 http://security.ubuntu.com/ubuntu zesty-security/main amd64 php7.0-json amd64 7.0.22-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:4 http://security.ubuntu.com/ubuntu zesty-security/main amd64 php7.0-opcache amd64 7.0.22-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:5 http://security.ubuntu.com/ubuntu zesty-security/main amd64 php7.0-readline amd64 7.0.22-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:6 http://security.ubuntu.com/ubuntu zesty-security/main amd64 php7.0-cli amd64 7.0.22-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:2 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 php-common all 1:49
  404  Not Found [IP: 91.189.88.162 80]
E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/php-defaults/php-common_49_all.deb  404  Not Found [IP: 91.189.88.162 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-common_7.0.22-0ubuntu0.17.04.1_amd64.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-json_7.0.22-0ubuntu0.17.04.1_amd64.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-opcache_7.0.22-0ubuntu0.17.04.1_amd64.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-readline_7.0.22-0ubuntu0.17.04.1_amd64.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php7.0/php7.0-cli_7.0.22-0ubuntu0.17.04.1_amd64.deb  404  Not Found [IP: 91.189.88.152 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

So I tried apt-get update:
```
Ign:1 http://gb.archive.ubuntu.com/ubuntu zesty InRelease
Err:2 http://gb.archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 91.189.88.149 80]
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease
Get:4 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]
Get:5 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]
Get:6 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,350 B]
Reading package lists... Done      
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by #&amp;thj^% on 2018-04-03
17.04 has been out of support for a few months now so that explains your problem.;)
either upgrade/install  17.10 or stay with the LTS 16.04 supported till 2021

---

### Post by csdgbas on 2018-04-03
What, and in three months upgrade again? No.  Forget it, I'm going back to Windows.  Canonical forcing people to upgrade is unacceptable.

---

### Post by mörgæs on 2018-04-03
Almost a year ago a poster informed you about the long term support option. The long- versus short term support choice can hardly come as a surprise. 

[https://ubuntuforums.org/showthread.php?t=2361966&p=13647997&viewfull=1#post13647997](https://ubuntuforums.org/showthread.php?t=2361966&p=13647997&viewfull=1#post13647997)

---

### Post by oldos2er on 2018-04-03
And we're done. I'd like to remind everyone to please be courteous and polite.

Closed.

---

