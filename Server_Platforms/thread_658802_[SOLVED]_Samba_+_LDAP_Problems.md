---
title: "[SOLVED] Samba + LDAP Problems"
date: 2008-01-05
forum: Server Platforms
---

### Post by codemaster on 2008-01-05
I am attempting to setup Samba with credentials from an OpenLDAP server.

The problem I am having is I want to allow my LDAP users to change their password (ie - using passwd, smbpasswd, etc.) and am running into problems w/ smbpasswd.

I attempt running smbpasswd -D 4 (to get a bit of debugging, just in case) and I find two problems near the end:
SPNEGO login failed: Logon failure
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE

I went onto the #samba channel on FreeNode and asked around. Finally, one kind person recommended I try adding
client use spnego = no
to my /etc/samba/smb.conf

Attempting smbpasswd -D 4 again, I received a different error:
cli_session_setup: NT1 session setup failed!
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE

I am stuck here as googling around for answers still takes me nowhere :)

Here are the results of my testparm:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
        workgroup = WORKGROUP
        server string = %h
        null passwords = Yes
        passdb backend = ldapsam:ldap://ldap.test.org
        log level = 256
        log file = /usr/local/samba/var/log.%m
        max log size = 50
        client use spnego = No
        domain logons = Yes
        os level = 255
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        ldap admin dn = cn=samba,dc=test,dc=org
        ldap group suffix = o=Departments
        ldap idmap suffix = o=Employees
        ldap passwd sync = Yes
        ldap suffix = dc=test,dc=org
        ldap user suffix = o=Employees

[homes]
        comment = Home Directories
        path = /home/%u
        read only = No
        browseable = No

[printers]
        comment = All Printers
        path = /usr/spool/samba
        printable = Yes
        browseable = No



If anyone has any advice or assistance, it's greatly appreciated! :D

---

### Post by kevinp on 2008-01-13
Sorry - posted in wrong thread

---

### Post by codemaster on 2008-01-19
I eventually (somewhat) solved my problem.

Samba is looking for the LDAP config file at /etc/ldap.conf, while OpenLDAP stores it as /etc/ldap/ldap.conf, so I simply create a soft-link to the file :)

---

