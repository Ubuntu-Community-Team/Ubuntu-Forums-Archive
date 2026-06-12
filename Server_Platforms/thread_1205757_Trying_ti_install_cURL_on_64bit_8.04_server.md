---
title: "Trying ti install cURL on 64bit 8.04 server"
date: 2009-07-06
forum: Server Platforms
---

### Post by wxman on 2009-07-06
I can't seem to get cURL to work on my 8.04 64bit server. I've tried aptitude install php5-curl and get:
```
The following packages are BROKEN:
  php5-curl
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.0kB of archives. After unpacking 123kB will be used.
The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5.6) but 5.2.9-0.dotdeb.2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libapache2-mod-php5
php5
php5-imagick

Downgrade the following packages:
php-pear [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-cgi [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-cli [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-common [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-gd [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-mcrypt [5.2.9-0.dotdeb.2 (now) -> 5.2.3-0ubuntu1 (hardy)]
php5-mysql [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]

Score is 467

```
My sources.list is:
```
# deb cdrom:[Ubuntu-Server 8.04.2 _Hardy Heron_ - Release amd64 (20090121.1)]/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted
## Major bug fix updates produced after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
## offered by Canonical and the respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```
Has anyone run into this problem and found a solution?

---

### Post by wxman on 2009-07-07
I was finally able to fix this. It ended up that I accidentally installed the wrong version of one of the php libraries. I think it happened when I turned on a dotdeb source to try out one program. I think when I did that, I updated php5-common without knowing it. The only way to fix it was to uninstall php5-common and all associated with it. Then I reinstalled all the php5 files over again from the correct sources. At least that worked for me.

---

