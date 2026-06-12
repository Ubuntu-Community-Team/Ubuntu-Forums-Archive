---
title: "Samba broken after apt-get upgrade - missing library libwbclient.so.0"
date: 2013-09-13
forum: Server Platforms
---

### Post by funkymike on 2013-09-13
An ubuntu server 12.04 LTS has an issue where samba was working fine up until an apt-get update and apt-get upgrade

Now i can't run anything samba related, it complains that libwbclient.so.0 is missing. 

i.e. 

smbpasswd: error while loading shared libraries: libwbclient.so.0: cannot open shared object file: No such file or directory



I cannot seem to locate that file anywhere, can anyone assist with how to fix this?

I have tried backing up my samba configuration file, then doing an  apt-get remove --purge samba, installing it again which didn't help  either. 

thank you.

---

### Post by funkymike on 2013-09-13
i was able to fix it. 

i had to do a apt-get remove --purge libwbclient.0 uninstall samba then reinstall samba and it reinstalled it.

---

