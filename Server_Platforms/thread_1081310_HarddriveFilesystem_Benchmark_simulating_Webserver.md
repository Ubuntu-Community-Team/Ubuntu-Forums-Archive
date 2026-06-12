---
title: "Harddrive/Filesystem Benchmark simulating Webserver Load"
date: 2009-02-26
forum: Server Platforms
---

### Post by mart78 on 2009-02-26
Hello, this does not really fit in here but the server category seemed to match best.
I am looking for a benchmark program to test harddrives/filesystems that will simulate the workload of a Web/Imageserver.
I'm trying to find the best RAID Level and filesystem for my requirements which is delivering Images with an average size of 30kB on a social-networking website. OS is Ubuntu Hardy Server 64.

I know the classic benchmarks like bonnie++ and iozone but I couldn't find one that will test for the load the server will receive in a production environment. I found the iometer benchmark that has a webserver workload but it only works with the main program running on a windows box :/

---

### Post by mart78 on 2009-02-27
Just in case anyone finds this thread looking for something similar, I stumbled across filebench today. This seems to be exactly what I was looking for, a multithreaded filesystem benchmark that comes with several preconfigured workloads for webserver, mailserver, database, etc and also allows the definition of own workloads.

It's originally for OpenSolaris and the newest versions seem to be exclusively in OpenSolaris but the code on their sourceforge page compiles well on Ubuntu. On Hardy it locked up when starting its reader threads but when I tried it on my workstation that is still on Gutsy I was surprised to see it running well ;)

You can find links to the sources, documentation, etc on here: [http://opensolaris.org/os/community/performance/filebench/](http://opensolaris.org/os/community/performance/filebench/)

---

