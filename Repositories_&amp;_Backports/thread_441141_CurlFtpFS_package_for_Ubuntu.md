---
title: "CurlFtpFS package for Ubuntu"
date: 2007-05-12
forum: Repositories &amp; Backports
---

### Post by geco on 2007-05-12
CurlFtpFS package is available for Debian but not for (K)ubuntu, I was wandering if it will be available or if we will use Debian packages forever...
any ideas??

---

### Post by mlind on 2007-05-13
> **geco said:**
> CurlFtpFS package is available for Debian but not for (K)ubuntu, I was wandering if it will be available or if we will use Debian packages forever...
any ideas??

gutsy and feisty archives contain the curlftpfs package
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=curlftpfs](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=curlftpfs)

Do you need a backport for earlier Ubuntu version?

---

### Post by geco on 2007-05-13
> **mlind said:**
> gutsy and feisty archives contain the curlftpfs package
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=curlftpfs](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=curlftpfs)

Do you need a backport for earlier Ubuntu version?

For now I installed the Debian packages (and it seems to work), I also posted an HowTo (not yet approved by a moderator) because I needed to upgrade several Ubuntu packages with Debian ones.

Anyway it could be useful for Edgy users to have a curlftpfs package.

Thank you,
geco

EDIT:
I mean... it could be useful also for Dapper and earliest versions users :D

---

### Post by mlind on 2007-05-13
> **geco said:**
> For now I installed the Debian packages (and it seems to work), I also posted an HowTo (not yet approved by a moderator) because I needed to upgrade several Ubuntu packages with Debian ones.

Anyway it could be useful for Edgy users to have a curlftpfs package.

Thank you,
geco

EDIT:
I mean... it could be useful also for Dapper and earliest versions users :D

What packages you had to upgrade in order to do this? It's usually a very bad sign if you need to install several binaries from other distribution to satisfy a single package. Often this happens when package is not "binary-compatible" with your system. And this might result a cycle where you install more binaries from a foreign distribution and end up with a broken system.

At least avoid upgrading any core libraries.

Here's a curlftpfs backport for edgy. You can make an official backport request by using [lauchpad]("https://launchpad.net/distros/ubuntu") and filing a bug against the package.

---

### Post by geco on 2007-05-15
> **mlind said:**
> What packages you had to upgrade in order to do this? It's usually a very bad sign if you need to install several binaries from other distribution to satisfy a single package. Often this happens when package is not "binary-compatible" with your system. And this might result a cycle where you install more binaries from a foreign distribution and end up with a broken system.

At least avoid upgrading any core libraries.

Here's a curlftpfs backport for edgy. You can make an official backport request by using [lauchpad]("https://launchpad.net/distros/ubuntu") and filing a bug against the package.

First of all thank you for the backport and the advice.

I installed the following Debian packages:

curlftpfs_0.9-2+b2_i386.deb
fuse-utils_2.6.3-2_i386.deb
libcurl3-gnutls_7.15.5-1_i386.deb
libgpg-error0_1.4-2_i386.deb
libgpg-error-dev_1.4-2_i386.deb

---

### Post by mlind on 2007-05-15
> **geco said:**
> First of all thank you for the backport and the advice.

I installed the following Debian packages:

curlftpfs_0.9-2+b2_i386.deb
fuse-utils_2.6.3-2_i386.deb
libcurl3-gnutls_7.15.5-1_i386.deb
libgpg-error0_1.4-2_i386.deb
libgpg-error-dev_1.4-2_i386.deb

You said you had to install these from Debian, weren't these available in Ubuntu repository?

---

### Post by geco on 2007-05-16
I downloaded curlftpfs_0.9-2 from Debian Testing and the Edgy fuse-utils, libcurl3-gnutils etc. was an earlier version than required from Debian curlftpfs so I downloaded also the required dependency for Debian Testing.
If your advice is to switch back to Edgy packets I will install your backport and downgrade the other packets (for the moment everything seems to work well).

Thaks,
geco

---

### Post by mlind on 2007-05-16
downgrading is what I would do. You might run into dependency problems when something requires certain version of the library/utilities or is built against certain set of symbols which aren't found in the new installed library. It's probably okay to keep the "foreign" stuff though, I'm just speaking of my own experience.

---

### Post by geco on 2007-05-16
> **mlind said:**
> downgrading is what I would do. You might run into dependency problems when something requires certain version of the library/utilities or is built against certain set of symbols which aren't found in the new installed library. It's probably okay to keep the "foreign" stuff though, I'm just speaking of my own experience.

Ok, thank you very much. I will downgrade to Edgy packages as soon as possible.

byebye

---

### Post by geco on 2007-05-16
I downgraded from Debian Testing curlftpfs 0.9-2.b2 (and dependencies) to Ubuntu Edgy 0.9.1-1 (and dependencies) but in this way curlftpfs doesn't recognize the /etc/fstab line for mounting the FTP host
```

curlftpfs#ftpuser:ftppassword@ftp.host /mount/directory/path fuse allow_other,uid=myuid,gid=mygid,noauto 0 0

```
maybe curlftpfs 0.9.1 uses a different "grammar"?

EDIT:
I saw that curlftp fs 0.9.2 has been released for Festy... but there's no Edgy package... I don't want to bore you asking for another backport... I will ask for an official backport

---

### Post by mlind on 2007-05-16
0.9.1-1 version is greater than feisty's 0.9-2

---

### Post by geco on 2007-05-17
> **mlind said:**
> 0.9.1-1 version is greater than feisty's 0.9-2

Is you're right... it was late when I posted and I didn't realize... anyway, I don't know why fstab doesn't work with. I'll try to fix it later (I'll search for the documentation)

thanks

---

### Post by geco on 2007-05-22
> **mlind said:**
> downgrading is what I would do. You might run into dependency problems when something requires certain version of the library/utilities or is built against certain set of symbols which aren't found in the new installed library. It's probably okay to keep the "foreign" stuff though, I'm just speaking of my own experience.


Thank you for your help, finally I downgraded and everything worked... anyway - once I bought an external HD for backup - I decided to upgrade my system to feisty.

byebye
Geco

---

