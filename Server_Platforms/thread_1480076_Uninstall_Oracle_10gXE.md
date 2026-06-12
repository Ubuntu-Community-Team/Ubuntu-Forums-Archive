---
title: "Uninstall Oracle 10gXE???"
date: 2010-05-11
forum: Server Platforms
---

### Post by mslovette on 2010-05-11
Has anyone ever uninstalled 10gXE from ubuntu server? I ask because I (apparently) didnt do my homework prior to installing the suite.
 
I wanted to relocate the data files to a RAID for expansion purposes. 
I wanted to generate a separate set of RDBMS files for other applications (on the RAID).
 
I discovered that, while fully functional, the RDBMS apparently is in a fixed location and database growth limited by a 4GB storage cap (I'll burn 4GB+ with JUST my family photos)
 
Any guidance will be greatly appreciated.
 
/vr, mslovette

---

### Post by Waappu on 2010-05-11
Hi,

How you did install database ?
If from repository do just
```
sudo apt-get remove --purge oracle-xe
```

BTW, you can move data files after wards

---

### Post by mslovette on 2010-05-12
Thanks... Did install using aptitude.  Will use your suggestion.
 
/vr, mslovette

---

