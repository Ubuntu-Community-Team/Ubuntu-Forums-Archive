---
title: "Samba BDC not authenticating users"
date: 2010-07-18
forum: Server Platforms
---

### Post by linux203 on 2010-07-18
I have two ubuntu 10.04 64-bit servers running samba (3.4.7) and openLDAP (2.4.21).  The LDAP directory is successfully replicating between the two servers.  These servers also serve as LDAP servers for sudo, pam, nss, and other services for a dozen servers without issues.

The BDC samba is configured to use itself for LDAP.  I connected to the BDC using the samba ldap credentials and verified I could a) see the Computer object b) read NTPassword and LMPassword.

The workstations can authenticate to the domain successfully against the PDC.  If a workstation boots and connects to the BDC, they login fails with:
```

[2010/07/18 11:46:23,  0] rpc_server/srv_netlog_nt.c:336(get_md4pw)
  get_md4pw: Workstation MACHINENAME$: no account in domain
[2010/07/18 11:46:23,  0] rpc_server/srv_netlog_nt.c:584(_netr_ServerAuthenticate3)
  _netr_ServerAuthenticate3: failed to get machine password for account MACHINENAME$: NT_STATUS_ACCESS_DENIED

```a successful authentication against the PDC shows:
```

[2010/07/18 11:59:20,  1] smbd/service.c:1063(make_connection_snum)
  MACHINENAME (192.168.2.145) connect to service netlogon initially as user username (uid=30000, gid=512) (pid 1727)
[2010/07/18 11:59:20,  1] smbd/service.c:1063(make_connection_snum)
  MACHINENAME (192.168.2.145) connect to service data initially as user nobody (uid=65534, gid=65534) (pid 1727)
[2010/07/18 11:59:20,  1] smbd/service.c:1063(make_connection_snum)
  MACHINENAME (192.168.2.145) connect to service username initially as user username (uid=30000, gid=512) (pid 1727)

```smb.conf from BDC:
```

[global]
        idmap gid = 10000-20000
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        passwd program = /usr/bin/passwd %u
        dns proxy = no
        ldap passwd sync = Yes
        idmap uid = 10000-20000
        workgroup = DOMAINNAME
        debug level = 1
        ldap admin dn = cn=LDAPProxy,dc=example,dc=com
        security = user
        usershare allow guests = yes
        add machine script = /usr/sbin/smbldap-useradd -w "%u"
        delete user script = /usr/sbin/smbldap-userdel "%u"
        max log size = 1000
        log file = /var/log/samba/log.%m
        ldap user suffix = ou=Users
        add group script = /usr/sbin/smbldap-groupadd -p "%g"
        socket options = TCP_NODELAY
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        domain master = no
        map to guest = bad user
        idmap backend = ldap://localhost/
        encrypt passwords = true
        passdb = ldapsam:ldap://localhost/
        wins support = yes
        ldap delete dn = Yes
        server string = %h server (Samba, Ubuntu)
        ldap machine suffix = ou=Computers
        ldap group suffix = ou=Builtin
        ldap suffix = dc=example,dc=com
        unix password sync = yes
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
        syslog = 0
        ldap idmap suffix = ou=idmap
        panic action = /usr/share/samba/panic-action %d
        domain logons = yes
        pam password change = yes

[netlogon]
   comment = Network Logon Service
   path = /var/lib/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


```Thanks.

---

### Post by linux203 on 2010-07-22
```
passdb = ldapsam:ldap://localhost/
```
 
should be:
 
```
passdb backend = ldapsam:ldap://localhost/
```

---

