---
title: "[SOLVED] samba ldap nss"
date: 2008-07-01
forum: Server Platforms
---

### Post by cdenley on 2008-07-01
I'm having a strange problem with my samba domain controller using LDAP. As far as I can tell, everything is set up properly. I can see the LDAP unix accounts
```

getent passwd
getent group

```
I can search the ldap server, and everything seems correct
```

ldapsearch -x

```
I can join the domain, log in. Group memberships seem correct. On windows clients, if I look at a file's security properties, it lists my groups gid instead of the group name. If I click add, then search for users and groups, it lists my groups by display name, but doesn't show any users.

I think this is related to this weird output I get on the server
sudo net groupmap list
```

Domain Admins (S-1-5-21-2685038278-1934203593-1148576369-512) -> 10001
Domain Users (S-1-5-21-2685038278-1934203593-1148576369-513) -> 10002

```

On a server I have with a similar setup except without LDAP, it gives the name of the unix group instead of the GID.
sudo net groupmap list
```

Domain Users (S-1-5-21-3631119556-1891064373-1155372299-513) -> ntusers
Domain Admins (S-1-5-21-3631119556-1891064373-1155372299-512) -> ntadmins

```

---

### Post by promodus on 2008-07-01
Hmm. Good question.
I will try some theory that I understand, maybe it will be of some help.
Bare with me.

> I'm having a strange problem with my samba domain controller using LDAP. As far as I can tell, everything is set up properly. I can see the LDAP unix accounts
```

getent passwd
getent group

```
I can search the ldap server, and everything seems correct
```

ldapsearch -x

```
I can join the domain, log in. Group memberships seem correct. On windows clients, if I look at a file's security properties, it lists my groups gid instead of the group name. If I click add, then search for users and groups, it lists my groups by display name, but doesn't show any users.


Do you have in your /etc/ldap/slapd.conf
```
index displayName eq
```

On my server it's listed as
```
index sambaSIDList,sambaDomainName,displayName eq
```

> 
I think this is related to this weird output I get on the server
sudo net groupmap list
```

Domain Admins (S-1-5-21-2685038278-1934203593-1148576369-512) -> 10001
Domain Users (S-1-5-21-2685038278-1934203593-1148576369-513) -> 10002

```

On a server I have with a similar setup except without LDAP, it gives the name of the unix group instead of the GID.
sudo net groupmap list
```

Domain Users (S-1-5-21-3631119556-1891064373-1155372299-513) -> ntusers
Domain Admins (S-1-5-21-3631119556-1891064373-1155372299-512) -> ntadmins

```

Makes me think it's more an LDAP issue than a SAMBA one.
SAMBA is binding, it's just not able to resolve the GID.

or, maybe you need winbind?

---

### Post by cdenley on 2008-07-01
```

cdenley@zimbra:~$ sudo grep displayName /opt/zimbra/conf/slapd.conf.in|grep index
index   displayName            pres,eq,sub

```

winbind doesn't seem to help

---

### Post by promodus on 2008-07-01
Here is what is listed in my slapd configuration.
```
cat /etc/ldap/slapd.conf | grep index
# for indexing.
index           objectClass eq
index		sambaSIDList,sambaDomainName,displayName	eq
index		SambaSID					eq,sub
index		sambaPrimaryGroupSID				eq
index		uid,uidNumber,gidNumber,memberUid		eq
index		cn,mail,surname,givenname			eq,subinitial

```

Maybe try playing with the index options?

---

### Post by cdenley on 2008-07-02
Here is what I had
```

index   objectClass                 eq
index   zimbraForeignPrincipal      eq
index   zimbraYahooId               eq
index   zimbraId                    eq
index   zimbraVirtualHostname       eq
index   zimbraVirtualIPAddress      eq
index   zimbraAuthKerberos5Realm    eq
index   zimbraMailCatchAllAddress   eq,sub
index   zimbraMailDeliveryAddress   eq,sub
index   zimbraMailForwardingAddress eq
index   zimbraMailAlias             eq,sub
index   zimbraMailTransport         eq
index   zimbraDomainName            eq,sub
index   zimbraShareInfo             sub
index   uid                         pres,eq
index   mail                   pres,eq,sub
index   cn                     pres,eq,sub
index   displayName            pres,eq,sub
index   sn                     pres,eq,sub
index   gn                     pres,eq,sub
index   zimbraCalResSite       eq,sub
index   zimbraCalResBuilding   eq,sub
index   zimbraCalResFloor      eq,sub
index   zimbraCalResRoom       eq,sub
index   zimbraCalResCapacity   eq
index   entryUUID              eq
index   entryCSN               eq
index uidNumber             eq
index gidNumber             eq
index memberUID             eq
index sambaSID              eq
index sambaPrimaryGroupSID  eq
index sambaDomainName       eq

```

I tried adding "index sambaSIDList eq", didn't help. Adding ",sub" to the "sambaSID" line only caused the clients to not be able to see the groups. Zimbra uses most of those attributes, and I don't want to screw it up since I don't fully understand what these do. Do you have any suggestions? The only indices I added were straight from a zimbra guide.
[http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Configuring_Zimbra_LDAP](http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Configuring_Zimbra_LDAP)
Could the problem be with something else?

---

### Post by promodus on 2008-07-02
On your server what do you get when you type

```
net group
```

I'm curious what samba will return?

---

### Post by cdenley on 2008-07-02
> **promodus said:**
> On your server what do you get when you type

```
net group
```

I'm curious what samba will return?

```

cdenley@zimbra:~$ net group
Password:
Domain Admins
Domain Users

```

---

### Post by promodus on 2008-07-02
I changed the name of "Domain Guests" in my ldap to Domain Guests 2... and it shows up.
I don't think it's an indexing problem.

```
root@ldapserver:~# net groupmap list
Domain Admins (S-1-5-21-2077956632-1721461777-1151864052-512) -> 512
Domain Users (S-1-5-21-2077956632-1721461777-1151864052-513) -> 513
Domain Guests2 (S-1-5-21-2077956632-1721461777-1151864052-514) -> 514
Domain Computers (S-1-5-21-2077956632-1721461777-1151864052-515) -> 515
Administrators (S-1-5-32-544) -> 544
Account Operators (S-1-5-32-548) -> 548
Print Operators (S-1-5-32-550) -> 550
Backup Operators (S-1-5-32-551) -> 551
Replicators (S-1-5-32-552) -> 552
```

I have to rebuild my ldap server to do anymore testing. Maybe by the weekend I'll see how the windows side of things is behaving.

---

### Post by cdenley on 2008-07-02
I deleted the groups, then re-created them. Now the group name is listed instead of the gid, as it should. However, what I wanted to begin with was to be able to list the domain users when changing security permissions or group memberships. This works fine without LDAP, but with LDAP it will list groups but not users. I thought this was another symptom of the same problem, but apparently not.

By the way, maybe I messed up my groups before because I had everything set up in LDAP, then I purged samba and got a new SID when I reinstalled. I had to go back and change the SID's on the groups and users.

---

### Post by cdenley on 2008-07-02
```

net user

```
This command gives me blank output. I change "ldapsam:ldap://127.0.0.1/" to tdbsam, restart samba, add samba accounts. Now the command above lists the users.

---

### Post by promodus on 2008-07-03
Well, this much I know so far when using ldapsam.

Domain users, Domain Admins, and the SID are both queried from LDAP.
The ntusers and ntadmins, i'm not sure what attribute or if that's coming from LDAP at all.

Are group 512 and 513 set in /etc/groups or is it something that's pulled from LDAP on the host?

If it's pulling those two groups from LDAP, what do you get from:
```
getent group
```

And my last thought is that maybe SAMBA doesn't know where the UNIX groups are to do the mapping?  SAMBA wanting to look up group 512, and 513 but doesn't know where those UID's are in the directory.

A thought. I'm interested in figuring this one out.

Cheers,
Rich.

---

### Post by promodus on 2008-07-04
> 
I can join the domain, log in. Group memberships seem correct. On windows clients, if I look at a file's security properties, it lists my groups gid instead of the group name. If I click add, then search for users and groups, it lists my groups by display name, but doesn't show any users.


I recreated my LDAP + SAMBA Domain. On my windows host, I see all group names. No group ID's show up. My Server still lists the net groupmap list identical to the ways yours does.

If you're wanting RDP access and shell access to take a look. I may be able to arrange something for the weekend. PM me for my email info.

---

### Post by cdenley on 2008-07-04
> **promodus said:**
> I recreated my LDAP + SAMBA Domain. On my windows host, I see all group names. No group ID's show up. My Server still lists the net groupmap list identical to the ways yours does.

I think as long as I don't edit the group it works fine. I'm still having trouble with the users, though. What output do you get with this command?
```

net user

```

---

### Post by promodus on 2008-07-04
The list is the names of the few users I have listed in that OU.
root
nobody
rich

---

### Post by cdenley on 2008-07-05
It doesn't list any users for me using LDAP. Maybe it is because all my users have been edited at some point, and it is the same problem as the groups. I'll have to test this on Monday by creating a new user, then see if it shows up with "net user".

---

### Post by cdenley on 2008-07-07
Doesn't work, even with a new user. I can't seem to get "net user" to work with LDAP no matter what I do. Apparently it's some kind of permissions problem.

net -d 1 user
```

[2008/07/07 08:30:04, 1] libads/cldap.c:recv_cldap_netlogon(219)
  no reply received to cldap netlogon
[2008/07/07 08:30:05, 1] utils/net.c:net_find_server(430)
  no server to connect to
Password:
[2008/07/07 08:30:07, 1] libsmb/clirap2.c:cli_RNetUserEnum0(870)
  NetUserEnum gave error 50
[2008/07/07 08:30:07, 1] utils/net_rap.c:net_rap_user(741)
  Net user returned: 50
cdenley@zimbra:~$ net -d 1 user
[2008/07/07 08:30:18, 1] libads/cldap.c:recv_cldap_netlogon(219)
  no reply received to cldap netlogon
Password:
[2008/07/07 08:30:20, 1] utils/net_rpc.c:run_rpc_command(170)
  rpc command function failed! (NT_STATUS_ACCESS_DENIED)

```

"pdbedit -L" does work correctly.

net rpc info
```

Domain Name: MYDOMAIN
Domain SID: [MY SID]
Sequence number: 1215440253
**Num users: 0**
Num domain groups: 2
Num local groups: 0

```

```

cdenley@zimbra:~$ net user info cdenley
Password:
Domain Admins

```

---

### Post by promodus on 2008-07-07
I almost forgot I have added access controls.
Within slapd.conf
```
include /etc/ldap/slad.access.conf
```

Within slapd.access.conf:
```
# This configuration file contains default ACLs that attempt to cater
# to most setups, specifically unix authentication, samba's ldapsam backend
# and allowing users to have a shared address book
# If these ACLs don't meet your needs, please do not modify the file in-place,
# but rather make a copy, and change the include directive in slapd.conf
# This file is *not* marked as noreplace, so it will be replaced during an
# upgrade, this is done so that we can ensure that the ACLs are in sync with
# the schema files they require.

# The root DIT should be accessible to all clients
access to dn.exact=""
	by * read

# So should the schema
access to dn.subtree="cn=Subschema"
	by * read

# Generic ACLs
# These ACLs should work well for any domain-based (ie dc=,dc=) suffix,
# but need adjustment and testing for any other suffix
# Note that these ACLs allow anonymous read access to most non-password 
# attributes, you may want to prevent leakage of this information by 
# removing the "by anonymous read" lines
# Regex-based ACLs also impose a performance penalty, replace
# for example dn.regex="^([^,]+,)?ou=People,(dc=[^,]+(,dc=[^,]+)*)$" with
# dn.subtree="ou=People,dc=example,dc=com" and all $2's with dc=example,dc=com
# if you need the extra performance

# Protect passwords, using a regex so we can have generic accounts with
# write access
# Openldap will not authenticate against non-userPassword attributes
# but we would have to duplicate most rules ...
access to dn.regex="^([^,]*,)?ou=[^,]+,(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=sambaLMPassword,sambaNTPassword,userPassword,sambaPasswordHistory,sambaPwdLastSet
        by self write
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by anonymous auth
        by * none

# ACL allowing samba domain controllers to write their domain info
access to dn.regex="^sambaDomainName=([^,]+),(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=entry,children,sambaDomain
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read

# ACL allowing samba domain controllers to add user accounts
access to dn.regex="^([^,]+,)?ou=People,(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=entry,children,posixAccount,sambaSamAccount
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read

# allow users to modify their own "address book" entries:
access to dn.regex="([^,]+,)?ou=People,(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=inetOrgPerson,mail
        by self write
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read

# Allow samba domain controllers to create groups and group mappings
access to dn.regex="^([^,]+,)?ou=Group,(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=entry,children,posixGroup,sambaGroupMapping
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read

# Allow samba domain controllers to create machine accounts
access to dn.regex="^([^,]+,)?ou=Hosts,(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=entry,children,posixAccount,inetOrgperson,sambaSamAccount
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read

# Allow samba to create idmap entries
access to dn.regex="^([^,]+,)?ou=Idmap,(dc=[^,]+(,dc=[^,]+)*)$"
        attrs=entry,children,sambaIdmapEntry
        by dn.exact,expand="uid=root,ou=Users,$2" write
        by group.expand="cn=Domain Controllers,ou=Groups,$2" write
	by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read

# Allow users in the domain to add entries to the "global address book":
# For use with Evolution, the attrs list could be modified to be:
# attrs=children,entry,inetOrgPerson,evolutionperson,calEntry
# if evolutionperson.schema and calendar.schema are available
access to dn.regex="^([^,]+,)?ou=Contacts,(dc=[^,]+(,dc=[^,]+)*)$"
       attrs=children,entry,inetOrgPerson
        by dn.sub,expand="ou=Users,$2" write
        by group.expand="cn=Replicator,ou=Groups,$2" write
        by users read
	by anonymous read
```

---

### Post by promodus on 2008-07-07
```
[global]
   netbios name = ldapserver
   workgroup = error
   enable privileges = yes
   security = user
   wins support = yes
   name resolve order = wins bcast hosts
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   os level = 33

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
   security = user
   encrypt passwords = true
    passdb backend = ldapsam:ldap://127.0.0.1
    ldap suffix = dc=error,dc=local
    ldap admin dn = cn=admin,dc=error,dc=local
    ldap group suffix = ou=Groups
    ldap machine suffix = ou=Hosts
    ldap user suffix = ou=Users
    ldap idmap suffix = ou=Idmap
    ldap passwd sync = yes
    
   passwd program = /usr/sbin/smbldap-passwd %u
   passwd chat = *New*password* %n\n *Retype*new*password* %n\n *all*authentication*tokens*updated*

########## Domains ###########
   domain logons = yes
   prefered master = yes
   #logon path = \\ldapserver\profiles\%U\profile
   #logon drive = H:
   #logon home = \\ldapserver\profiles\%U
   #logon script = logon.cmd

   add user script = /usr/sbin/smbldap-useradd -m "%u"
   delete user script = /usr/sbin/smbldap-userdel "%u"
   add machine script = /usr/sbin/smbldap-useradd -w "%u"
   add group script = /usr/sbin/smbldap-groupadd -p "%g"
   delete group script = /usr/sbin/smbldap-groupdel "%g"
   add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
   delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
   set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"

########## Printing ##########
;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin

############ Misc ############
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8912
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================
[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = no
   create mask = 0700
   directory mask = 0700

[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   browseable = yes
   writable = yes
   share modes = no

[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = yes
   browseable = yes
   writeable = yes
   create mask = 0600
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

### Post by cdenley on 2008-07-08
```

cdenley@zimbra:~$ grep -v \# /etc/samba/smb.conf|grep -v \;|grep -v "^$"
[global]
   workgroup = FMC
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
passdb backend = ldapsam:ldap://127.0.0.1/
ldap admin dn = "cn=config"
ldap suffix = dc=mydomain,dc=com
ldap group suffix = ou=groups
ldap user suffix = ou=people
ldap machine suffix = ou=machines
add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null -o -u 9999 -g 65534 "%u"
enable privileges = yes
   obey pam restrictions = no
   invalid users = root
   unix password sync = no
   ldap password sync = yes
   domain logons = yes
   logon path = \\%N\profiles\%U
   logon drive = H:
   logon home = \\%N\%U
   logon script = logon.cmd
   socket options = TCP_NODELAY
   usershare allow guests = yes
[homes]
   comment = Home Directories
   browseable = yes
   writeable = yes
   map acl inherit = yes
   create mask = 0700
   directory mask = 0700
   valid users = %S
[netlogon]
   comment = Network Logon Service
   path = /opt/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no
[profiles]
   comment = Users profiles
   path = /opt/samba/profiles
   guest ok = no
   browseable = no
   writeable = yes
   create mask = 0600
   directory mask = 0700
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

```

```

cdenley@zimbra:~$ sudo grep -v \# /opt/zimbra/conf/slapd.conf.in|grep -v "^$"
include		"/opt/zimbra/openldap/etc/openldap/schema/core.schema"
include		"/opt/zimbra/openldap/etc/openldap/schema/cosine.schema"
include		"/opt/zimbra/openldap/etc/openldap/schema/inetorgperson.schema"
include		"/opt/zimbra/openldap/etc/openldap/schema/amavisd.schema"
include		"/opt/zimbra/openldap/etc/openldap/schema/zimbra.schema"
include		"/opt/zimbra/lib/conf/zimbra-ext.schema"
include "/opt/zimbra/openldap/etc/openldap/schema/nis.schema"
include "/opt/zimbra/openldap/etc/openldap/schema/samba.schema" 
threads		8
pidfile		"/opt/zimbra/openldap/var/run/slapd.pid"
argsfile	"/opt/zimbra/openldap/var/run/slapd.args"
TLSCertificateFile /opt/zimbra/conf/slapd.crt
TLSCertificateKeyFile /opt/zimbra/conf/slapd.key
TLSVerifyClient never
loglevel @@ldap_log_level@@
modulepath	/opt/zimbra/openldap/libexec/openldap
moduleload	back_bdb.la
moduleload	back_monitor.la
moduleload	syncprov.la
moduleload	accesslog.la
access to dn.subtree=""
	by dn.children="cn=admins,cn=zimbra" write
	by * break
access to dn.base=""
	by * read
access to dn.base="cn=Subschema"
	by * read
access to attrs=userPassword
	by anonymous auth
	by dn.children="cn=admins,cn=zimbra" write
access to dn.subtree="cn=zimbra" 
      by dn.children="cn=admins,cn=zimbra" write
access to attrs=zimbraZimletUserProperties,zimbraGalLdapBindPassword,zimbraGalLdapBindDn,zimbraAuthTokenKey,zimbraPreAuthKey,zimbraPasswordHistory,zimbraIsAdminAccount,zimbraAuthLdapSearchBindPassword
	by dn.children="cn=admins,cn=zimbra" write
        by * none
access to attrs=objectclass
	by dn.children="cn=admins,cn=zimbra" write
	by dn.exact="uid=zmpostfix,cn=appaccts,cn=zimbra" read
	by dn.exact="uid=zmamavis,cn=appaccts,cn=zimbra" read
	by * read
access to attrs=amavisAccount
	by dn.children="cn=admins,cn=zimbra" write
	by dn.exact="uid=zmamavis,cn=appaccts,cn=zimbra" read
	by * break
access to attrs=mail
	by dn.children="cn=admins,cn=zimbra" write
	by dn.exact="uid=zmamavis,cn=appaccts,cn=zimbra" read
	by * break
access to attrs=zimbraAllowFromAddress
	by dn.children="cn=admins,cn=zimbra" write
	by dn.exact="uid=zmpostfix,cn=appaccts,cn=zimbra" read
access to filter=(!(zimbraHideInGal=TRUE)) attrs=cn,co,company,dc,displayName,givenName,gn,initials,l,mail,o,ou,physicalDeliveryOfficeName,postalCode,sn,st,street,streetAddress,telephoneNumber,title,uid
	by dn.children="cn=admins,cn=zimbra" write
	by dn.exact="uid=zmpostfix,cn=appaccts,cn=zimbra" read
	by * read
access to attrs=zimbraId,zimbraMailAddress,zimbraMailAlias,zimbraMailCanonicalAddress,zimbraMailCatchAllAddress,zimbraMailCatchAllCanonicalAddress,zimbraMailCatchAllForwardingAddress,zimbraMailDeliveryAddress,zimbraMailForwardingAddress,zimbraPrefMailForwardingAddress,zimbraMailHost,zimbraMailStatus,zimbraMailTransport,zimbraDomainName,zimbraDomainType,zimbraPrefMailLocalDeliveryDisabled
	by dn.children="cn=admins,cn=zimbra" write
	by dn.exact="uid=zmpostfix,cn=appaccts,cn=zimbra" read
	by * read
access to attrs=entry
	by dn.children="cn=admins,cn=zimbra" write
	by * read
database	config
rootpw {SSHA}[hash]
database	monitor
rootdn		"cn=config"
access to dn.children="cn=monitor"
	by dn.children="cn=admins,cn=zimbra" read
database	bdb
suffix		""
rootdn		"cn=config"
cachesize 10000
idlcachesize 10000
checkpoint 64 5
directory	"/opt/zimbra/openldap-data"
index   objectClass                 eq
index   zimbraForeignPrincipal      eq
index   zimbraYahooId               eq
index   zimbraId                    eq
index   zimbraVirtualHostname       eq
index   zimbraVirtualIPAddress      eq
index   zimbraAuthKerberos5Realm    eq
index   zimbraMailCatchAllAddress   eq,sub
index   zimbraMailDeliveryAddress   eq,sub
index   zimbraMailForwardingAddress eq
index   zimbraMailAlias             eq,sub
index   zimbraMailTransport         eq
index   zimbraDomainName            eq,sub
index   zimbraShareInfo             sub
index   zimbraACE                   sub
index   uid                         pres,eq
index   mail                   pres,eq,sub
index   cn                     pres,eq,sub
index   displayName            pres,eq,sub
index   sn                     pres,eq,sub
index   gn                     pres,eq,sub
index   zimbraCalResSite       eq,sub
index   zimbraCalResBuilding   eq,sub
index   zimbraCalResFloor      eq,sub
index   zimbraCalResRoom       eq,sub
index   zimbraCalResCapacity   eq
index   entryUUID              eq
index   entryCSN               eq
index uidNumber             eq
index gidNumber             eq
index memberUID             eq
index sambaSID              eq
index sambaPrimaryGroupSID  eq
index sambaDomainName       eq
sizelimit unlimited
timelimit unlimited

```

I hardly changed anything in slapd.conf, so it probably isn't the problem. I tried copying most of your access controls, but they didn't seem to work.

---

### Post by cdenley on 2008-07-08
I was missing a the account flags in the ldap user accounts (sambaAcctFlags). Samba would find the accounts, but skip them because it was missing that attribute. It now works as expected.

---

### Post by promodus on 2008-07-08
Awesome! happy to help.

Cheers,
Rich.

---

