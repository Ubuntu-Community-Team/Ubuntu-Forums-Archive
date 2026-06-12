---
title: "winbind: net command: Could not connect to server 127.0.0.1"
date: 2015-02-11
forum: Server Platforms
---

### Post by peridian on 2015-02-11
Hi,  (Ubuntu server 14.04)

Does anybody know what winbind and/or the net command was even looking for at the localhost address?  ldap, smbd, nmbd, and krb5-kdc are all up and running and responding to command line requests on localhost.

```

sudo net domain join -U root
Enter root's password:
Could not connect to server 127.0.0.1
Connection failed: NT_STATUS_NO_LOGON_SERVERS

```

Prompted by the following error in the logs for winbind, which was failing to start up:

```

winbindd version 4.1.6-Ubuntu started
../source3/winbindd/winbindd_util.c:634(init_domain_list) Could not fetch our SID - did we join?
../source3/winbindd/winbindd.c:1204(winbindd_register_handlers) unable to initialise domain list

```

I had provisioned the domain with samba-tool successfully, so I had assumed I had run the net command to join the domain.  Guessing not, although getlocalsid does return the correct SID stored against the domain record in the LDAP database.

Any help would appreciated.

Regards,
Rob.

---

### Post by peridian on 2015-02-14
Figured it out, my DNS resolv.conf file was mucked up.  Fixed.

Regards,
Rob.

---

