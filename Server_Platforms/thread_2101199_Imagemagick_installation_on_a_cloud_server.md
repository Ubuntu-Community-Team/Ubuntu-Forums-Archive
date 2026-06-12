---
title: "Imagemagick installation on a cloud server"
date: 2013-01-04
forum: Server Platforms
---

### Post by ELMIT on 2013-01-04
I need to install Imagemagick on a cloud server:

apt-get install imagemagickReading package lists... Done
Building dependency tree       
Reading state information... Done
Package imagemagick is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'imagemagick' has no installation candidate


lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise


What repository do I need to add?

---

### Post by Cheesemill on 2013-01-04
It's in the default repositories. Have you run...
```
sudo apt-get update
```
first?

[http://packages.ubuntu.com/precise/imagemagick](http://packages.ubuntu.com/precise/imagemagick)

---

