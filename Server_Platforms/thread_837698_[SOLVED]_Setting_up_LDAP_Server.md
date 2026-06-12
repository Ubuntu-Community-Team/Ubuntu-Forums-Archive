---
title: "[SOLVED] Setting up LDAP Server"
date: 2008-06-22
forum: Server Platforms
---

### Post by johnnybeem on 2008-06-22
Hi,
I am trying to set up an LDAP server so that all of my usernames and passwords are the same for several computers in the house.

I followed the exact directions in several Ubuntu tutorials online, and am desperate for help. Here are my configs (copied from the Ubuntu Community tutorial):


Server:
**slapd.conf** Added these lines; also tried setting rootpw to the output of slappasswd
suffix          "dc=example,dc=com"
directory       "/var/lib/ldap"
rootdn          "cn=admin,dc=example,dc=com"
rootpw          secret

Client
**nsswitch.conf** Changed these lines
passwd:         files ldap
group:          files ldap

**ldapsearch outputs what you would expect**
> ldapsearch -x -H ldap://192.168.0.200 -b "dc=example,dc=com"
# extended LDIF
#
# LDAPv3
# base <dc=example,dc=com> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# example.com
dn: dc=example,dc=com
objectClass: dcObject
objectClass: organizationalUnit
dc: example
ou: Example Dot Com

# admin, example.com
dn: cn=admin,dc=example,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator

# people, example.com
dn: ou=people,dc=example,dc=com
objectClass: organizationalUnit
ou: people

# groups, example.com
dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups

# lionel, people, example.com
dn: uid=lionel,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: lionel
sn: Porcheron
givenName: Lionel
cn: Lionel Porcheron
displayName: Lionel Porcheron
uidNumber: 1000
gidNumber: 10000
gecos: Lionel Porcheron
loginShell: /bin/bash
homeDirectory: /home/lionel
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
mail: [email]lionel.porcheron@example.com[/email]
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress:
initials: LP

# example, groups, example.com
dn: cn=example,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: example
gidNumber: 10000

# example2, groups, example.com
dn: cn=example2,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: example2
memberUid: lionel
gidNumber: 10001

# search result
search: 2
result: 0 Success

# numResponses: 8
# numEntries: 7

**but getent passwd does not show the user lionel**
> getent passwd | grep lionel
[prints nothing]


I also cannot connect to using the Directory Administrator GUI. It tells me "Invalid Credentials". I'm assuming that's my whole problem... PLEASE HELP!! Thanks.

---

### Post by Sef on 2008-06-22
Moved to Server Platforms.

---

### Post by bluefrog on 2008-06-23
to make a long story short:

change uri ldapi by uri ldap in/etc/ldap.conf

OR (the long story)
on the client side, you need to:
install ldap-auth-client (the easy way, you can do it by hand but obviously you have a problem with that)
use ldap://your-ldap-server-IP/ instead of ldapi:// (this is certainly why your getent fails)

run
sudo auth-config-client -a -p lac_ldap
correct in /etc/ldap.conf "bind_policy hard" to "bind_policy soft"

---

### Post by johnnybeem on 2008-06-23
Sweet got it working. Almost. But now it is giving this when I try to log in at the login screen.

"Cannot set your user group. You will not be able to log in"

Any idea what that means?

---

### Post by bluefrog on 2008-06-24
create a group in ldap and make your user member of it.

---

### Post by johnnybeem on 2008-07-05
Hey, sorry it took me a while to respond. I tried adding the user to the group - not much progress...

Here's some of my output/files... on the client:

```

> getent passwd | grep testuser
testuser:x:1005:10000:Test User:/home/testuser:/bin/bash
> getent group | grep testgroup
testgroup:*:10000:testuser

```

Could it have something to do with the * versus the x?? I don't know what those mean, but in my local users they say x for the user AND for the group (no *)...


On the server (init.ldif file that I loaded into LDAP)

```

dn: dc=example,dc=com
objectClass: dcObject
objectClass: organizationalUnit
dc: example
ou: Example Dot Com

dn: cn=admin,dc=example,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {SSHA}kNv2pDtkihVjQZJkdfc2ugfcunVWAlQi

dn: ou=users,dc=example,dc=com
objectClass: organizationalUnit
ou: users

dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups

dn: uid=testuser,ou=users,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: testuser
sn: Test
givenName: Test
cn: Test User
displayName: Test User
uidNumber: 1005
gidNumber: 10000
userPassword: {SSHA}kNv2pDtkihVjQZJkdfc2ugfcunVWAlQi
loginShell: /bin/bash
homeDirectory: /home/testuser
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: [email]testuser@example.com[/email]

dn: cn=testgroup,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: testgroup
gidNumber: 10000
memberUid: testuser

```

---

### Post by bluefrog on 2008-07-06
should work.

is your testuser the only one with uid 1005?

---

### Post by johnnybeem on 2008-07-06
Yup, testuser is the only one with uid 1005...

So weird, I went to sleep and woke back up again and now it works lol

Probably had something to do with restarting the computer, but I am sure I have tried restarting before and it never worked... Anyways, I'm not complaining :)

Thanks for all your help bluefrog!

---

