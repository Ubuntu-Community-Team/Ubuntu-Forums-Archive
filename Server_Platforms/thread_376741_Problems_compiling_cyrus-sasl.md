---
title: "Problems compiling cyrus-sasl"
date: 2007-03-05
forum: Server Platforms
---

### Post by ovelaur on 2007-03-05
Hi

I am quite new to Linux, and may perhaps aiming to high with my ambitions in the beginning...

Anyway, I am using Samba today as a domain controller, but wants to upgrade this to be using LDAP. Some googleing has been done, and I have found out that some other packages such as Kerberos, OpenSSL, Berkeley-DB and Cyrus SASL should be installed first.

Kerberos was installed using apt-get heimdal-clients

OpenSSL and Berkeley-DB has been installed using the latest stable sources and compiling these.

However Cyrus SASL will not compile. I have been using the tips on [http://www.delouw.ch/linux/Postfix-Cyrus-Web-cyradm-HOWTO/html/install.html]("http://www.delouw.ch/linux/Postfix-Cyrus-Web-cyradm-HOWTO/html/install.html") to help me on the ./configure tokens. This does not make much sens to me though, but I am trying.

The error shows up when running the command *make*:

auth_getpwent.c:48:20: error: des.h: No such file or directory
...
...

I have tried *whereis des.h*,  but I do not find a header file with this name.

Anyone that may be able to help me??

---

### Post by Mr. C. on 2007-03-05
Use find, not whereis.

OpenSSL and other packages often install under their own directories in /usr/local.  You need to configure your builds to look in those places, such as

  --with-openssl=/usr/local/ssl

des.h comes with openssl.  It should be found with the above.

Is there any reason why you are not starting with a package that already contains these libraries so that you do not have to build?

MrC

---

### Post by ovelaur on 2007-03-06
> **Mr. C. said:**
> Use find, not whereis.

OpenSSL and other packages often install under their own directories in /usr/local.  You need to configure your builds to look in those places, such as

  --with-openssl=/usr/local/ssl

des.h comes with openssl.  It should be found with the above.

Is there any reason why you are not starting with a package that already contains these libraries so that you do not have to build?

MrC

Thanks, I found the file under /usr/local/ssl/openssl/include
But I did not find out how to use *find* for searching in subdirectories...

The reason for building and compiling myself? I have no other good reasons for that other than the "perfect Ubuntu setup" guide that I did use, did not contain these packages. And as I was completly new to Linux, thats just how I started. I could reinstall now, and perhaps will do sometime. But the way I am doing now may be slow and timeconsuming, but it is a way of learning. And I have been using computers since 1982, and everything is self-learned. Today it is much easier to learn stuff due to the internet. And hopefully I will in the future be able to run all my needed programs at at Linux desktops in a Linux server configuration. And also be able to maintain my computer park myself. Not to save money, but because for me it is also a hobby.

However, I was helped at this issue. And of course a lot of new errors showed ut when trying to build the code. But I am one step closer (or furter away :confused: ). I see that I need to learn more about using the ./configure command.

Thank U for your kind help.

---

### Post by Mr. C. on 2007-03-06
Your find command:

  find startdirname -name des.h -ls

will do what you want.  Replace startdirname with the directory from where you want searching to commence.

Your reasons are good enough for me! :-)

The more you use configure, the easier it gets.  The first couple are a bit daunting, but you'll soon discover they all start looking the same.

Keep your configure options in a file, and just sh the file, as in:

$cat file.config
./configure -prefix=/usr --bindir=/usr/bin --datadir=/usr/share --mandir=/usr/share --enable-fsect-man5

This way, you can just (re-)run the config with:

sh file.config

and get the config completed.  When you want to change options, just add it to the file and re-run.

MrC

---

