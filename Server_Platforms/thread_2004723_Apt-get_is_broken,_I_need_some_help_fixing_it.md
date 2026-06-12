---
title: "Apt-get is broken, I need some help fixing it"
date: 2012-06-16
forum: Server Platforms
---

### Post by cusinndzl on 2012-06-16
The power went out in my house when I was updating my applications on my Ubuntu 12.04 server. After starting back up the server I'm getting some errors when trying to do things with apt-get. 

Here's the error when I type apt-get -f install. From what I can tell it looks like when mysql-client-5.5 was updating the power went out and because of that apt-get is having some issues. 

Can anyone help me out?

> 
root@ubuntu:/var/cache/apt/archives# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-23-generic linux-headers-3.2.0-23
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-client-5.5
Suggested packages:
  libterm-readkey-perl
The following packages will be upgraded:
  mysql-client-5.5
1 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
Need to get 0 B/10.3 MB of archives.
After this operation, 7,139 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 105091 files and directories currently installed.)
Preparing to replace mysql-client-5.5 5.5.22-0ubuntu1 (using .../mysql-client-5.5_5.5.25-1~dotdeb.0_amd64.deb) ...
Unpacking replacement mysql-client-5.5 ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.5_5.5.25-1~dotdeb.0_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mysql', which is also in package mysql-client-core-5.5 5.5.24-0ubuntu0.12.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-5.5_5.5.25-1~dotdeb.0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by N0oki3 on 2012-06-16
Hello there. You can try:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/mysql-client-5.5_5.5.25-1~dotdeb.0_amd64.deb

```


after ward
```
sudo apt-get autoremove 
sudo apt-get update
```

or remove package```

sudo apt-get remove --purge getdeb-repository

```


If not, post ```

sudo dpkg --configure -a
cat /etc/apt/sources.list

```

Might helps us more

---

### Post by cusinndzl on 2012-06-16
> **N0oki3 said:**
> Hello there. You can try:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/mysql-client-5.5_5.5.25-1~dotdeb.0_amd64.deb

```

or remove package```

sudo apt-get remove --purge getdeb-repository

```

after ward
```
sudo apt-get autoremove 
sudo apt-get update
```

If not, post ```

sudo dpkg --configure -a
cat /etc/apt/sources.list

```

Might helps us more

Thanks, that worked.

---

