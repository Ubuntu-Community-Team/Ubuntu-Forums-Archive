---
title: "Ubuntu 18.04 trojan warning"
date: 2019-01-08
forum: Security
---

### Post by kevinvdbosch on 2019-01-08
I'm using docker to create images to deploy on my ubuntu server. In one of those images I use the base image of ubuntu:18.04. (I run these locally on a docker-machine by Oracle VirtualBox.) However if I try to install the gdal package with "apt-get update && apt-get install -y --no-install-recommends gdal-bin" I get a trojan warning from AVG on Windows:

Name of thread: ELF:Mirai-ACO [Trj]
URL: [http://archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu60_60.2-3ubuntu3_amd64.deb|data.tar.xz|data.tar|.\usr\lib\x86_64-linux-gnu\libicudata.so.60.2](http://archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu60_60.2-3ubuntu3_amd64.deb|data.tar.xz|data.tar|.\usr\lib\x86_64-linux-gnu\libicudata.so.60.2)
Process: C:\Program Files\Oracle\VirtualBox\VBoxHeadless.exe

I get the same warning when trying to install clamav to check for viruses. Is there really a trojan in this package or is this a false positive by AVG? I've build many images this way but never seen this message before.

---

### Post by Frogs Hair on 2019-01-08
I think that you could ask the false positive question on the AVG [forum]("https://support.avg.com/answers#!/feedtype=RECENT_REPLY&dc=All&criteria=ALLQUESTIONS"). I see a 404 error on the link you posted.

---

