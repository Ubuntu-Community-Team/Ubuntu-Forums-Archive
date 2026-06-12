---
title: "Package authentication issue from us.archive.ubuntu.com ?? !!"
date: 2013-04-09
forum: Security
---

### Post by MWP on 2013-04-09
Hi all,

Im trying to run the normal scheduled update & upgrade on my 10.04 LTS servers.

Im having the problem of...

```

root@kvm-host:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  bind9-host dnsutils libbind9-60 libdns64 libisc60 libisccc60 libisccfg60 liblwres60 libnspr4-0d libnss3-1d
  libpam-modules libpam-runtime libpam0g libperl5.10 libxml2 libxml2-utils libxslt1.1 linux-libc-dev perl perl-base
  perl-modules python-libxml2
22 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 4,217kB/14.7MB of archives.
After this operation, 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  perl-modules perl libperl5.10 perl-base libpam-modules libpam-runtime libpam0g libxml2 bind9-host dnsutils libisc60
  libdns64 libisccc60 libisccfg60 liblwres60 libbind9-60 libnspr4-0d libnss3-1d libxml2-utils libxslt1.1
  linux-libc-dev python-libxml2
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated

```

My sources list looks like:
```

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

"apt-get update" runs without any issues/warnings.

Does anyone know what the issue might be?
Its the first time ive come across this problem.

Thanks in advance!!

---

### Post by papibe on 2013-04-09
Hi

Try this:
```
sudo apt-**[COLOR="#FF0000"]key[/COLOR]** update

sudo apt-get update
```
Let us know how it goes.
Regards.

---

### Post by MWP on 2013-04-09
> 
root@kvm-host:~# apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2


Then then did update (no issues).
apt-get upgrade then gave the same "The following packages cannot be authenticated" as above.

---

### Post by MWP on 2013-04-09
I just tried changing the mirror source to "http://au.archive.ubuntu.com/ubuntu/" on one of the servers.
update & upgrade ran perfectly.

---

### Post by papibe on 2013-04-09
**EDIT: It seems you solved it already.**

Could you post the result of these commands?
```
lsb_release -a

sudo apt-key list
```
Regards.

---

### Post by MWP on 2013-04-09
> 
root@kvm-host:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

root@kvm-host:~# apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/B64F0AFA 2009-06-10
uid                  Launchpad ubuntu-ha

pub   1024R/56497ED8 2009-07-07
uid                  Launchpad Stable backported cluster stack


Thanks.

---

### Post by MWP on 2013-04-09
BTW... using the AU mirror is a temporary fix.
I definitely do want go back to using the US mirrors, so getting this fixed is important.

---

