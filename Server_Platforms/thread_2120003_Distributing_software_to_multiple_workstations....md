---
title: "Distributing software to multiple workstations..."
date: 2013-02-25
forum: Server Platforms
---

### Post by ragtag on 2013-02-25
I've been looking into a good system for distributing software (both open-source, in-house and propriatery) to multple workstations. Previously we've been using an NFS server to make the software available to the clients, but I want to move to having it locally on each workstation.

We have cfengine2 set up, and I'm in the process of moving to cfengine3. While cfengine2 can be used to synchronize a folder to all the workstations, it's quite slow when those folders get big (several 100 mb) and you have 40+ workstations contacting it, which in turns seems to crash the cfengine service on the server (I haven't verified that this is the case).

For now Murder, that Twitter uses to distribute their software, seems like a good alternative. It basically uses bit torrent to distribute the software, thus distributing the load across all machines. Murder can be used with cfengine3, so that cfengine3 tells it when to fetch an updated torrent and start downloading.

Some form of multicast rsync could also be an option.

An alternative would be to create .deb packages for all the software we need and set up our own little repos server, but this seems like quite a bit of extra work. 

What are people using for this kind of job?

---

### Post by thnewguy on 2013-02-25
With only 40 workstations I would seriously consider putting your software in tar archives on a central server, maybe using FTP or SFTP to distribute. Have each client perform regular checks for new packages and download them and simply untar. Really, it looks like the solutions you are investigating are overkill for a job like this. A single file server and a cronjob will do the work quite nicely.

---

### Post by ragtag on 2013-02-26
You're probably right. :)  I tend to overbuild things a bit, in case the company one days grows in size.

---

