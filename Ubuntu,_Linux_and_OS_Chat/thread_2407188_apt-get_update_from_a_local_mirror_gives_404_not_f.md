---
title: "apt-get update from a local mirror gives 404 not found"
date: 2018-11-30
forum: Ubuntu, Linux and OS Chat
---

### Post by theoharis on 2018-11-30
hello 
i have set up a local mirror via apt-mirror
this is the list

```
cat /etc/apt/mirror.listset nthreads     20
set _tilde 0


deb http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse


deb-src http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse


clean http://archive.ubuntu.com/ubuntu
```


this is my apache2 conf

```
<VirtualHost *:80>    ServerName cdk-juju
    ServerAlias *
    DocumentRoot /var/spool/apt-mirror/mirror/archive.ubuntu.com/
    LogLevel info
    ErrorLog /var/log/apache2/mirror-archive.ubuntu.com-error.log
    CustomLog /var/log/apache2/mirror-archive.ubuntu.com-access.log combined


    <Directory /var/spool/apt-mirror/>
      Options Indexes FollowSymLinks
      AllowOverride None
      Require all granted
    </Directory>
</VirtualHost>
```




apt-get update errors

```
sudo apt updateIgn:1 http://10.100.1.156/ubuntu bionic InRelease
Ign:2 http://10.100.1.156/ubuntu bionic-updates InRelease
Ign:3 http://10.100.1.156/ubuntu bionic-backports InRelease
Err:4 http://10.100.1.156/ubuntu bionic Release
  404  Not Found [IP: 10.100.1.156 80]
Err:5 http://10.100.1.156/ubuntu bionic-updates Release
  404  Not Found [IP: 10.100.1.156 80]
Err:6 http://10.100.1.156/ubuntu bionic-backports Release
  404  Not Found [IP: 10.100.1.156 80]
Get:7 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Reading package lists... Done
```

what could be wrong ? thanks

---

### Post by deadflowr on 2018-12-01
duplicate thread
[https://ubuntuforums.org/showthread.php?t=2407191]("https://ubuntuforums.org/showthread.php?t=2407191")
thread closed

---

