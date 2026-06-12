---
title: "Holding gir1.2-gtk-3.0 and perl for 4 days"
date: 2011-12-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-03
Are you guys holding this packages for some days now? I'm beginning to get worried with other deps. I do use perl for my own stuff.

```
The following packages have been kept back:
  gir1.2-gtk-3.0 libalgorithm-diff-xs-perl libapt-pkg-perl libcairo-perl
  libgail-3-0 libglib-perl libgtk-3-0 libgtk-3-bin libgtk-3-dev libgtk2-perl
  libhtml-parser-perl libio-pty-perl libjson-xs-perl liblocale-gettext-perl
  libnet-dns-perl libnet-ssleay-perl libpango-perl libsnmp15 libsocket6-perl
  libsub-name-perl libtext-charwidth-perl libtext-iconv-perl libuuid-perl
  libxml-parser-perl libyaml-syck-perl lintian perl perl-base perl-modules
  perlmagick sessioninstaller

```

---

### Post by paul_in_london on 2011-12-03
I'm using the ricotz-testing ppa and the only things I can't upgrade at the moment if I try aptitude full-upgrade (i.e. held back with aptitude safe-upgrade) are:

```
The following packages will be upgraded:
  xserver-xorg-input-wacom{b} xserver-xorg-video-qxl{b} 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 152 kB of archives. After unpacking 45.1 kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-video-qxl: Depends: xorg-video-abi-10 which is a virtual package.
  xserver-xorg-input-wacom: Depends: xorg-input-abi-12 which is a virtual package.
```

Taking your first package as an example:

```
paul@precise-64:~$ apt-cache policy gir1.2-gtk-3.0
gir1.2-gtk-3.0:
  Installed: 3.3.5+git20111201.f9c24e8f-0ubuntu1~12.04~ricotz0
  Candidate: 3.3.5+git20111201.f9c24e8f-0ubuntu1~12.04~ricotz0
  Version table:
 *** 3.3.5+git20111201.f9c24e8f-0ubuntu1~12.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     3.2.2-2ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by PaulW2U on 2011-12-03
> **effenberg0x0 said:**
> Are you guys holding this packages for some days now? 

Nothing held back here in either Ubuntu or Kubuntu.

---

### Post by zika on 2011-12-04
> **effenberg0x0 said:**
> Are you guys holding this packages for some days now? I'm beginning to get worried with other deps. I do use perl for my own stuff.

```
The following packages have been kept back:
  gir1.2-gtk-3.0 libalgorithm-diff-xs-perl libapt-pkg-perl libcairo-perl
  libgail-3-0 libglib-perl libgtk-3-0 libgtk-3-bin libgtk-3-dev libgtk2-perl
  libhtml-parser-perl libio-pty-perl libjson-xs-perl liblocale-gettext-perl
  libnet-dns-perl libnet-ssleay-perl libpango-perl libsnmp15 libsocket6-perl
  libsub-name-perl libtext-charwidth-perl libtext-iconv-perl libuuid-perl
  libxml-parser-perl libyaml-syck-perl lintian perl perl-base perl-modules
  perlmagick sessioninstaller

```Did You try dist-upgrade to see what is going on?
64-bit Ubuntu, nothing on hold...

---

