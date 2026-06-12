---
title: "No snap in upgraded 14.04 -&gt; 16.04?"
date: 2016-10-20
forum: Server Platforms
---

### Post by pa1jim on 2016-10-20
Upgraded from 14.04 to 16.04 server. Had a few errors due to old  config-files but runs fine now. One strange thing I found: no snaps! 

$snap info gives:
-bash: snap: command not found

~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

~$ uname -r
4.4.0-45-generic


What do I have to do to get snap-support?

Grtz, Jim

---

### Post by howefield on 2016-10-20
```
snap help
```

will give you the available options.

---

### Post by pa1jim on 2016-10-20
~$ snap help
-bash: snap: command not found

---

### Post by howefield on 2016-10-20
Perhaps snapd isn't installed, it is on a clean install but perhaps not on an upgrade.

Do you have an installed version..

```
apt-cache policy snapd
```

if not install with..

```
sudo apt install snapd
```

---

### Post by pa1jim on 2016-10-20
$ apt-cache policy snapd
snapd:
  Installed: (none)
  Candidate: 2.15.2ubuntu1
  Version table:
     2.15.2ubuntu1 500
        500 [http://mirror.transip.net/ubuntu/ubuntu](http://mirror.transip.net/ubuntu/ubuntu) xenial-updates/main amd64 Packages
     2.0.2 500
        500 [http://mirror.transip.net/ubuntu/ubuntu](http://mirror.transip.net/ubuntu/ubuntu) xenial/main amd64 Packages

$sudo apt install snapd gave me errors about a previous broken install of snapd. Apparently it should be installed but got broken during upgrade. The force option wasn't working so deleting all snap* entries in /var/lib/dpkg/info and /var/cache/apt/archives and rerun install snapd worked:

$ apt-cache policy snapd
snapd:
  Installed: 2.15.2ubuntu1
  Candidate: 2.15.2ubuntu1
  Version table:
 *** 2.15.2ubuntu1 500
        500 [http://mirror.transip.net/ubuntu/ubuntu](http://mirror.transip.net/ubuntu/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.0.2 500
        500 [http://mirror.transip.net/ubuntu/ubuntu](http://mirror.transip.net/ubuntu/ubuntu) xenial/main amd64 Packages 

Thank you VERY much for the quick response!

---

### Post by howefield on 2016-10-20
Cool, well done on sussing it out.

---

