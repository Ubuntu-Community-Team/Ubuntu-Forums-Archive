---
title: "KDE Neon - I cannot access my desktop."
date: 2018-10-11
forum: Ubuntu/Debian BASED
---

### Post by ibrahim. on 2018-10-11
Hi. I'm using KDE Neon 5.14 (it's based Ubuntu). I have downloaded new version of LibreOffice. So I have wanted to delete old version of LibreOffice from my os. I have used this for this job:
```
sudo apt-get purge libre*
```
After this job I think required things of KDE Neon have deleted. So I cannot access my desktop and apt-get has deleted:
```
root@neon:/# apt update
apt: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory
```
I have used CD Live and I have run these commands and installed apt-get:
```
wget security.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_1.0.1ubuntu2.17_amd64.deb
dpkg -i libapt-pkg4.12_1.0.1ubuntu2.17_amd64.deb
```
After this job I could run apt-get (I mean that apt-get installed):
```

apt-get update
apt-get upgrade
apt-get -f install

```
I have restarted my pc and now I see a black screen and waiting. How can I solve this problem? Thanks.

---

### Post by QIII on 2018-10-11
Moved to Ubuntu/Debian BASED.

---

