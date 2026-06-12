---
title: "Replicating LDAP server"
date: 2014-03-18
forum: Server Platforms
---

### Post by arjun7 on 2014-03-18
Hi,
I am running Ubuntu 13.10 server on a server machine, and 13.10 desktop on a desktop machine.
I have an OpenLDAP server running successfully on the server, and the client is able to authenticate just fine.
However, I want to have a copy of the LDAP server running on the desktop also. I tried following the steps here:
[https://help.ubuntu.com/12.10/serverguide/openldap-server.html#openldap-server-replication](https://help.ubuntu.com/12.10/serverguide/openldap-server.html#openldap-server-replication)

However, when I run:
[FONT=monospace]**sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f consumer_sync.ldif**
[/FONT]
I get the following error:
[B]modifying entry "cn=module{0},cn=config"
ldap_modify: Type or Value exists (20)
        additional info: modify/add: olcModuleLoad: value #0 already exists 
[/B]
And when I run:
[FONT=monospace]**ldapsearch -z1 -LLLQY EXTERNAL -H ldapi:/// -s base contextCSN**
[/FONT][FONT=monospace]
[/FONT]I do not see the expected output as on the help page, but instead just get the following on both the provider and the consumer:

[FONT=monospace]**dn:**
[/FONT]
Please help!
As a follow up, once I get the slave LDAP server setup, how can I inform the other LDAP clients that there are two potential LDAP server locations instead of just the one earlier?

Thanks!

:guitar:

---

### Post by arjun7 on 2014-03-19
Issue might be related to another post [http://ubuntuforums.org/showthread.php?t=1732719](http://ubuntuforums.org/showthread.php?t=1732719) (but no replies there either)

---

