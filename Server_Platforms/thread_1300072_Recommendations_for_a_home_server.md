---
title: "Recommendations for a home server"
date: 2009-10-24
forum: Server Platforms
---

### Post by wlraider70 on 2009-10-24
So i have a spare computer and I just moved so im thinking about turnming it into a server.

I would like to know what kind of Recommendations for a home server you would have. Also PLEASE give me the program name.

I think I'll backup some files, 
fun an FTP to get files from work
I'd like to do an active directory type. give my local boxes an internal ip.
 

Thats all off the top of my head...

---

### Post by dvlchd3 on 2009-10-24
Active Directory - Use LDAP (Open LDAP)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Network File Storage:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

FTP and SSH servers are installed by default on all Ubuntu Server distros.  For configuration, refer to the official server documentation:
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

HIVE - Digital Life Management System:
[https://help.ubuntu.com/community/Hive](https://help.ubuntu.com/community/Hive)

Many other guides for servers:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

