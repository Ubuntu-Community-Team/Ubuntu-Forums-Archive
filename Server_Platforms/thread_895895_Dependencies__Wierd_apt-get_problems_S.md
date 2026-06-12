---
title: "Dependencies / Wierd apt-get problems :S"
date: 2008-08-20
forum: Server Platforms
---

### Post by Ravenamp on 2008-08-20
Hy, 

I've got this wierd problem when trying to install software through apt-get. I keep getting this error when doing apt-get -f install. it started downloading stuff, and when it's done it says:

**E: Internal Error, Could not perform immediate configuration (2) on libc6**
 
To solve this, I've tried compiling libc6 ([http://packages.ubuntu.com/dapper/base/libc6](http://packages.ubuntu.com/dapper/base/libc6)) from scratch, but apt still says it's not installed ??? 

apt-get check, unfortunately it's in dutch...:

Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
U kunt 'apt-get -f install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
  axigen: Vereisten: libc6 (>= 2.3.2) maar het is niet geinstalleerd
          Vereisten: libstdc++6 (>= 4.0) maar het is niet geinstalleerd
          Vereisten: libgcc1 (>= 4.0) maar het is niet geinstalleerd
          Vereisten: adduser (>= 3.47) maar het is niet geinstalleerd
          Vereisten: bash (>= 2.05b) maar het is niet geinstalleerd
          Vereisten: coreutils maar het is niet geinstalleerd
          Vereisten: sysv-rc maar het is niet geinstalleerd of
                     file-rc maar het is niet geinstalleerd
          Vereisten: passwd maar het is niet geinstalleerd
  belocs-locales-bin: Vereisten: libc6 (>= 2.3.4-1) maar het is niet geinstalleerd
  dpkg-dev: Vereisten: dpkg (>= 1.13.1) maar het is niet geinstalleerd
            Vereisten: perl5
            Vereisten: perl-modules maar het is niet geinstalleerd
            Vereisten: cpio (>= 2.4.2-2) maar het is niet geinstalleerd
            Vereisten: patch (>= 2.2-1) maar het is niet geinstalleerd
            Vereisten: make maar het is niet geinstalleerd
            Vereisten: binutils maar het is niet geinstalleerd
  libc6-dev: Vereisten: libc6 (= 2.3.6-0ubuntu20.5) maar het is niet geinstalleerd
             Vereisten: linux-kernel-headers (>= 2.6.11.2-0) maar het is niet geinstalleerd
E: Er zijn vereisten waaraan niet voldaan is. Probeer -f te gebruiken.


I've tried some more things, all to no avail... I hope you guys can help me out here. I really don't feel like reinstalling my server :/ I'm running Ubuntu 6.06lts

---

### Post by Ravenamp on 2008-08-21
*bump* 

Really in trouble here guys, anyone who can help me out here? :(

---

