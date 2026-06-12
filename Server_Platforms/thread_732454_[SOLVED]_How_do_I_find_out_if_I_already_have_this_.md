---
title: "[SOLVED] How do I find out if I already have this software installed?"
date: 2008-03-22
forum: Server Platforms
---

### Post by MountainX on 2008-03-22
I am following this guide:
[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

It recommends this

apt-get install samba smbclient smbfs beep ntp ntpdate

I installed samba file sharing services during installation (I think). How can I double check that? I tried apt-cache policy smbfs and it seems to be telling me I have smbfs installed already, as I would expect. But it tells me ntp is not installed and I find that strange because the installer accessed an ntp server during installation.

---

### Post by kevdog on 2008-03-22
I think the ntp client is installed by default but not the ntp server.

---

### Post by brownknight on 2008-03-22
I usually do** aptitude show <package name>**. It will show install status if yes or no and other info that are very useful about the package.

---

### Post by netlogic on 2008-03-23
dpkg -l |grep "nameoftheapp"

---

