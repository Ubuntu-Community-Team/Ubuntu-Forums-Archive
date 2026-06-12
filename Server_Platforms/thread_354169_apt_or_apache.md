---
title: "apt or apache"
date: 2007-02-05
forum: Server Platforms
---

### Post by Kissack on 2007-02-05
New to ubuntu here, and I think I have fouled up, so your help would be appreciated....

I installed apached (apt-get install apache) and several days later realised I should have installed apache2.  I installed apache2 then removed apache (apt-get remove apache).  Apache2 wouldnt start so I thought i'd start again.  I removed apache2 then deleted the apache/apache2 directories in etc and var/log.  Re-installed apache2 (even tried lamp through the package manager) but it still doesnt start.  however i think the reason now is there is no etc/apache2/apache2.conf (in fact only a mods-available sub-dir).

Can I resurrect this without re-installing xubuntu?

hoping so...

-- 
Allan

---

### Post by jtc on 2007-02-05
I think we will be able to save the situation without having to reinstall the entire system :-)

For apt to recreate your config-files etc it needs to know/belive that apache2 is completely removed. If you have an existing package, i.e apache2, you want to remove completly you use apt-get remove, with the purge flag, like this.

```
apt-get --purge remove apache2
```

If the package is already uninstalled the "normal" way you can use dpkg to purge the remaining parts.

```
dpkg --purge apache2
```

When you install apache2 you'll get all config-files, logs, etc back.

---

### Post by Kissack on 2007-02-06
Thanks.  I tried this (and apt-get autoremove apache2) but still no config files :-( 
> 
root@green:/mnt/hdd2/allan/home/admin/old-installed# apt-get --purge remove apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 57 not upgraded.
Need to get 0B of archives.
After unpacking 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102215 files and directories currently installed.)
Removing apache2 ...
root@green:/mnt/hdd2/allan/home/admin/old-installed# dpkg --purge apache2
dpkg - warning: ignoring request to remove apache2 which isn't installed.
root@green:/mnt/hdd2/allan/home/admin/old-installed# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 57 not upgraded.
Need to get 0B/36.0kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 102220 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu4) ...
root@green:/mnt/hdd2/allan/home/admin/old-installed# ls -l /etc/apache2
ls: /etc/apache2: No such file or directory
root@green:/mnt/hdd2/allan/home/admin/old-installed# 

anything else i can try?
-- 
Allan

---

### Post by Brazen on 2007-02-07
maybe try ```
sudo dpkg-reconfigure apache2
```

---

### Post by Kissack on 2007-02-08
> sudo dpkg-reconfigure apache2

Had already tried this.  Sadly my apache is still non-operational.  Can anyone help?

---

### Post by Kissack on 2007-02-08
jtc, thanks....
I experimeted and ran
> apt-get --purge remove apache2-common
then re-installed and am up and running again :-)

---

