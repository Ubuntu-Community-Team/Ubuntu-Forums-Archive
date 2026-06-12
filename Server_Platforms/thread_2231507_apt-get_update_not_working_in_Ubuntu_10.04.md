---
title: "apt-get update not working in Ubuntu 10.04"
date: 2014-06-26
forum: Server Platforms
---

### Post by neha2 on 2014-06-26
My ubuntu version is 10.04. the apt-get update is not working. I have set the proxy in the "/etc/apt/apt.conf.d/01ubuntu" file. Also appended the DNS server of Google (8.8.8.8 and 8.8.4.4) in the /etc/resolv.conf. On apt-get update I a still getting the following error:
```

Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (111: Connection refused) [IP: 91.189.92.150 80]
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (111: Connection refused)
Err [http://ppa.launchpad.net/ferramroberto/java/ubuntu/](http://ppa.launchpad.net/ferramroberto/java/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to ppa.launchpad.net:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric Release.gpg 
  Could not connect to 10.5.19.30:80 (10.5.19.30). - connect (110: Connection timed out)
Err [http://10.5.19.30/extras/](http://10.5.19.30/extras/) oneiric/main Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric Release.gpg 
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/partner/](http://10.5.19.30/partner/) oneiric/partner Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/partner/](http://10.5.19.30/partner/) oneiric-security/partner Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/partner/](http://10.5.19.30/partner/) oneiric-backports/partner Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/partner/](http://10.5.19.30/partner/) oneiric-updates/partner Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric/restricted Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric/main Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric/multiverse Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric/universe Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-backports/restricted Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-backports/main Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-backports/multiverse Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-backports/universe Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-security/restricted Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-security/main Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-security/multiverse Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-security/universe Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates Release.gpg
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-updates/restricted Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-updates/main Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-updates/multiverse Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30/ubuntu/](http://10.5.19.30/ubuntu/) oneiric-updates/universe Translation-en_IN
  Unable to connect to 10.5.19.30:http:
Ign [http://10.5.19.30](http://10.5.19.30) oneiric Release     
Ign [http://10.5.19.30](http://10.5.19.30) oneiric Release     
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates Release
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/partner Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-backports/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-security/universe Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/restricted Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/main Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/multiverse Packages
Ign [http://10.5.19.30](http://10.5.19.30) oneiric-updates/universe Packages
Err [http://10.5.19.30](http://10.5.19.30) oneiric/main Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric/partner Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security/partner Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports/partner Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates/partner Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric/restricted Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric/main Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric/multiverse Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric/universe Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports/restricted Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports/main Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports/multiverse Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-backports/universe Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security/restricted Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security/main Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security/multiverse Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-security/universe Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates/restricted Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates/main Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates/multiverse Packages
  Unable to connect to 10.5.19.30:http:
Err [http://10.5.19.30](http://10.5.19.30) oneiric-updates/universe Packages
  Unable to connect to 10.5.19.30:http:
Reading package lists... Done              
W: Failed to fetch [http://10.5.19.30/extras/dists/oneiric/Release.gpg](http://10.5.19.30/extras/dists/oneiric/Release.gpg)  Could not connect to 10.5.19.30:80 (10.5.19.30). - connect (110: Connection timed out)

W: Failed to fetch [http://10.5.19.30/extras/dists/oneiric/main/i18n/Translation-en_IN.bz2](http://10.5.19.30/extras/dists/oneiric/main/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric/Release.gpg](http://10.5.19.30/partner/dists/oneiric/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric/partner/i18n/Translation-en_IN.bz2](http://10.5.19.30/partner/dists/oneiric/partner/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-security/Release.gpg](http://10.5.19.30/partner/dists/oneiric-security/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-security/partner/i18n/Translation-en_IN.bz2](http://10.5.19.30/partner/dists/oneiric-security/partner/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-backports/Release.gpg](http://10.5.19.30/partner/dists/oneiric-backports/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-backports/partner/i18n/Translation-en_IN.bz2](http://10.5.19.30/partner/dists/oneiric-backports/partner/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-updates/Release.gpg](http://10.5.19.30/partner/dists/oneiric-updates/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-updates/partner/i18n/Translation-en_IN.bz2](http://10.5.19.30/partner/dists/oneiric-updates/partner/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/Release.gpg](http://10.5.19.30/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/restricted/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/main/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric/main/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/universe/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/Release.gpg](http://10.5.19.30/ubuntu/dists/oneiric-backports/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/Release.gpg](http://10.5.19.30/ubuntu/dists/oneiric-security/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/main/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/Release.gpg](http://10.5.19.30/ubuntu/dists/oneiric-updates/Release.gpg)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_IN.bz2](http://10.5.19.30/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (111: Connection refused) [IP: 91.189.92.150 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://10.5.19.30/extras/dists/oneiric/main/binary-amd64/Packages.gz](http://10.5.19.30/extras/dists/oneiric/main/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric/partner/binary-amd64/Packages.gz](http://10.5.19.30/partner/dists/oneiric/partner/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-security/partner/binary-amd64/Packages.gz](http://10.5.19.30/partner/dists/oneiric-security/partner/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-backports/partner/binary-amd64/Packages.gz](http://10.5.19.30/partner/dists/oneiric-backports/partner/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/partner/dists/oneiric-updates/partner/binary-amd64/Packages.gz](http://10.5.19.30/partner/dists/oneiric-updates/partner/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/restricted/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric/restricted/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/main/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric/main/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric/universe/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric/universe/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/restricted/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-security/restricted/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/main/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-security/main/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/multiverse/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-security/multiverse/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-security/universe/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-security/universe/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Failed to fetch [http://10.5.19.30/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages.gz](http://10.5.19.30/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages.gz)  Unable to connect to 10.5.19.30:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```





Can anybody please help me figure out where am I going wrong? Thanks a lot.

---

### Post by SeijiSensei on 2014-06-26
Is this the Server version of Ubuntu, or the regular desktop version?  If the latter, 10.04 has reached its [end-of-life]("https://wiki.ubuntu.com/Releases") and is no longer supported with updates. Neither is Onieric.

Can you connect to regular web sites with a browser on this machine? Why do you need a proxy?

---

### Post by varunendra on 2014-06-26
Welcome to the forums Neha!

The first and biggest problem is that you are using version 10.04, whose desktop version has reached its End Of Life ([EOL]("https://wiki.ubuntu.com/Releases")) and the server version will also meet the same destiny in April next year.

Once a release reaches its EOL, it gets no more updates and after a short while, its repositories are moved to a different URL too ('old-releases.ubuntu.com' instead of 'archive.ubuntu.com').

I am not sure about the proxy address, but pretty sure the solution for you is to simply upgrade to a currently supported version, preferably doing a clean install.

**EDIT:** SeijiSensei  beat me to it. :|

---

### Post by houstonbofh on 2014-06-29
This could be a transient problem with that repository.  Are you on server or desktop?  Changing repositories to a regional mirror will fix it, but the methods are different.

[http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main](http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main)

[http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line)

---

### Post by kc1di on 2014-06-29
Hi neha2 and welcome to Linux,

Is this a Desktop machine or Server?  I ask because the 10.04 Desktop Reached end of life in May of 2013.  So it is no longer supported.  server version is supported until next year.  If it's a desktop you can no longer upgrade that version.  So apt will not find any repositories. 

You would be better off updating your version to say 12.04 Supported until April 2017 or to 14.04 which will be supported until 2019.

---

### Post by houstonbofh on 2014-07-05
Out of the 4 responses, 3 were just telling him that he was running an older version of Ubuntu...  I think he knows.

---

### Post by lisati on 2014-07-05
> **houstonbofh said:**
> Out of the 4 responses, 3 were just telling him that he was running an older version of Ubuntu...  I think he knows.

Exactly. Please see [this sticky]("http://ubuntuforums.org/showthread.php?t=2229730").

---

