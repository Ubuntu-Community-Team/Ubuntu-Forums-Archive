---
title: "Ubuntu 16.04 sudo problems with users in OpenLDAP"
date: 2017-05-26
forum: Server Platforms
---

### Post by jorgerodriguezing on 2017-05-26
Hi all,

I have a problem and, after researching a lot, I cannot find a solution. I have an OpenLDAP server on Ubuntu 16.04.2 with sudoers schema deployed, OU Sudoers set and groups and users configured with sudoUser attributes; now I need to auth users on Ubuntu Desktop 16.04, and it works, but when I try to do sudo it indicates that the user's not in sudoers file.

I have installed and configured libnss-ldapd and libpam-ldapd for using with nscd and nslcd, and set the line "sudoers: ldap files" in nsswitch.conf file.

When installing the older libraries libnss-ldap and libpam-ldap I could set the sudoers_base option, but I can't find a way to indicate it on the new 2 libraries, I think the problem comes there, but not sure.

Users DO authenticate, home dirs are created and can login to Desktop, the problem is when I try to sudo with those users.

Any help would be appreciated.

Thanks

Jorge

---

