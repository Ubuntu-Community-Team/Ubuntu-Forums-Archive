---
title: "How does update-manager check for updates without root permissions?"
date: 2011-06-03
forum: The Cafe
---

### Post by RJ12 on 2011-06-03
I just realized that Update-manager is able to check for updates without being run as root (although it can't install them, which is expected), isn't this the same as running apt-get update? How come I can't run apt-get update without using sudo (or root) then?

---

### Post by Old_Grey_Wolf on 2011-06-03
> **RJ12 said:**
> I just realized that Update-manager is able to check for updates without being run as root (although it can't install them, which is expected), isn't this the same as running apt-get update? How come I can't run apt-get update without using sudo (or root) then?

I am trying to explain the concept without getting into the details. Update Manager and apt-get do not functions the same way. When you use Update Manager to check for updates it does not add the packages to a file of packages to downloaded. apt-get update actually adds the packages to a file to be downloaded; therefore, the need for sudo. When you select install packages in Update Manager it will add the packages to the file of packages to be downloaded; however, it will ask for the password at that time.

Also, Update Manager will install packages not installed by sudo apt-get upgrade. The Update Manager does something similar to sudo apt-get dist-upgrade.

---

### Post by el_koraco on 2011-06-03
Update Manager and USC do not use apt directly, they use a fork of PackageKit called aptdaemon. 

[http://lists.debian.org/deity/2009/02/msg00000.html]("http://lists.debian.org/deity/2009/02/msg00000.html")

Aptdaemon already provides the following features:

...
* PolicyKit authorization allowing e.g. desktop user to update the cache
  (check for updates) passwordlessly

...
* Install packages from repositories or local file system, remove 
  packages, update the cache and (safe) upgrade your system

---

### Post by RJ12 on 2011-06-03
Wow! I should have known... thanks for answering the question guys (and providing an awesome explanation!), I couldn't get it off my mind until now :)

---

