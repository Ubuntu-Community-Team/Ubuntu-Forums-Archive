---
title: "issue with installing openldap from source"
date: 2012-05-01
forum: Server Platforms
---

### Post by associates on 2012-05-01
Hi,

I was wondering if anyone might be able to help me with Ubuntu Server 10.04. I am a newbie to Linux. What I am trying to do is to install LAMP from the source onto my machine running on Ubuntu Server 10.04. I found some guides on how to download and install Apache2 - httpd-2.2.22, and put it under /usr/local/src. Since I would like to use LDAP, I included with-ldap to ./configure as follows

```
sudo ./configure --prefix=/usr/local/src/httpd-2.2.22 --enable-rewrite --enable-imagemap --enable-php --enable-ldap -- enable-authnz_ldap --enable-so --disable-userdir --disable-status -- with-ldap --with-auth-ldap --enable-auth-ldap
```

after running it, I received errors saying it could not find ldap library. So I went to download openldap-2.4.31 and put it under /usr/local/src. Unzip it and run only ```
./configure
```

Then, I got an error saying it requires Berkeley-db. So I went to download Berkeley-db (db-5.2.36) and put it under /usr/local/src. Unzip it and then do the following

```
cd db-5.2.36
cd build_unix
sudo ../dist/configure
```

No errors produced so far. I then run ```
$ sudo make
``` and run ```
$ sudo make install
```

Since it completed successfully, I went back to openldap-2.4.31, and run ```
$ sudo ./configure --with-tls=no
```

However, I am still getting the same error that says BDB/HDB: BerkeleyDB not available.

I am not sure what to do. Any help would be greatly appreciated.

Thank you

---

