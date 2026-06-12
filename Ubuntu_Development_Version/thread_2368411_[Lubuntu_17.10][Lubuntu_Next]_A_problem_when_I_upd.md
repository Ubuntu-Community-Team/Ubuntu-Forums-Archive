---
title: "[Lubuntu 17.10][Lubuntu Next] A problem when I update repositories"
date: 2017-08-10
forum: Ubuntu Development Version
---

### Post by learnspeakthink on 2017-08-10
I nearly always update repositories every day ,using terminal or Synaptic like many people .Like this :

sudo apt-get update && sudo apt-get upgrade   #When I type this I watched I had 32 packages to be update and I know that easily be done with Synaptic .

Finally I recharged the list of repositories and I saw :

```
Fallo al obtener [http://pe.archive.ubuntu.com/ubuntu/dists/artful/main/dep11/Components-amd64.yml.xz](http://pe.archive.ubuntu.com/ubuntu/dists/artful/main/dep11/Components-amd64.yml.xz)  La suma hash difiere
Hashes of expected file:
 - Filesize:459676 [weak]
 - SHA256:835ef063070bb54b9c7da83b84084b52d8bf3737a3e0e35e1cb8ea9262ed1b5a
 - SHA1:dd4766720fcd8c179e38d2e99a005243624b743b [weak]
 - MD5Sum:b7efa5f7dc49ec7d63fc3bc69db664db [weak]
Hashes of received file:
 - SHA256:43411ffc3f31904d9996ea8d5562da7e258f560b69de30dc1d8607d2ff52ea51
 - SHA1:d25eadf652ed106eba70a8fc8f28a2f80f47d161 [weak]
 - MD5Sum:6e0967baba3a7135a6f732b1e78f5449 [weak]
 - Filesize:459508 [weak]
Last modification reported: Thu, 10 Aug 2017 10:00:39 +0000
Release file created at: Thu, 10 Aug 2017 14:59:52 +0000
Fallo al obtener [http://pe.archive.ubuntu.com/ubuntu/dists/artful/main/dep11/icons-64x64.tar.gz](http://pe.archive.ubuntu.com/ubuntu/dists/artful/main/dep11/icons-64x64.tar.gz)  404  Not FoundFallo al obtener [http://pe.archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/Components-amd64.yml.xz](http://pe.archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/Components-amd64.yml.xz)  Fallo al obtener [http://pe.archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/icons-64x64.tar.gz](http://pe.archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/icons-64x64.tar.gz)  Fallo al obtener [http://pe.archive.ubuntu.com/ubuntu/dists/artful/multiverse/dep11/Components-amd64.yml.xz](http://pe.archive.ubuntu.com/ubuntu/dists/artful/multiverse/dep11/Components-amd64.yml.xz)  Fallo al obtener [http://pe.archive.ubuntu.com/ubuntu/dists/artful/multiverse/dep11/icons-64x64.tar.gz](http://pe.archive.ubuntu.com/ubuntu/dists/artful/multiverse/dep11/icons-64x64.tar.gz)  404  Not FoundNo se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.
```

Maybe It's not the biggest problem for Lubuntu Next (a development version) or Ubuntu 17.10 but I think that should be known .

---

### Post by QIII on 2017-08-10
Hello!

Please surround all commands and their results with code tags.

1.  Click the # button above the text entry box, place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after it. The square brackets are required.

---

### Post by oldos2er on 2017-08-10
Thread moved to Ubuntu Development Version.

---

