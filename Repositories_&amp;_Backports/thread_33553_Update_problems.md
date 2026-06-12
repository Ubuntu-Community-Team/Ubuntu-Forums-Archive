---
title: "Update problems"
date: 2005-05-11
forum: Repositories &amp; Backports
---

### Post by Spirit on 2005-05-11
Im trying to install mplayer and i get following error

[B]The following packages have unmet dependencies:
  mplayer-586: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed[/B]

When i try apt-get update i gat this message

[B]Reading package lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems[/B]

---

### Post by spd106 on 2005-05-11
Hi, have you tried the authentication method found on this wiki page
[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)

Hope this helps

---

### Post by Spirit on 2005-05-12
i've tried but like i said here [http://www.ubuntuforums.org/showthread.php?p=142066#post142066](http://www.ubuntuforums.org/showthread.php?p=142066#post142066)

---

