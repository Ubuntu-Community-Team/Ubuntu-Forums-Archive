---
title: "How to delete a repository hosted on a server"
date: 2011-10-19
forum: Server Platforms
---

### Post by kaustubh.karkare on 2011-10-19
Situation: To make things simpler for the students of my college, a local server has been setup that contains repositories from which we can download stuff. I am a admin for this server, and have been given the task for removing the older repos and setting up new ones. However, while I have located and already tested procedures for setting up a new repo, many hours have been spent, but i have been unable literally anything on how to delete an existing repo from a server. It is essential that I do this, as we are repeatedly facing disk space storage problems.

Server Configuration: HP Pavillion Desktop PC, Intel Pentium Dual Core 1.8 GHz Processor, 2.5 GB RAM, 149 GB Hard Disk Drive, Ubuntu 8.10 on 2.6.24-22-generic kernel, with 300GB NAS. Repositories available for Ubuntu 8.10, 10.04, 10.10 and Fedora 13, 14.

Problem: I need to delete the repo for Ubuntu 8.10, 10.04 and Fedora 13 and 14.

My attempts so far: I went through the files /var/spool/apt-mirror/mirror/server-ip/repo/ubuntu/dists/release-name/ folder and found that it only contained an index of the files associated with that repo. However, the actual packages are in the /var/spool/apt-mirror/mirror/server-ip/repo/ubuntu/pool/ folder and aren't organized by release, and manually deleting them or writing a script for the purpose is rather inconvenient. I also considered temporarily downloading the entire maverick repo onto another system using apt-mirror, deleting everything on the server, and the setting up the maverick repo again using the other system as a source. However, this seems too "dirty". I was hoping there would be existing tool to delete repos ... something along the lines of "apt-mirror --remove etc/apt/unmirror.list" that would remove all packages associated with the index files referred to in the unmirror.list file.

---

