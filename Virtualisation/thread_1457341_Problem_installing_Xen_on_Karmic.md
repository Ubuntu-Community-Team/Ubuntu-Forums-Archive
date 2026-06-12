---
title: "Problem installing Xen on Karmic"
date: 2010-04-18
forum: Virtualisation
---

### Post by sheperson on 2010-04-18
Hi,
I try to install Xen on Ubuntu 9.10, like this, but I get error:
```

$ sudo apt-get install ubuntu-xen-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-xen-desktop: Depends: libc6-xen but it is not going to be installed
                      Depends: python-xen-3.3 but it is not going to be installed
                      Depends: xen-utils-3.3 but it is not going to be installed
                      Depends: convirt but it is not going to be installed
E: Broken packages

```I tried another way to install Xen as described [here]("http://mediakey.dk/%7Ecc/ubuntu-howto-install-xen/") and I get this:
```

sudo aptitude install ubuntu-xen-desktop bridge-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libc6-xen python-dev python2.6-dev 
The following NEW packages will be installed:
  bridge-utils convirt debootstrap{a} libconfig-inifiles-perl{a} libdb4.6{a} libexpect-perl{a} libio-pty-perl{a} libio-stty-perl{a} 
  librpm0{a} librpmbuild0{a} librpmio0{a} libterm-readline-gnu-perl{a} libterm-size-perl{a} libtext-template-perl{a} libxen3 
  linux-generic-pae linux-image-2.6.31-14-generic-pae linux-image-generic-pae linux-server python-paramiko{a} python-rpm{a} 
  python-xen-3.3 python2.5{a} python2.5-minimal{a} reiserfsprogs{a} rinse{a} rpm{a} ubuntu-xen-desktop vnstat{a} xen-docs-3.3 
  xen-hypervisor-3.3 xen-shell{a} xen-tools xen-utils-3.3 xfsprogs{a} 
0 packages upgraded, 38 newly installed, 0 to remove and 6 not upgraded.
Need to get 48.2MB of archives. After unpacking 144MB will be used.
The following packages have unmet dependencies:
  libc6-xen: PreDepends: libc6 (= 2.10.1-0ubuntu15) but 2.10.1-0ubuntu16 is installed.
  python-dev: Depends: python (= 2.6.4~rc1-0ubuntu1) but 2.6.4-0ubuntu1 is installed.
  python2.6-dev: Depends: python2.6 (= 2.6.4~rc2-0ubuntu1) but 2.6.4-0ubuntu3 is installed.
                 Depends: libpython2.6 (= 2.6.4~rc2-0ubuntu1) but 2.6.4-0ubuntu3 is installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
libc-bin [2.10.1-0ubuntu16 (now) -> 2.10.1-0ubuntu15 (karmic)]
libc-dev-bin [2.10.1-0ubuntu16 (now) -> 2.10.1-0ubuntu15 (karmic)]
libc6 [2.10.1-0ubuntu16 (now) -> 2.10.1-0ubuntu15 (karmic)]
libc6-dbg [2.10.1-0ubuntu16 (now) -> 2.10.1-0ubuntu15 (karmic)]
libc6-dev [2.10.1-0ubuntu16 (now) -> 2.10.1-0ubuntu15 (karmic)]
libpython2.6 [2.6.4-0ubuntu3 (now) -> 2.6.4~rc2-0ubuntu1 (karmic)]
python [2.6.4-0ubuntu1 (now) -> 2.6.4~rc1-0ubuntu1 (karmic)]
python-minimal [2.6.4-0ubuntu1 (now) -> 2.6.4~rc1-0ubuntu1 (karmic)]
python2.6 [2.6.4-0ubuntu3 (now) -> 2.6.4~rc2-0ubuntu1 (karmic)]
python2.6-minimal [2.6.4-0ubuntu3 (now) -> 2.6.4~rc2-0ubuntu1 (karmic)]

Score is 354

Accept this solution? [Y/n/q/?]

```Any ideas?
Thanks in advance.

---

### Post by sheperson on 2010-04-20
Well, it seems no one has ever experienced this problem before !!
Now what is your idea about this:
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/161783](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/161783)

Is it the same problem? Has it been fixed?

---

### Post by tgalati4 on 2010-04-20
I bought a book on xen and I just started reading it.  I would presume that you need to be running the xen kernel to get the xen desktop to load properly.

apt-cache search xen

Try installing the xen hyperviser first.

---

### Post by sh1ny on 2010-04-21
I don't think you can run Ubuntu as a Dom0 anymore. The support for xen and openvz has been removed in favor of kvm.

EDIT : You can compile and install your own Xen kernel tho.

---

### Post by tgalati4 on 2010-04-21
Yes, that seems to be the case.  The hooks for the xen module have been removed, but you can recompile the kernel to include the xen functionality.

---

