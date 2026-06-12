---
title: "Users can't change password using smbldap-pwd in Lucid [Samba + OpenLDAP]"
date: 2010-08-20
forum: Server Platforms
---

### Post by goofrider on 2010-08-20
I followed this guide to setup Samba + OpenLDAP in Lucid:

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

Everything works fine. Users can login from XP clients, access SMB shares, group mapping, etc. I also setup PAM/NSS integration so the user can login to shell/ssh and they can use passwd to change their UNIX password in the LDAP directory. 

However, users cannot change SMB password from XP clients (it says you do not have permission or something like that) nor use smbldap-password.
The exact error I get from smbldap-passwd is:

```

Failed to modify SMB password: Insufficient access at /usr/sbin/smbldap-passwd line 238, <STDIN> line 3.

```

I can still change user's SMB passwords smbldap-passwd as root,  so it looks like  ACL permission issue to sambaNTPassword and sambaLMPassword field?

The ACL rules as illustrated in the guide are:

```

olcAccess: to attrs=userPassword by dn="cn=admin,dc=tuxnetworks,dc=com" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read

```

I check other Samba + OpenLDAP howtos and they all have the same ACL rules. I check my old slapd.d config backup and it had the same rules too. I tried changing the rule to

```

olcAccess: to attrs=userPassword by dn="cn=admin,dc=tuxnetworks,dc=com" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange,sambaNTPassword,sambaLMPassword by self write by * read
olcAccess: to dn.base="" by * read

```

And it still didn't work.

Your help is very much appreciated.

---

### Post by goofrider on 2010-09-21
Can anyone help?

---

### Post by upengan78 on 2010-10-29
Hi there, 

I have the same problem, so thanks for starting the thread!

Did you find solution to this problem ? I have same ACLs as you originally had. 

I am not sure if smbpasswd will achieve same results because in smb.conf I have enabled ldap password syncing.

Please let me know. Thanks.

---

### Post by liororama on 2010-11-04
Hi,

I have the same problem here.

smbldap-passwd managed to change the unix password but failed to change the samba one.

Any ideas??

--lior

---

### Post by Zeosa on 2010-11-07
Try this:

```


access to attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,sambaPwdLastSet,sambaNTPassword
        by dn="cn=admin,dc=xxx,dc=xxx" write
        by anonymous auth
        by self write
        by * none

```

---

### Post by liororama on 2010-11-08
Hi,

Thanks for your help. It worked and now I can change the password using smbldap-passwd.

I needed to do the following:

Create an ldif file

----- ldif file start ----
dn: olcDatabase={1}hdb,cn=config
changetype: modify
delete: olcAccess
olcAccess: {0}
-
add: olcAccess
olcAccess: {0}  to
attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,
sambaPwdLastSet,sambaNTPassword by dn="cn=admin,dc=xxx,dc=xxx"
write by anonymous auth  by self write  by * none
-
-------- ldif file end -----

Remember to change the dc=xxx,dc=xxx entries inside the file.


Now you can run:

 ldapmodify -x -D cn=admin,cn=config -W -f file.ldif

where file.ldif is the file you created before....

Once this is done you can use smbldap-passwd :)


--lior
[COLOR=#888888]----------------------oo--o(:-:)o--oo----------------
Lior Amar, Ph.D.
Cluster Logic Ltd --> The Art of HPC
[www.clusterlogic.net]("http://www.clusterlogic.net/")
----------------------------------------------------------[/COLOR]

---

### Post by upengan78 on 2010-11-08
Thanks Zeosa ! also thanks to liororama for the .ldif and command. I know I will also need to run the command to modify the olcAccess. However, the command is not working in my case, can anyone help?

cat /tmp/modify_new 
```
dn: olcDatabase={1}hdb,cn=config
changetype: modify
delete: olcAccess
olcAccess: {0}
add: olcAccess
olcAccess: {0} to
attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,
sambaPwdLastSet,sambaNTPassword by dn="cn=admin,dc=pdc"
write by anonymous auth by self write by * none

```ldapmodify -x -D 'cn=admin,cn=config' -W -f /tmp/modify_new
```
Enter LDAP Password: 
modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Insufficient access (50)

```ADDITONAL INFO :

ldapsearch -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -b cn=config -W olcDatabase={1}hdb

```

Enter LDAP Password: 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
# extended LDIF
#
# LDAPv3
# base <cn=config> with scope subtree
# filter: olcDatabase={1}hdb
# requesting: ALL
#

# {1}hdb, config
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=pdc
olcAccess: {0}to attrs=userPassword by dn="cn=admin,dc=pdc" write by anonymous
  auth by self write by * none
olcAccess: {1}to attrs=shadowLastChange by self write by * read
olcAccess: {2}to dn.base="" by * read
olcAccess:: ezN9dG8gKiBieSBkbj0iY24RtaW4ggggsZGM9cGRjeSAqIHJlYWQg
olcLastMod: TRUE
olcRootDN: cn=admin,dc=pdc
olcRootPW: qqqqqqblah
olcRootPW: {crypt}64KIVVtLyblah
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: cn eq
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq
olcDbIndex: memberUid eq
olcDbIndex: uniqueMember eq
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1


```what am I doing incorrectly?

Please help!

Thanks

---

### Post by Zeosa on 2010-11-08
I had that problem too, for some reason there was an extra colon (:) in the file /etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif in the olcRootPW entry.

Try running slappasswd and pasting the input in there as olcRootPW (backup the original first as always)
so is looks similar to this:

```

.......
olcRootDN: cn=admin,cn=config
olcRootPW: {SSHA}xxxxxxxxxxxxxxx
........

```

Then authenticate with the password you used to generate the hash using slappasswd.

Originally I had two colons on the olcRootPW line that had my access to cn=config screwed up.

---

### Post by upengan78 on 2010-11-08
> **Zeosa said:**
> I had that problem too, for some reason there was an extra colon (:) in the file /etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif in the olcRootPW entry.

Try running slappasswd and pasting the input in there as olcRootPW (backup the original first as always)
so is looks similar to this:

```

.......
olcRootDN: cn=admin,cn=config
olcRootPW: {SSHA}xxxxxxxxxxxxxxx
........

```Then authenticate with the password you used to generate the hash using slappasswd.

Originally I had two colons on the olcRootPW line that had my access to cn=config screwed up.

Thanks again.

Yes, that's true. I also see "::" in front of olcAccess and olcRootPW below file,

cat /etc/ldap/slapd.d/cn\=config/olcDatabase\=\{1\}hdb.ldif

```
dn: olcDatabase={1}hdb
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=pdc
olcAccess: {0}to attrs=userPassword by dn="cn=admin,dc=pdc" write by anonymous
  auth by self write by * none
olcAccess: {1}to attrs=shadowLastChange by self write by * read
olcAccess: {2}to dn.base="" by * read
olcAccess:: ezN9dG8gKiBieSBkbj0iY249YWRtRjIiB3cml0ZSBieSAqIHJlYWQg
olcLastMod: TRUE
olcRootDN: cn=admin,dc=pdc
olcRootPW:: I2Flcm8kc21pabcd=
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: cn eq
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq
olcDbIndex: memberUid eq
olcDbIndex: uniqueMember eq
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub
structuralObjectClass: olcHdbConfig
entryUUID: b237ed4a-336c-102f-9e25-47eb1d9f6ff4
creatorsName: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
createTimestamp: 20100803170251Z
entryCSN: 20100803170251.989496Z#000000#000#000000
modifiersName: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
modifyTimestamp: 20100803170251Z
olcRootPW: {crypt}64KIVVtLyabcd

```

I will try to do what you have suggested

---

### Post by upengan78 on 2010-11-08
```
ldapmodify -x -D cn=admin,cn=config -W -f /tmp/modify 
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)

Same error again..
```I do see, below that, olcAccess line has two :: infront of it, 

```
olcAccess: {0}to attrs=userPassword by dn="cn=admin,dc=pdc" write by anonymous
  auth by self write by * none
olcAccess: {1}to attrs=shadowLastChange by self write by * read
olcAccess: {2}to dn.base="" by * read
olcAccess:: ezN9dG8gKiBieSBkbj0iY249YWRtaW4sZGM9cGRjIiB3cml0ZSBieSAqIHJlYWQg

```

olcRootPW :: was fixed using slappasswd, thanks.

Any idea how to fix this ? May be this is causing the issue.

---

### Post by upengan78 on 2010-11-08
ldapmodify -v -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f /tmp/modify

I ran above 3 times using different version of /tmp/modify each time.
```

dn: olcDatabase={1}hdb,cn=config
changetype: modify
delete: olcAccess
olcAccess: {0}
``````
dn: olcDatabase={1}hdb,cn=config
changetype: modify
 delete: olcAccess
 olcAccess:

``````
dn: olcDatabase={1}hdb,cn=config
add: olcAccess
olcAccess: to attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,sambaPwdLastSet,sambaNTPassword by dn="cn=admin,dc=pdc" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=pdc" write by * read
```finally now smbldap-passwd works for smb-ldap users (non root users)

```
smbldap-passwd 
Identity validation...
enter your UNIX password: 
Changing UNIX and samba passwords for lee
New password: 
Retype new password:
```

---

### Post by goofrider on 2011-08-16
> **upengan78 said:**
> ```
dn: olcDatabase={1}hdb,cn=config
add: olcAccess
olcAccess: to attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,sambaPwdLastSet,sambaNTPassword by dn="cn=admin,dc=pdc" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=pdc" write by * read
```finally now smbldap-passwd works for smb-ldap users (non root users)



I tried to follow your instructions but got an error when I ran the 3rd ldapmodify config file


```



add olcAccess:
        to attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,sambaPwdLastSet,sambaNTPassword by dn="cn=admin,dc=xxx,dc=yyy,dc=org" write by anonymous auth by self write by * none
        to attrs=shadowLastChange by self write by * read
        to dn.base="" by * read
        to * by dn="cn=admin,dc=xxx,dc=yyy,dc=org" write by * read
modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Type or value exists (20)
        additional info: modify/add: olcAccess: value #1 already exists

```

---

### Post by goofrider on 2011-08-16
OK I figured it out. The steps in reply #11 is specific to the previously mentioned config. My config has the following olcAccess lines:

Run:

```
$ sudo ldapsearch -v -Y EXTERNAL -H ldapi:/// -b cn=config
```

The olcAccess lines in my config looks like this:

```
# {1}hdb, config
...
olcAccess: {0}to dn.base="" by * read
olcAccess: {1}to * by dn="cn=admin,dc=xxx,dc=org" write by * read
...
```

The goal is to delete all olcAccess lines for # {1}hdb, config. I basically had to run step 1 twice and skip step 2.

Save this to /tmp/modify1

```
dn: olcDatabase={1}hdb,cn=config
changetype: modify
delete: olcAccess
olcAccess: {0}
```

And run the following cmd twice:

```
$ sudo ldapmodify -v -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f /tmp/modify1

```

After which, run the previous ldapsearch cmd and make sure there's no olcAccess lines.

Then save this to /tmp/modify3:

```
dn: olcDatabase={1}hdb,cn=config
add: olcAccess
olcAccess: to attrs=userPassword,shadowLastChange,sambaPwdMustChange,sambaLMPassword,sambaPwdLastSet,sambaNTPassword by dn="cn=admin,dc=xxx,dc=org" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=xxx,dc=org" write by * read
```

And run:

```

sudo ldapmodify -v -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f /tmp/modify3
```

Finally, run ldapsearch again to make sure all the aboce olcAccess lines were added to # {1}hdb, config.

---

