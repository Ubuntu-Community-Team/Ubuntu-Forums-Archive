---
title: "Problem with update package"
date: 2021-01-04
forum: Security
---

### Post by aarcos on 2021-01-04
```
sudo apt-get update && sudo apt list --upgradable && sudo apt-get dist-upgrade && sudo apt-get autoclean && sudo apt-get autoremove 
[sudo] contraseña para melange: 
Obj:1 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal InRelease                 
Des:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [109 kB]
Des:3 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Des:4 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]
Des:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [24,3 kB]
Des:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [56,5 kB]
Ign:7 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata
Ign:8 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata
Ign:9 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata
Des:7 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [263 kB]
Err:7 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata
  El archivo tiene un tamaño inesperado (263220 != 263408). ¿La sincronización de la réplica está en progreso? [IP: 200.236.31.4 80]
  Hashes of expected file:
   - Filesize:263408 [weak]
   - SHA256:38584f81d95481f4ba4f48e8f87523fecca7a8e3bc25c51a155681713d07dd2e
   - SHA1:e437ffdc7f30d6df2c2b4bbba0a8ac1d79c06d8b [weak]
   - MD5Sum:d9f7aaa11e5ea662705961fc07d04fcb [weak]
  Release file created at: Mon, 04 Jan 2021 12:05:20 +0000
Des:8 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [205 kB]
Err:8 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata                                                                                                         
  
Des:9 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2.468 B]
```

---

### Post by CelticWarrior on 2021-01-04
Welcome.

Please try again later (a few hours) or change server.

---

