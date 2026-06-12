---
title: "dpkg-buildpackage error"
date: 2010-02-12
forum: Server Platforms
---

### Post by iclebyte on 2010-02-12
Hi,

I'm attempting to apply the quota patch to postfix 2.5.1.

I have done the following..

```
cd /usr/src/
apt-get source postfix
wget [http://vda.sourceforge.net/VDA/postfix-2.5.1-vda-ng.patch.gz](http://vda.sourceforge.net/VDA/postfix-2.5.1-vda-ng.patch.gz)
gunzip postfix-2.5.1-vda-ng.patch.gz
cd postfix-2.5.1
patch -p1 < ../postfix-2.5.1-vda-ng.patch
dpkg-buildpackage
```

The resulting output is as follows

```
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
[B]tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1[/B]
```

I have searched hi and low and still can't work out how to resolve this.

Any help most appreciated!

---

### Post by jobix on 2010-02-12
Did you try doing the same using "sudo", i.e.,

sudo apt-get ...
sudo wget ...
etc...

---

### Post by iclebyte on 2010-02-12
I've actually resolved this.

I had downloaded the source using 'apt-get source postfix' which also downloads a ubuntu diff file. However, I'd messed about with the source so much that I was extracting it manually using 'tar -zxvf postfix-postfix_2.5.1.orig.tar.gz'. Thats fine except that when you download using 'apt-get source postfix' apt applies the diff files which installs the debian/ directory into the source code.

So.. if anybody has this error message my suggestion is to remove ALL the source archives then download them again using 'apt-get source postfix' then execute dpkg-buildpackage in the source directory.

Win!

---

