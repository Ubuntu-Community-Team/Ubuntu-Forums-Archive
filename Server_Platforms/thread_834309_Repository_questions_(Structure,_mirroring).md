---
title: "Repository questions (Structure, mirroring)"
date: 2008-06-19
forum: Server Platforms
---

### Post by Luke has no name on 2008-06-19
I'm looking to mirror part of what is the official repo (I only want 64-bit and the network install).

1)While apt-mirror is handy, but it didn't work the way I wanted it to. I want to know of any other methods of downloading the directories necessary. <-- Important

2)I want to understand the logic behind the directory hierarchy on the repos, as I currently do not. Are there any manuals or explanations?

---

### Post by koenn on 2008-06-19
1) you could look into apt-cacher, apt-cacher-ng, apt-proxy, apt-move, debmirror or the Setting up a Debian archive mirror howto  : [http://www.debian.org/mirror/ftpmirror](http://www.debian.org/mirror/ftpmirror)

2) the directory tree of a mirror is quite simple :
in the root of the repo (ubuntu/) you have two directories : dists and pool
dists contains a Realease file and a Packages file, organized in subdirectories per release, component, architecture, ...
eg

.../ubuntu/dists/hardy/main/binary-i386:
Packages.bz2
Packages.gz
Release

the pool directory contains the actual .deb files, organized alpahabetically in subdirectories, eg 

.../pool/main/a/anacron/             
anacron_2.3-11ubuntu2_i386.deb	
anacron_2.3-13ubuntu2_i386.deb

a packet manager would read the Packages files in the relevant release subdirectory of dists/, where it finds out what is the corresponding .deb file for that package in the given release. The Packages file also lists the dependencies of each package, so they can be retrieved the same way.


More:
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html)

---

