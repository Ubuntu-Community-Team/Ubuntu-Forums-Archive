---
title: "Self-hosted apt-mirror - Hash Sum mismatch"
date: 2019-09-11
forum: Server Platforms
---

### Post by 5mall5nail5 on 2019-09-11
[COLOR=#1A1A1B][FONT=&quot]I have a large lab that I host an internal mirror for. I am using apt-mirror in order to create the repo. The repo server ran out of disk space on the location I am saving mirror data to. I bumped the disk, re-ran the /usr/bin/apt-mirror cronjob, and it ran for a while and completed. However, from a client I still get "hash sum mismatch" for a package. What's the best way to proceed? Thanks![/FONT][/COLOR]

---

### Post by LHammonds on 2019-09-12
Maybe the "[acquire-by-hash]("https://wiki.debian.org/DebianRepository/Format#Acquire-By-Hash")" setting can help in this situation.

---

