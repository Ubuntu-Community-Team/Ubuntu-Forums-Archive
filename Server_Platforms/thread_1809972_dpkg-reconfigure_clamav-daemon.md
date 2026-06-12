---
title: "dpkg-reconfigure clamav-daemon"
date: 2011-07-22
forum: Server Platforms
---

### Post by DeepakAnandani on 2011-07-22
plzz help me with the following error.

root@ubuntucserver:~# sudo dpkg-reconfigure clamav-daemon
/usr/sbin/dpkg-reconfigure: clamav-daemon is broken or not fully installed


:confused:..

---

### Post by DeepakAnandani on 2011-07-25
the problem was solved  by doing some changes in ''source.list''
file... plzz note this problem as solved... i m providing u with the information what changes i have made......

i took a back-up of ''source.list'' file..... and replaced the whole file with the following,.....


First try to set your sources server (from update-manager) to use the main server... and retry...
  if still don't works please
made a backup copy of your actual sources.list file and then
try to put some as my standard /etc/apt/sources.list
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) naverick-updates main restricted universe
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse main universe restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
 

 

 problem is solved....:guitar:

---

