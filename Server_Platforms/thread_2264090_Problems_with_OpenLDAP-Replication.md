---
title: "Problems with OpenLDAP-Replication"
date: 2015-02-05
forum: Server Platforms
---

### Post by psychofrog on 2015-02-05
Hi guys,


we just set up a Ubuntu Server with OpenLDAP running.
We also have a second server, running Ubuntu as well.
Now i tried to set up the replication using this guide: [https://help.ubuntu.com/lts/serverguide/openldap-server.html#openldap-server-replication](https://help.ubuntu.com/lts/serverguide/openldap-server.html#openldap-server-replication)


Problem is, when i want to add the provider file using sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f provider_sync.ldif
i get a error-message:
ldapadd: invalid format (line 5) entry: "olcDatabase={1}hdb,cn=config" 


Does anyone know where this problem comes from?

---

