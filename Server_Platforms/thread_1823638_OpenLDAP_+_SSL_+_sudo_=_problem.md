---
title: "OpenLDAP + SSL + sudo = problem"
date: 2011-08-12
forum: Server Platforms
---

### Post by tall-male on 2011-08-12
I configured OpenLDAP (10.04.3 LTS) as mentioned on [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html), using SSL encryption. Port 389, non-ssl, is disabled and can only be accessed from localhost. It seems to work perfectly, but using sudo fails:

Trying to become root fails:

sudo su -
sudo: setreuid(ROOT_UID, user_uid): Operation not permitted

It looks I am suffering the bug mentioned in [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/423252](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/423252).

Is a solution already available? Using LDAP without SSL is not an option.

---

### Post by jimakira on 2011-10-03
i am digging the same problem here. Anyone has solution or workaround for this ??

---

