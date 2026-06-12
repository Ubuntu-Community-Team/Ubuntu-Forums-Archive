---
title: "What's updating currently?"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by vasa1 on 2012-04-24
I've installed 12.04 (RC) successfully. I run apt-get update and apt-get upgrade often so as to be current. Although several MB are "fetched", mostly there's no software program that's updated as indicated by
```
...                                                             
Fetched 12.5 MB in 4min 59s (41.6 kB/s)                                                                                            
Reading package lists... Done
Working...
No files to download.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-e 
Done! Verify that all packages were installed successfully. If errors are found, run apt-get clean as root and try again using apt-get directly.

```
So what's being **fetched** in these 12.5 MB (in this case)? Is it just my local databases being refreshed?
(I'm using [apt-fast]("http://ubuntuforums.org/showpost.php?p=5115680&postcount=1").)

---

### Post by robgraves on 2012-04-24
[http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html)

read section "update"

---

### Post by vasa1 on 2012-04-24
> **robgraves said:**
> [http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html)

read section "update"
Thanks, so ...```
update
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.

```
but are these MB size *fetches* a temporary phenomenon (till 12.04 is actually released) because the *fetches* with 11.10 (release version) weren't this large?

---

### Post by lisati on 2012-04-24
It could be that the "update" part is successfully updating its notes, but there are no actual updates available while 12.04 is being made ready for release.

---

### Post by georgelappies on 2012-04-24
Yeah, update only gets the newest package list files from the server (it can be huge, in my case a "sudo apt-get update" will download about 23MB every time).

If there is anything to upgrade after the package lists have been updated you need to run "sudo apt-get upgrade"

---

