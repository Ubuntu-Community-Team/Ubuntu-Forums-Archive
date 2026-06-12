---
title: "gnome-control-center error in the build"
date: 2006-07-02
forum: Sun Sparc Users
---

### Post by recupero on 2006-07-02
Hi!
after updating the sources, I am stuck with this error:
[B]dpkg: parse error, in file `/var/lib/dpkg/status' near line 10221 package `gnome-control-center':
 `Depends' field, syntax error after reference to package `l'[/B]
I cannot remove that package or the whole GNOME either.

logfile:
neo@verdon:~/Desktop$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  rssh
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
103 not fully installed or removed.
Need to get 0B/209kB of archives.
After unpacking 553kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 10221 package `gnome-control-center':
 `Depends' field, syntax error after reference to package `l'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by netztier on 2006-07-02
I've seen this kind of error dozens of times during my Ubuntu/SPARC experiments; it's a glitch in the /var/lib/dpkg/status file.

You can open and edit it (with sudo) and correct the error at the line indicated in the error message.

Sometimes erasing the whole package paragraph for the package in question helps.

You will  then have to make synaptic correct all dependency problems first, or force a reinstallation of the "damaged" package.

It hasn't been happening lately, but while dapper still was beta, I've been seeing these twice a week :-/

kind regards

Marc

---

### Post by Cynical on 2006-08-30
its late but

```

sudo dselect update

```

---

