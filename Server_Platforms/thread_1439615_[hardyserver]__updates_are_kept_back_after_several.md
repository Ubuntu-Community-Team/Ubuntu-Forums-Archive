---
title: "[hardyserver]  updates are kept back after several months"
date: 2010-03-26
forum: Server Platforms
---

### Post by GSMX on 2010-03-26
Hi all,

already several months I get this message on a Hardy (8.04) Server I have:

```
~$sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisc35 libisccfg30 liblwres30 linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

I know sometimes packages are 'kept back' because there is a small dependency problem that is mostly solved after a couple of hours. But now it's already keeping these packages back since a few months! First, I thought it had to do with the external webmin ppa, but today I removed webmin (and the ppa) and tried again, but it had no effect. 

Secondly, I know that running 'sudo apt-get dist-upgrade' can solve the issue, but since this is a production server, I can not take any risk.

What causes this problem? Are there more people experiencing this? How can I solve this as good as possible? I would like this server to survive a couple of years more till the next LTS (the one after Lucid) is released.

---

### Post by inphektion on 2010-03-26
the "upgrade" command is depreciated.  what you are really doing is "safe-upgrade".  if you want to get those packages you would do
```
aptitude update
aptitude full-upgrade

```

then reboot, then you'll be good to go.

---

### Post by GSMX on 2010-03-26
Why would 'upgrade' be deprecated? Synaptic still uses it (on the desktop, that is)... And btw, I don't want to use aptitude, i'd rather stick to apt-get, because I am using apt-get since the OS was installed and changing sides now could lead to even more disastrous errors.

---

### Post by inphektion on 2010-03-26
it won't lead to errors.  use apt-get.  I just use aptitude cause its better.

apt-get used to not be as good with dependencies etc. and the aptitude commands i sent will work just fine but if you need to use apt-get then
```
apt-get upgrade bind9-host dnsutils libbind9-30 libdns35 libisc35 libisccfg30 liblwres30 linux-image-server linux-server

```
will do it.

---

### Post by inphektion on 2010-03-26
and yes "upgrade" isn't depreciated in apt-get.  I was thinking of aptitude where it differentiates between "safe" upgrades and ones that might be more dangerous so you have aptitude safe-upgrade or aptitude full-upgrade.

aptitude safe-upgrade is equiv to apt-get upgrade
aptitude full-upgrade will then upgrade those packages held back cause upgdrading them could potentially be more dangerous.  in apt-get world you need to actually specify them.

---

