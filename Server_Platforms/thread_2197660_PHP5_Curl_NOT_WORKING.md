---
title: "PHP5 Curl NOT WORKING"
date: 2014-01-04
forum: Server Platforms
---

### Post by kosterjacob8 on 2014-01-04
Ahhh! Pulling out my hair to get this! 

```


root@Genki:/var/www# sudo apt-get install libcurl3 php5-curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
libcurl3 is already the newest version.
libcurl3 set to manually installed.
The following NEW packages will be installed:
  php5-curl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.0 kB of archives.
After this operation, 117 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com/ubuntu/ precise-updates/main php5-curl i386 5.3.10-1ubuntu3.6
  404  Not Found [IP: 91.189.92.200 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main php5-curl i386 5.3.10-1ubuntu3.6
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.3.10-1ubuntu3.6_i386.deb  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@Genki:/var/www#



```

So yeah!

---

### Post by Doug S on 2014-01-05
Welcome to Ubuntu forums.

It seems to be looking for an obsolete version, it should be looking for 5.3.10-1ubuntu3.9.
You should try what the command failure message said and "run apt-get update" first, to bring your system up to date.

---

### Post by mörgæs on 2014-01-05
Regarding the root user:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

