---
title: "Help me building DC with samba&amp;LDAP on Ubuntu 10.04"
date: 2010-12-18
forum: Server Platforms
---

### Post by tanlenhat on 2010-12-18
My scenario is based on Ubuntu server guide, can be found at [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
Step 1: I do as chapter 6, install OPENLDAP server, populating LDAP => run ok.
Step 2: do as LDAP Authentication section => run ok.
Step 3: Install samba => ok.
Step 4: do as OpenLDAP Configuration section => there's a problem here: when I run the command:
> ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif
I can't login to LDAP server, it said that:
> ldap_bind: Invalid credentials (49)
I am sure that the password is correct, but I still receive this message :(
Please help me! [-o<

---

### Post by brettg on 2010-12-19
Follow [these instructions]("http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html") to the letter.

---

### Post by tanlenhat on 2010-12-20
> **brettg said:**
> Follow [these instructions]("http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html") to the letter.
I follwed it but got an error when windows xp joined to domain: 
> The following error occurred when DNS was queried for the service  location (SRV) resource record used to locate a domain controller for  domain tat.com:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.tat.com

Common causes of this error include the following:

- The DNS SRV record is not registered in DNS.

- One or more of the following zones do not include delegation to its child zone:

tat.com
com
. (the root zone)


---

### Post by tanlenhat on 2010-12-21
anyone can help me?:(

---

