---
title: "Updating natty to latest LTS"
date: 2016-07-28
forum: Server Platforms
---

### Post by gorbachov on 2016-07-28
Hello Guys,

I am helping a friend with administration of servers. Servers are long time setup and it seems they are left on the state they were installed.
Setup is one powerful server and many Virtuals on top of it.

Physical server is running Natty. I have managed to update it to latest natty packages with the old- prefix. But I see no way to update it to Xenial.

Is this possible at all. Or I have to live with this.

I have managed to update all virtual to Xenial but they were fresher versions of Ubuntu.

Regards,
Yasen

---

### Post by howefield on 2016-07-28
Thread moved to the "*Server Platforms*" forum.

---

### Post by gorbachov on 2016-07-28
Here is the output. I see it does not manage to fetch since those are already in archive.

> Checking for a new ubuntu releaseYour Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)


Get:1 Upgrade tool signature [198 B]
Get:2 Upgrade tool [1471 kB]
Fetched 1471 kB in 0s (0 B/s)
authenticate 'oneiric.tar.gz' against 'oneiric.tar.gz.gpg'
extracting 'oneiric.tar.gz'
[screen is terminating]
root@bibliata:~# do-release-upgrade
Checking for a new ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)


Get:1 Upgrade tool signature [198 B]
Get:2 Upgrade tool [1471 kB]
Fetched 1471 kB in 0s (0 B/s)
authenticate 'oneiric.tar.gz' against 'oneiric.tar.gz.gpg'
extracting 'oneiric.tar.gz'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages
  404  Not Found [IP: 91.189.88.152 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages
  404  Not Found [IP: 91.189.88.152 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Fetched 0 B in 0s (0 B/s)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Fetched 0 B in 0s (0 B/s)


Error during update


A problem occurred during the update. This is usually some sort of
network problem, please check your network connection and retry.


W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages)
404 Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)
404 Not Found [IP: 91.189.88.149 80]
, E:Some index files failed to download. They have been ignored, or
old ones used instead.




Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
=== Command detached from window (Thu Jul 28 11:47:19 2016) ===
=== Command terminated with exit status 1 (Thu Jul 28 11:47:19 2016) ===




---

### Post by gorbachov on 2016-07-28
Right after I posted this I figured it out.

During the do-release-upgrade, source list is changed. And I have to go and change it back to old-releases.

---

### Post by Irihapeti on 2016-07-28
In theory, you can upgrade from natty to oneiric to precise, and then to trusty and finally to xenial.

But in practice, things often go wrong. Make sure you have a good backup first and that you know you can recover from it (the backup).

Personally, I find it easier just to do a clean install.

---

### Post by mastablasta on 2016-07-28
> **Irihapeti said:**
> 
Personally, I find it easier just to do a clean install.

who knows what is easier in this case: > 
Setup is one powerful server and many Virtuals on top of it.

also at least setup some auto security updates or at leats notification that it needs an update with the changelog attached. the mentioned server looks like a serious thing and i can only wonder why it has no maintenance (planned scheduled upgrades with testing and such, updates...).

---

