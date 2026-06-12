---
title: "Samba sharing on Systems logged in through LDAP"
date: 2010-01-05
forum: Server Platforms
---

### Post by dinkoarun on 2010-01-05
I have a Ubuntu 8.04 server that is setup as a PDC using openldap. All users are able to login to the PDC server using SAMBA with their LDAP username and Password.

The users also able connect to the local systems running on Ubuntu 9.04 with their ldap username name and password. I set this up by following this guide [[COLOR="Blue"]**https://help.ubuntu.com/community/LDAPClientAuthentication**[/COLOR]]("https://help.ubuntu.com/community/LDAPClientAuthentication"). I have made the necessary changes to /etc/nsswitch.conf, /etc/pam.d/commom-session, /etc/pam.d/common-auth, /etc/pam.d/common-passwd.

Now, the users want to share their local files via samba with other users. But when this happens, the other users are not able to login to the samba share. I have checked the folder permissions and they have read and right access. I am not sure if I have to make any changes to the /etc/samba/smb.conf file to support ldap authentication.

---

