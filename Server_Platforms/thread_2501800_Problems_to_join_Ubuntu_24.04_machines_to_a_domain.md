---
title: "Problems to join Ubuntu 24.04 machines to a domain Windows Server 2025"
date: 2024-10-21
forum: Server Platforms
---

### Post by lutti1972 on 2024-10-21
Problems to join Ubuntu 24.04 machines to a domain
Is not posible to join Ubuntu machines to a domain based on Windows Server 2025 (using realm at least) this is the error:


 


! Couldn't set password for computer account: XXXX$: Message stream modified
adcli: joining domain xxxx.de failed: Couldn't set password for computer account: XXXX$: Message stream modified
! Failed to join the domain
realm: Couldn't join realm: Failed to join the domain


 


Domain is discoverable vía realm:


realm discover xxx.de
xxx.de
  type: kerberos
  realm-name: xxx.DE
  domain-name: xxx.de
  configured: no
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin 


Tested on WS2025 build 10.0.26100.2033 and Linux Ubuntu 24.04 LTS.


 


Those 2 versions of Linux joined to another doman based Windows Server 2022 without issues.

apt policy sssd-ad sssd-tools realmd adcli
sssd-ad:
  Installed: 2.9.4-1.1ubuntu6.1
  Candidate: 2.9.4-1.1ubuntu6.1
  Version table:
 *** 2.9.4-1.1ubuntu6.1 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.9.4-1.1ubuntu6 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) noble/main amd64 Packages
sssd-tools:
  Installed: 2.9.4-1.1ubuntu6.1
  Candidate: 2.9.4-1.1ubuntu6.1
  Version table:
 *** 2.9.4-1.1ubuntu6.1 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.9.4-1.1ubuntu6 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) noble/main amd64 Packages
realmd:
  Installed: 0.17.1-3build2
  Candidate: 0.17.1-3build2
  Version table:
 *** 0.17.1-3build2 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) noble/main amd64 Packages
        100 /var/lib/dpkg/status
adcli:
  Installed: 0.9.2-1ubuntu2
  Candidate: 0.9.2-1ubuntu2
  Version table:
 *** 0.9.2-1ubuntu2 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) noble/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by stephan4 on 2024-11-09
What do your configs look like?
Have you tried it with classic samba + winbind ?
Is your 2025 ADDC perhaps restricted --> Windows Firewall, what does the EventLog say when the joining attempt happens?

---

