---
title: "OpenLDAP User not add to database"
date: 2012-04-06
forum: Server Platforms
---

### Post by jitenderana on 2012-04-06
Hi All,
This is my first thread hear, i am in trouble i was configure OpenLDAP + Samba as a PDC to follow this link
[http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)
but when i try to add user in data base its given a error message and not able to add user on it. 
root@ldapmstr:~# smbldap-useradd -a -m test
Error looking for next uid in sambaDomainName=example.local,example,dc=example,dc=local:invalid DN at /usr/share/perl5/smbldap_tools.pm line 1174.
 
Please suggest me where i am wrong.
 
Thanks

---

