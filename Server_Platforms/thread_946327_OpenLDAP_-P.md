---
title: "OpenLDAP :-P"
date: 2008-10-13
forum: Server Platforms
---

### Post by ronni on 2008-10-13
I want to centralize login using OpenLDAP, Heimdal Kerberos, FreeRadius and SSH, so I can log in on switches, servers etc. using one user and one password.

So far I have installed OpenLDAP by following this guide:
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
I skipped LDAP replication.

Then I followed this guide:
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
But because I have Ubuntu 8.04 its not 100% the same.
What I've done:
- Installed: apt-get install libpam-ldap libnss-ldap nss-updatedb libnss-db
- Configured doing the installation
- Configured the /etc/nsswitch.conf

When I make a:
getent passwd
It looks like the content of the passwd file (and it is), but the information is not retreived from LDAP. The custom user I have added in LDAP is not in the list.
The file /etc/libnss-ldap.conf is not to be found anywhere, in stead I have /etc/ldap.conf ? It looks like the same information?

I have not yet done the PAM configuration.

The question is:
1. Whats wrong?
2. How do I confirm that the data is actually retreived from LDAP?
3. What about all the users currently in my passwd file, do I have to move them to LDAP incl. groups etc. ?

---

