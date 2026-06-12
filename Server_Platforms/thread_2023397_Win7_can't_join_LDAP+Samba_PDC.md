---
title: "Win7 can't join LDAP+Samba PDC"
date: 2012-07-12
forum: Server Platforms
---

### Post by shamusxz on 2012-07-12
Hello so i've been scratching my head regarding this issue for awhile now, going through complete reinstalls/reconfigs

I ended up following the Ubuntu 12.04 guide for server, as far as i could and now I am stuck at this point on 2 different servers.  Heres a quick walkthrough of what I have

 lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04

 slapd -V
@(#) $OpenLDAP: slapd  (Apr  5 2012 16:19:27) $
	buildd@roseapple:/build/buildd/openldap-2.4.28/debian/build/servers/slapd

smb.conf:
workgroup = TEST
  server string = %h PDC
  dns proxy = no
   log level = 2
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   os level = 33
   passdb backend = ldapsam:ldap://localhost
   ldap suffix = dc=TEST,dc=local
   ldap admin dn = cn=admin,dc=TEST,dc=local
   ldap machine suffix = ou=Computers
   ldap user suffix = ou=People
   ldap group suffix = ou=Groups
   ldap idmap suffix = ou=Idmap
   ldap ssl = no
   ldap passwd sync = yes
   domain logons = yes
   add machine script = /usr/sbin/smbldap-useradd -w '%u'
   add user script = /usr/sbin/smbldap-useradd -m '%u'

   logon path = \\%N\profile\%U
   logon drive = M:
   logon home = \\%N\%U
   logon script = logon.cmd

[profile]
    comment = User profiles
    path = /srv/samba/profile
    oplocks = false
    level2 oplocks = false
    csc policy = disable
    browseable = No
    writeable = Yes
    read only = No
    profile acls = yes
    create mask = 0600
    store dos attributes = Yes
    directory mask = 0700

[netlogon]
    comment = Network Logon Service
    path = /srv/samba/netlogon/
    browseable = No
    writeable = No
    write list = root

I can add and remove users using smbldap-tools without any issue, i have added the machine trying to join using "smbldap-useradd -m"

Here is what i see going wrong in the syslog:
Jul 12 13:44:10 ubuntuPDC slapd[2139]: conn=1233 op=1 BIND dn="" method=163
Jul 12 13:44:10 ubuntuPDC slapd[2139]: conn=1233 op=1 RESULT tag=97 err=14 text=SASL(0): successful result: security flags do not match required
Jul 12 13:44:10 ubuntuPDC slapd[2139]: conn=1233 op=2 BIND dn="" method=163
Jul 12 13:44:10 ubuntuPDC slapd[2139]: SASL [conn=1233] Failure: no secret in database
Jul 12 13:44:10 ubuntuPDC slapd[2139]: conn=1233 op=2 RESULT tag=97 err=49 text=SASL(-13): user not found: no secret in database
Jul 12 13:44:10 ubuntuPDC slapd[2139]: conn=1232 fd=19 closed (connection lost)

I feel it might be something I'm overlooking, so a second pair of eyes might point out the smalled detail i am missing.

Thanks!!

---

### Post by Rev. Dead Corpse on 2012-07-26
Getting the same thing on my LDAP. My client is a Mac running 10.6.8 though. 

I can get another Linux box to authenticate to a gui desktop (openSuSE, Mint, and Fedora). I can ssh from a Windows box, a Mac, and other Linux boxes no problem.

I just can't get the dang thing to work on the Mac. It's like the first part will ID the correct user dn, but then it drops the dn for the user when it tries to auth the password...

---

### Post by Rev. Dead Corpse on 2012-07-30
Narrowing this down to misconfigured pam.d. Working on it now...

ETA: tail -f /var/log/syslog is showing: 

conn=1005 op=0 BIND dn="" method=128

That BIND dn="" should be the dc=blah-blah. This shows up fine when doing an ssh, telnet, id, etc... But fails to populate the dn= when doing password authentication. In my mind, this points to libpam not being configured correctly. Someone correct me if I'm wrong.

---

