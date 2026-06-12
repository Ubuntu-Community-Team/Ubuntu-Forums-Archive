---
title: "LDAP Authentication troubles"
date: 2007-04-09
forum: Server Platforms
---

### Post by mopok on 2007-04-09
Hello. I'm experiensing troubles while trying to set up my Ubuntu Dapper box to authenticate users using Kerberos+ldap sheme from Active Directory. I've set up Kerberos and I can successfully obtain kerberos tickets using kinit. Now I'm trying to get user information from my Windows 2003 R2 PDC using ldap. The libnss-ldap.conf file looks like this:

host 192.168.0.252
base dc=mydomain,dc=local
uri ldap://mypdc.mydomain.local/
binddn [email]linuxproxy@mydomain.loca[/email]l
bindpw password
scope sub
ssl no
nss_base_passwd cn=Users,dc=mydomain,dc=local?sub
nss_base_shadow cn=Users,dc=mydomain,dc=local?sub
nss_base_group cn=Users,dc=mydomain,dc=local?sub?&(objectCategory=group)(gidnumb$
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member

This file was taken from this tutorial:
[http://blog.scottlowe.org/2007/01/15/linux-ad-integration-version-4/](http://blog.scottlowe.org/2007/01/15/linux-ad-integration-version-4/)

Also I've tried to use this tutorial:
[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)

And this one:
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

And the result was the same: I can't get information from AD using 'getent passwd' command. What am I doing wrong?

---

### Post by mopok on 2007-04-09
PS. Here is my nsswitch.conf

passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by mopok on 2007-04-09
Hello. I'm experiensing troubles while trying to set up my Ubuntu Dapper box to authenticate users using Kerberos+ldap sheme from Active Directory. I've set up Kerberos and I can successfully obtain kerberos tickets using kinit. Now I'm trying to get user information from my Windows 2003 R2 PDC using ldap. The libnss-ldap.conf file looks like this:

host 192.168.0.252
base dc=mydomain,dc=local
uri ldap://mypdc.mydomain.local/
binddn [email]linuxproxy@mydomain.loca[/email]l
bindpw password
scope sub
ssl no
nss_base_passwd cn=Users,dc=mydomain,dc=local?sub
nss_base_shadow cn=Users,dc=mydomain,dc=local?sub
nss_base_group cn=Users,dc=mydomain,dc=local?sub?&(objectCategory =group)(gidnumb$
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member

Here is my nsswitch.conf file:

passwd: compat ldap
group: compat ldap
shadow: compat ldap

hosts: files dns mdns
networks: files

protocols: db files
services: db files
ethers: db files
rpc: db files

netgroup: nis

This files were taken from this tutorial:
[http://blog.scottlowe.org/2007/01/15...ion-version-4/](http://blog.scottlowe.org/2007/01/15...ion-version-4/)

Also I've tried to use this tutorial:
[http://developer.novell.com/wiki/ind...the](http://developer.novell.com/wiki/ind...the) ntication

And this one:
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

And the result was the same: I can't get information from AD using 'getent passwd' command. What am I doing wrong?

---

### Post by chakkaradeep on 2007-04-09
> **mopok said:**
> 
passwd: compat ldap
group: compat ldap
shadow: compat ldap


Not sure, I usually change the above to,

[B][I]passwd: files ldap
group: files ldap
shadow: files ldap[/I][/B]

---

### Post by mopok on 2007-04-09
Just did it - no result, I mean positive :) I can only see my local accounts while calling getent passwd.

---

### Post by mopok on 2007-04-09
One more question: is there some place, where I can see the errors, occured while calling getent passwd command? Maybe some logs or something.

---

### Post by chakkaradeep on 2007-04-09
> **mopok said:**
> Just did it - no result, I mean positive :) I can only see my local accounts while calling getent passwd.

Can you check the ldap server connectivity using ldapsearch work ?

If that works, then there is some problem with the pam....

---

### Post by chakkaradeep on 2007-04-09
> **mopok said:**
> One more question: is there some place, where I can see the errors, occured while calling getent passwd command? Maybe some logs or something.

cat /var/log/messages

cat /var/log/syslog

---

### Post by mopok on 2007-04-09
Well, it seems, I have to reinstall my Dapper, cause after all my experiments I cannot use su and sudo commands:

mopok@ats:~$ su
su: Authentication information cannot be recovered
mopok@ats:~$ sudo nano /etc/nsswitch.conf
sudo: pam_authenticate: Authentication information cannot be recovered

I'll try do check it with ldapsearch tomorrow.

---

### Post by chakkaradeep on 2007-04-09
> **mopok said:**
> Well, it seems, I have to reinstall my Dapper, cause after all my experiments I cannot use su and sudo commands:

mopok@ats:~$ su
su: Authentication information cannot be recovered
mopok@ats:~$ sudo nano /etc/nsswitch.conf
sudo: pam_authenticate: Authentication information cannot be recovered

I'll try do check it with ldapsearch tomorrow.

did u use compat or files in nsswitch.conf ?. I have got those if i hadnt changed compat to files as i told in my earlier posts.

If you have any other linux partition, just boot into that linux, mount ubuntu dir, and change the nsswitch.conf, and boot into ubuntu back..it should work...

---

### Post by bapoumba on 2007-04-09
@ mopok: I've merged one of your duplicate thread in this one and deleted a third one with no answer.
It is not recommended to create multiple threads on the same subject, thanks.

---

### Post by mopok on 2007-04-10
@ bapoumba: I'm sorry, but I'm using this forum for a little time and I was confused, to which section to place my post.

Well, I recently tried to test my ldap server connectivity using ldapsearch and got this result:

root@ats:/home/mopok# ldapsearch -x -s sub
ldap_bind: Can't contact LDAP server (-1)

What could it be?

---

### Post by chakkaradeep on 2007-04-10
> **mopok said:**
> 
root@ats:/home/mopok# ldapsearch -x -s sub
ldap_bind: Can't contact LDAP server (-1)

What could it be?

I use to use this way,

**ldapsearch -x -b 'dc=example,dc=com' '(objectclass=*)'**

That should be same for ADS too

---

### Post by mopok on 2007-04-10
And here is the result:

root@ats:/home/mopok# ldapsearch -x -b 'dc=mydomain,dc=local' '(objectclass=*)'
# extended LDIF
#
# LDAPv3
# base <dc=mydomain,dc=local> with scope sub
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 1 Operations error
text: 00000000: LdapErr: DSID-0C090627, comment: In order to perform this ope
 ration a successful bind must be completed on the connection., data 0, vece

# numResponses: 1

---

### Post by mopok on 2007-04-10
Got some results:
ldapsearch -x -W -D "cn=linuxproxy,cn=Users,dc=mydomain,dc=local" "objectclass=User"

listed all my domain users.

---

### Post by mopok on 2007-04-10
More:

root@ats:/home/mopok# ldapsearch -x -W -D "cn=linuxproxy,cn=Users,dc=mydomain,dc=local" -LLL "(sAMAccountName=linuxproxy)"
Enter LDAP Password:
dn: CN=linuxproxy,CN=Users,DC=mydomain,DC=local
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: user
cn: linuxproxy
givenName: linuxproxy
distinguishedName: CN=linuxproxy,CN=Users,DC=mydomain,DC=local
instanceType: 4
whenCreated: 20070406095236.0Z
whenChanged: 20070406095345.0Z
displayName: linuxproxy
uSNCreated: 909889
uSNChanged: 909903
name: linuxproxy
objectGUID:: wJadNIPBiEOVM6JMc5N96w==
userAccountControl: 66048
badPwdCount: 0
codePage: 0
countryCode: 0
badPasswordTime: 128206626977031250
lastLogoff: 0
lastLogon: 128206627273125000
pwdLastSet: 128203268258593750
primaryGroupID: 513
objectSid:: AQUAAAAAAAUVAAAA8esbN7ffCXPoJ4xqswQAAA==
accountExpires: 9223372036854775807
logonCount: 0
sAMAccountName: linuxproxy
sAMAccountType: 805306368
userPrincipalName: [email]linuxproxy@mydomain.loca[/email]l
objectCategory: CN=Person,CN=Schema,CN=Configuration,DC=mydomain,DC=local

# refldap://ForestDnsZones.mydomain.local/DC=ForestDnsZones,DC=mydomain,DC=loca
 l

# refldap://DomainDnsZones.oblsnab.local/DC=DomainDnsZones,DC=mydomain,DC=loca
 l

# refldap://mydomain.local/CN=Configuration,DC=mydomain,DC=local

---

### Post by mopok on 2007-04-10
Whether all it means, that ldap server is operational and accessible from my Ubuntu box?

---

### Post by mopok on 2007-04-10
chakkaradeep, thanks for your help.
Everything works now and I see - everything worked even yesterday. The problem was that I forgot to set UNIX Attributes to my AD users that had to login to my Ubuntu box. ;)

---

### Post by bapoumba on 2007-04-10
> **mopok said:**
> @ bapoumba: I'm sorry, but I'm using this forum for a little time and I was confused, to which section to place my post.

No problem, mopok, and glad to see you got it to work :)

---

### Post by chakkaradeep on 2007-04-10
> **mopok said:**
> chakkaradeep, thanks for your help.
Everything works now and I see - everything worked even yesterday. The problem was that I forgot to set UNIX Attributes to my AD users that had to login to my Ubuntu box. ;)

kewl , happy that you got it working :)

---

