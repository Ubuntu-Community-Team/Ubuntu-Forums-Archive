---
title: "Samba Slave Share"
date: 2015-02-07
forum: Server Platforms
---

### Post by peridian on 2015-02-07
Hi,

I have a Samba master setup on Ubuntu server (LDAP backend) that is working just fine.  I've posted the config file for that one below.

I need to now setup a separate Ubuntu server  with actual Samba shares hosted, but where the users/groups for permissions come from the master server.

I can probably figure out the configuration for the slave after a few days, but if anybody can help with what I should set the slave to, it would be appreciated.

Regards,
Rob.

```

[global]
        workgroup = MYDOMAIN
        realm = MYDOMAIN.LOCAL
        netbios name = MACHINE
        server string = Robs Samba server


        hosts allow = 10.
        dns proxy = no
        dns forwarder = 10.x.x.x


        interfaces = lo, eth0
        bind interfaces only = yes


        syslog = 0
        log file = /var/log/samba/log.%m
        panic action = /usr/share/samba/panic-action %d


        server services = -s3fs, -ldap, +smb
        domain master = yes
        domain logons = yes
        logon script = logon.cmd


        security = domain
        encrypt passwords = yes


        passdb backend = ldapsam:ldap://machine.mydomain:389/
        ldapsam:trusted = yes
        ldap ssl = start tls
        ldap admin dn = cn=admin,ou=Admins,dc=machine,dc=mydomain
        ldap suffix = dc=machine,dc=mydomain
        ldap group suffix = ou=Groups
        ldap user suffix = ou=Users
        ldap machine suffix = ou=Computers
        ldap idmap suffix = ou=Idmaps
        ldap passwd sync = yes


        idmap_ldb:use rfc2307 = yes
        idmap config * : backend = ldap
        idmap config * : range = 1000000-1999999
        idmap config * : ldap_url = ldap://machine.mydomain:389/
        idmap config * : ldap_base_dn = ou=Idmaps,dc=machine,dc=mydomain
        idmap config * : ldap_user_dn = cn=idmapper,ou=Admins,dc=machine,dc=mydomain


        unix password sync = yes
        passwd program = /usr/sbin/smbldap-passwd "%u"
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *Password\supdated\ssuccessfully*


        map to guest = bad user
        usershare allow guests = no


        add user script = /usr/sbin/smbldap-useradd -a -c "" "%u"
        add machine script = /usr/sbin/smbldap-useradd -w -g machines -c "%u machine account" -s /bin/false "%u"
        add group script = /usr/sbin/smbldap-groupadd -a "%g"


        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g"


        load printers = no
        cups options = raw


        tls enabled = yes
        tls cafile = /usr/share/ca-certificates/extra/cacert.crt
        tls certfile = /etc/ssl/machine/machine.pem
        tls keyfile = /etc/ssl/machine/machine.key


[netlogon]
        browseable = no
        comment = Network Logon Service
        path = /var/lib/samba/sysvol/mydomain.local/scripts
        guest ok = yes
        read only = yes


[sysvol]
        browseable = no
        comment = Domain Logon Location
        path = /var/lib/samba/sysvol
        guest ok = yes
        read only = yes

```

---

### Post by volkswagner on 2015-02-08
I'm also interested in this subject. I'm no expert and have been toying with various SAMBA configs.

Is machine.mydomain.local samba 4? Is it an Active Directory Domain Controller? I don't see role listed in config.

I've successfully joined (but struggled) a SAMBA 3 member server to my SAMBA 4 AD DC and have notes which state
this [how-to]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") was most useful.

---

### Post by peridian on 2015-02-14
> **volkswagner said:**
> Is machine.mydomain.local samba 4?

This is a Samba 4 install yes.

> **volkswagner said:**
> I don't see role listed in config.

Correct, server role by default is set to "AUTO" which means it infers the value based upon other settings in the file, specifically the "security", "domain master" and "domain logons" settings.

> **volkswagner said:**
> Is it an Active Directory Domain Controller?

No, this is operating as a NT4 style domain, since I did not need the full array of AD services on my network, where there is only one Windows machine (all the rest are Linux/Android).

In reality this has turned out to be a pointless exercise, I realised I'm not even trying to create a MEMBER server, I am just trying to connect a CLIENT, so that the NAS Samba install can lookup users/groups.

If you try to create a MEMBER or DC, you are then faced with (best practice) replicating the LDAP backend to a separate backend for said install.  As this was not what I was after, I setup my Samba NAS to use the central LDAP/Kerberos services directly without a master Samba service in place.

Regards,
Rob.

---

