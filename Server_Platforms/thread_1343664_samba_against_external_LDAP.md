---
title: "samba against external LDAP"
date: 2009-12-02
forum: Server Platforms
---

### Post by superFerra on 2009-12-02
Hello,
i'd like to know how to setup Samba server to authenticate users against EXTERNAL ldap server. "EXTERNAL" means that it is on another machine (UNIX). 
Do i need to install slapd daemon on samba machine?
Or samba is enough? (using ldapsam as backend)
Thanks

---

### Post by Bag-O-Stuff on 2009-12-02
You do not need to install or run the daemon to do this.  Depending on how you intend to use the server, you might need libnss-ldap (for user/group ownership of local files) and smbldap-tools (to give samba the ability to add/modify/delete user accounts in the ldap directory).

---

