---
title: "Setting up my own repository, building .deb's"
date: 2007-06-09
forum: Repositories &amp; Backports
---

### Post by wags08 on 2007-06-09
Hello,

I manage a lab of computers.  When I'm working with software that's in aptitude, it's very easy for us to install it on all the machines thanks to a shell script we've written...but the problem comes when we need a piece of software that is not in the repositories.

For example, there is a chemistry program we're installing in our lab called Gaussview that is not in the repository.

So what I'd like to do is setup a repository for our own "custom" deb files on one of our servers on the network and add it ot the /etc/apt/sources.list files on our individual machines.  Then, for the example in the previous paragraph, I could easily do a "aptitude install gaussview" instead of having to untar and move the files to the right place, install the missing libraries, put symlinks where needed, etc.

Could somebody please explain how to create deb packages and set up a repository, or at least point me in the right direction to do it?

I've searched around on the internet, and the only thing I've seen for the repository set up is how to create mirrors of Ubuntu's repositories...nothing about manually setting up your own.

Thanks,
Jason

---

### Post by az on 2007-06-09
See:
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

And there is also:

apt-cache show dak
Package: dak
Priority: optional
Section: universe/misc
Installed-Size: 1168
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Joerg Jaspert <joerg@debian.org>
Architecture: i386
Version: 1.0-8.4ubuntu2
Depends: libapt-pkg-libc6.4-6-3.53, libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2), libstdc++6 (>= 4.1.2), python-central (>= 0.5.8), python (>= 2.3), python-pygresql, python-apt, apt-utils, gnupg, dpkg-dev, debconf | debconf-2.0, ucf, postfix | mail-transport-agent, python-ldap, bzip2
Recommends: python-gnupginterface, sudo
Suggests: lintian, linda, less, binutils-multiarch, symlinks, postgresql, procmail, rsync, debbugs
Filename: pool/universe/d/dak/dak_1.0-8.4ubuntu2_i386.deb
Size: 253832
MD5sum: e7c147b54c6604f1d213c3f4f450b8fd
SHA1: f8fefad364c7178bf4a51933ec580f9ed1eb4014
SHA256: d35cf2a7f9dbbf6f09fd76a0654ca7bdb24a380990a3e73d89fc6d79deec3b29
Description: Debian's archive maintenance scripts
 This is a collection of archive maintenance scripts used by the
 Debian project.
 .
 You don't want to use this if you only have a few hundred packages to maintain.
 Look at mini-dinstall or debarchiver or maybe even apt-ftparchive for this.
 .
 This is for a big archive, but there it is the best you can get.
 .
 You need a running postgresql, but as this can be on some other host its only
 a Suggests - install package postgresql if you want it local.
Python-Version: >= 2.3
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


But don't forget:


apt-cache show apt-utils
Package: apt-utils
Priority: important
Section: admin
Installed-Size: 488
Maintainer: Michael Vogt <mvo@ubuntu.com>
Original-Maintainer: APT Development Team <deity@lists.debian.org>
Architecture: i386
Source: apt
Version: 0.6.46.4ubuntu10
Replaces: apt (<< 0.5.9)
Provides: libapt-inst-libc6.4-6-1.1
Depends: libapt-pkg-libc6.4-6-3.53, libc6 (>= 2.5-0ubuntu1), libdb4.4, libgcc1 (>= 1:4.1.2), libstdc++6 (>= 4.1.2)
Filename: pool/main/a/apt/apt-utils_0.6.46.4ubuntu10_i386.deb
Size: 202726
MD5sum: 72f9ebc439792f93cc8364ad33506041
SHA1: b518aa07c6b4e92efaef39d17fe7e655d1b6935e
SHA256: d5debd5dbbfe2751ed593833ffca7726a3c730abd72bbe46f87d817462634187
Description: APT utility programs
 This package contains some APT utility programs such as apt-ftparchive,
 apt-sortpkgs and apt-extracttemplates.
 .
 apt-extracttemplates is used by debconf to prompt for configuration
 questions before installation. apt-ftparchive is used to create Package
 and other index files. apt-sortpkgs is a Package/Source file normalizer.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: minimal

---

