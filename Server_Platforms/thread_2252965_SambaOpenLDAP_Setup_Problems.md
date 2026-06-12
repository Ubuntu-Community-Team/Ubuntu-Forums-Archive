---
title: "Samba/OpenLDAP Setup Problems"
date: 2014-11-16
forum: Server Platforms
---

### Post by peridian on 2014-11-16
Hi, (Ubuntu Server 14.04)

I am trying to get Samba to provision a domain using an OpenLDAP backend.  The OpenLDAP server is already setup (empty) and tested using ldapclient.

Started off following this guide: [https://help.ubuntu.com/lts/serverguide/samba-ldap.html](https://help.ubuntu.com/lts/serverguide/samba-ldap.html)

Successfully added the samba schema, and the indexes.  I then tried the below command, and got the following errors:

```

sudo smbldap-populate -e samba.ldif


Use of uninitialized value $smbldap_tools::config{"usersdn"} in pattern match (m//) at /usr/share/perl5/smbldap_tools.pm line 307.
Use of uninitialized value $smbldap_tools::config{"usersdn"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 308.
Use of uninitialized value $smbldap_tools::config{"suffix"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 308.
Use of uninitialized value $smbldap_tools::config{"groupsdn"} in pattern match (m//) at /usr/share/perl5/smbldap_tools.pm line 311.
Use of uninitialized value $smbldap_tools::config{"groupsdn"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 312.
Use of uninitialized value $smbldap_tools::config{"suffix"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 312.
Use of uninitialized value $smbldap_tools::config{"computersdn"} in pattern match (m//) at /usr/share/perl5/smbldap_tools.pm line 315.
Use of uninitialized value $smbldap_tools::config{"computersdn"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 316.
Use of uninitialized value $smbldap_tools::config{"suffix"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 316.
Use of uninitialized value $smbldap_tools::config{"suffix"} in concatenation (.) or string at /usr/share/perl5/smbldap_tools.pm line 325.
Populating LDAP directory for domain WORKGROUP (S-1-5-21-3398521608-3281450377-2100543852)
(using builtin directory structure)


Use of uninitialized value $config{"suffix"} in pattern match (m//) at /usr/sbin/smbldap-populate line 146.
Use of uninitialized value $config{"suffix"} in concatenation (.) or string at /usr/sbin/smbldap-populate line 147.
Cannot extract first attr and value from suffix:  at /usr/sbin/smbldap-populate line 147.

```

**Question 1: Why does this happen?**
**Question 2: Does the smb.conf file need to be configured before running this command?**

In the comments in the smb.conf file, it states to setup the server role as "domain controller", you use the samba-tool command to provision the domain.

Despite some extensive documentation for samba-tool, there doesn't seem to be much help for the parameters on this particular command.  From various pages, I pieced together the following command:

```

samba-tool domain provision --host-name=myserver --host-ip=10.x.x.x --realm=dc.myserver.tld --domain=dc.myserver --server-role="domain controller" --ldap-backend-type=openldap --use-ntvfs --use-rfc2307 --option="interfaces=lo eth0" --option="bind interfaces only=yes" --adminpass=Secret123 --root=root --ldapadminpass=Secret123

vi smb.conf

# Global parameters
[global]
        workgroup = dc.myserver
        realm = dc.myserver.tld
        netbios name = myserver
        interfaces = lo, eth0
        bind interfaces only = Yes
        server role = active directory domain controller
        dns forwarder = 10.x.x.x
        server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, smb
        dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
        idmap_ldb:use rfc2307 = yes
[netlogon]
        path = /var/lib/samba/sysvol/dc.myserver.tld/scripts
        read only = No
[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

```

However, it appears that Samba has setup it's own range of tdb database files, instead of using OpenLDAP.

I'm concerned that the options for openldap are not getting into the script, since the above guide shows setting up smb.conf with various ldap- options after the smbldap-populate command.

Although the parameter "ldapadminpass" exists, I can't see any options for specifying the actual openldap admin user path (e.g. "cn=admin,dc=myserver,dc=tld").

I also originally had these extra paramaters in the command: --ldap-action=setup --ldap-uri=ldap://myserver.tld:389/
However, the samba-tool response says these paramaters do not exist.

**Question 3: How is this supposed to work with openldap?**

I also do not like the fact you enter passwords in plain text at the command line.

**Question 4: What do these passwords actually match to?**
**Question 5: Can these be changed subsequently, or specified through encrypted passwords (e.g. slappasswd)?**

Also, any information on what the --root parameter means would be helpful.

Any help appreciated.

Regards,
Rob.

---

### Post by peridian on 2014-11-22
Hi,

Got further:

Answer 1: smbldap-tools needed configuring, which needs the smbldap-config.pl file (doesn't get installed, you can get it from smbldap-tools source code), which in turn needs samba to be running first (so these steps were the wrong way around).
Answer 2: Yes, Samba needs to be up and running first, so samba-tool should come first.
Answer 3: In the end I configured everything manually, installed and configured Kerberos, installed winbind, got them up and running one at a time, and by the end it was all good.
Answer 4 & 5: No idea, but manual configuration avoided having to specify these.

Regards,
Rob.

---

