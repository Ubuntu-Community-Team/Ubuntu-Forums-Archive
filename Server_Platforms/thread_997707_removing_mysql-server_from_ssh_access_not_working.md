---
title: "removing mysql-server from ssh access not working"
date: 2008-11-30
forum: Server Platforms
---

### Post by abhinav90 on 2008-11-30
I am trying to remove mysql-server on my remotely accessed server as i made a mess of it root username and want to reinstall it.

when i type sudo apt-get remove mysql-server-5.0 it says removing 123 MB but the process takes less than a second. Then when i try and install this package again it takes only 1 second when the server has a 2MB connection. The root username privelege problem also still remains. The first time i installed mysql through ssh access it had worked out. Why is it not uninstalling and reinstalling properly this time ?

PLs Help

---

### Post by martien on 2008-11-30
> **abhinav90 said:**
> I am trying to remove mysql-server on my remotely accessed server as i made a mess of it root username and want to reinstall it.

when i type sudo apt-get remove mysql-server-5.0 it says removing 123 MB but the process takes less than a second. Then when i try and install this package again it takes only 1 second when the server has a 2MB connection. The root username privelege problem also still remains. The first time i installed mysql through ssh access it had worked out. Why is it not uninstalling and reinstalling properly this time ?

PLs Help
first see all the packages that comes with mysql and remove which you want:
> dpkg --list | grep mysql
then try purge:
> apt-get purge mysql-server-5.0

---

### Post by aos101 on 2008-11-30
The package installs quickly the second time probably because apt caches the .deb packages which you've already installed (in /var/cache/apt/archives), so when you install it again it doesn't need to fetch the package from the network at all.

---

