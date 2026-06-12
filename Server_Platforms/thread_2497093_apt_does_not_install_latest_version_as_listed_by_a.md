---
title: "apt does not install latest version as listed by apt-cache policy"
date: 2024-04-23
forum: Server Platforms
---

### Post by asiebenwirth on 2024-04-23
Hi,

I'm trying to install something from a PPA but apt does not want to install that latest version but prefers the version from ESM.
How do I change that behavior?

Thanks,
Axel

axel@lyra:/var/www/html/vhosts$ apt-cache policy phpmyadmin 
phpmyadmin:
  Installed: (none)
  Candidate: 4:4.9.5+dfsg1-2ubuntu0.1~esm1
  Version table:
     4:5.2.1+dfsg-1+focal2 500
        500 [http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu](http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu) focal/main amd64 Packages
        500 [http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu](http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu) focal/main i386 Packages
     4:4.9.5+dfsg1-2ubuntu0.1~esm1 510
        510 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) focal-apps-security/main amd64 Packages
        510 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) focal-apps-security/main i386 Packages
     4:4.9.5+dfsg1-2 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal/universe i386 Packages
        500 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) focal/universe amd64 Packages
        500 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) focal/universe i386 Packages

---

