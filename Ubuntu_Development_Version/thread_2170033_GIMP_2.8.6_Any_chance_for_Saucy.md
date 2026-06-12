---
title: "GIMP 2.8.6: Any chance for Saucy?"
date: 2013-08-24
forum: Ubuntu Development Version
---

### Post by thotz on 2013-08-24
For all those waiting: I have made some time ago a bug report that GIMP 2.8.6 should be included in saucy.

Please see: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1207734](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1207734)

Just to let you know.  I have looked about several bugs, help would be appreciated. Thank you!

---

### Post by SweetAurora on 2013-08-24
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp && sudo apt-get update && sudo apt-get install gimp gimp-data-extras gimp-plugin-registry
```
There. Latest version of Gimp at your disposal.

---

### Post by VinDSL on 2013-08-24
> **SweetAurora said:**
> ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp && sudo apt-get update && sudo apt-get install gimp gimp-data-extras gimp-plugin-registry
```
There. Latest version of Gimp at your disposal.
Sweet!  Thanks!

For some reason, I couldn't shrink the Toolbox Dialog in 2.8.4 -- had to close it, or push it off-screen, to do any work.

Toolbox works fine, in 2.8.6  :)

---

### Post by thotz on 2013-08-26
> **SweetAurora said:**
> ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp && sudo apt-get update && sudo apt-get install gimp gimp-data-extras gimp-plugin-registry
```
There. Latest version of Gimp at your disposal.

I have meant that it should be available in the official packages in saucy. But maybe we are already too late.

---

### Post by deadflowr on 2013-08-29
It's been upgraded today
```
gimp:  
Installed: 2.8.6-1ubuntu1
Candidate: 2.8.6-1ubuntu1
Version table:*** 2.8.6-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by thotz on 2013-08-29
Yes, I have spoken to Sebastien Bacher (seb128) on IRC :)

---

### Post by VinDSL on 2013-08-31
Loving 2.8.6-1ubuntu1...

Haven't run across any major problems/irritations, so far!

---

