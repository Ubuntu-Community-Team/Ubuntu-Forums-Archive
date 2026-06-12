---
title: "apt-pinning, how do I only upgrade one package"
date: 2008-09-11
forum: Server Platforms
---

### Post by awreneau on 2008-09-11
I thought I had this solved but I'm not sure I do.  I run a mixed system, 6.06 LTS w/ Apache from Feisty.  My /etc/apt/preference file is as follows:

Package: *
Pin: release a=feisty
Pin-Priority: 600

Package: *
Pin: release a=dapper
Pin-Priority: 700



when I run apt-get upgrade, apache2 is never upgraded.  What should my pref file look like and what command should I run to only get apache2 from feisty?

---

