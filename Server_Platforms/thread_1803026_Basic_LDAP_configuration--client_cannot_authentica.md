---
title: "Basic LDAP configuration--client cannot authenticate"
date: 2011-07-12
forum: Server Platforms
---

### Post by applefat on 2011-07-12
Hi all! I've spent several days trying to set up an Ubuntu 10.04 LDAP server and an Ubuntu 10.04 LDAP client (separate devices on the same local network) to communicate with each other. The idea is for the client to get its authentication information from the server--i.e., someone can log into the client using account details stored in the server. Pretty standard.

I think some of the many problems I've had might stem from the fact that the client is a custom-built embedded platform, so some of the dependencies that every tutorial assume is there is not necessarily installed. 

====================Problem==============================

Anyway, the client CAN retrieve data from the server with ldapsearch. But the problem is that I cannot log in as my test user "aperson". Note that ajmills-desktop is the server hostname.

Here's the suspicious bit from slapd's debug data:
```


=> access_allowed: auth accessccess_allowed: auth access to "uid=aperson,ou=People,dc=ajmills-desktop" "userPassword" requested
=> acl_get: [1] attr userPassword
=> acl_mask: access to entry "uid=aperson,ou=People,dc=ajmills-desktop", attr "userPassword" requested
=> acl_mask: to value by "", (=0)
<= check a_dn_pat: cn=admin,dc=ajmills-desktop
<= check a_dn_pat: anonymous
<= acl_mask: [2] applying auth(=xd) (stop)
<= acl_mask: [2] mask: auth(=xd)
=> slap_access_allowed: auth access granted by auth(=xd)
=> access_allowed: auth access granted by auth(=xd)
send_ldap_result: conn=1000 op=2 p=3
[COLOR="Red"]send_ldap_result: err=49 matched="" text=""[/COLOR]
send_ldap_response: msgid=3 tag=97 err=49
ber_flush2: 14 bytes to sd 13
  0000:  30 0c 02 01 03 61 07 0a  01 31 04 00 04 00         0....a...1....
ldap_write: want=14, written=14
  0000:  30 0c 02 01 03 61 07 0a  01 31 04 00 04 00         0....a...1....
conn=1000 op=2 RESULT tag=97 err=49 text=
daemon: activity on 1 descriptor
daemon: activity on: 13r
daemon: read active on 13
daemon: epoll: listen=7 active_threads=0 tvp=zero
daemon: epoll: listen=8 active_threads=0 tvp=zero


```

I've since discoverd that error 49 means LDAP_INVALID_CREDENTIALS. I assume that means, bad password. But I'm not sure if it's the LDAP Admin's, or the user who is trying to log in.

=================SETUP=====================================

I added a person called "aperson" to the server who I would like to be able to log in as on the client. Here's the results of ldapsearch, which works on **both the server and the client** (this example is the client). You can see that the info for "aperson" comes up. The password for this user is "IamNew2". I've tried entering this into the LDAP server as both plain text and hashed with SHA1 with same results.

```

ubuntu@gumstix:~$ ldapsearch -x
# extended LDIF
#
# LDAPv3
# base <dc=ajmills-desktop> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# ajmills-desktop
dn: dc=ajmills-desktop
objectClass: top
objectClass: dcObject
objectClass: organization
o: My System
dc: ajmills-desktop

# People, ajmills-desktop
dn: ou=People,dc=ajmills-desktop
objectClass: organizationalUnit
objectClass: top
ou: People

# aperson, People, ajmills-desktop
dn: uid=aperson,ou=People,dc=ajmills-desktop
uid: aperson
cn: A. Person
objectClass: account
objectClass: posixAccount
objectClass: top
objectClass: shadowAccount
shadowMax: 99999
shadowWarning: 7
loginShell: /bin/bash
uidNumber: 2001
gidNumber: 100
homeDirectory: /home/aperson
gecos: A. Person
shadowLastChange: 15167

# search result
search: 2
result: 0 Success

# numResponses: 4
# numEntries: 3
ubuntu@gumstix:~$ 



```

Here is /etc/ldap.conf on the client, with all comments removed:

```

base dc=ajmills-desktop
uri ldap://10.67.68.184
ldap_version 3
binddn cn=admin,dc=ajmills-desktop  
bindpw FooBar 
rootbinddn cn=admin,dc=ajmills-desktop
pam_password clear 

```

On the **client** I can actually issue the following command using the admin password, and get the same output (with addition of userPassword being displayed). So the admin password is working. Note that "aperson"s password is also shown, in Base64.

```

ubuntu@gumstix:~$ ldapsearch -xW -D "cn=admin,dc=ajmills-desktop"
Enter LDAP Password: FooBar
# extended LDIF
#
# LDAPv3
# base <dc=ajmills-desktop> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# ajmills-desktop
dn: dc=ajmills-desktop
objectClass: top
objectClass: dcObject
objectClass: organization
o: My System
dc: ajmills-desktop

# People, ajmills-desktop
dn: ou=People,dc=ajmills-desktop
objectClass: organizationalUnit
objectClass: top
ou: People

# aperson, People, ajmills-desktop
dn: uid=aperson,ou=People,dc=ajmills-desktop
uid: aperson
cn: A. Person
objectClass: account
objectClass: posixAccount
objectClass: top
objectClass: shadowAccount
shadowMax: 99999
shadowWarning: 7
loginShell: /bin/bash
uidNumber: 2001
gidNumber: 100
homeDirectory: /home/aperson
gecos: A. Person
shadowLastChange: 15167
userPassword:: SWFtTmV3Mg==

# search result
search: 2
result: 0 Success

# numResponses: 4
# numEntries: 3




```

I'm baffled, I know the two are talking, and I know that the client sends a request to the server when I try to log in. But the authentication always fails. Any ideas on how to narrow down the problem?

Thanks so much

---

### Post by applefat on 2011-07-13
Ok, so I took out the binddn and the bindpw since that's the way it's done in almost every example. But now, of course, the client cannot read userPassword field: 

```

<= acl_mask: [2] applying read(=rscxd) (stop)
<= acl_mask: [2] mask: read(=rscxd)
=> slap_access_allowed: read access granted by read(=rscxd)
=> access_allowed: read access granted by read(=rscxd)
=> access_allowed: result not in cache (userPassword)
=> access_allowed: read access to "uid=aperson,ou=People,dc=ajmills-desktop" "userPassword" requested
=> acl_get: [1] attr userPassword
=> acl_mask: access to entry "uid=aperson,ou=People,dc=ajmills-desktop", attr "userPassword" requested
=> acl_mask: to value by "", (=0)
<= check a_dn_pat: cn=admin,dc=ajmills-desktop
<= check a_dn_pat: anonymous
<= acl_mask: [2] applying auth(=xd) (stop)
<= acl_mask: [2] mask: auth(=xd)
[COLOR="Red"]=> slap_access_allowed: read access denied by auth(=xd)[/COLOR]
=> access_allowed: no more rules
send_search_entry: conn 1000 access to attribute userPassword, value #0 not allowed

```

It should work with anonymous LDAP access. So I guess the the client should be pushing its password to the server for authentication rather than pulling it. But this isn't happening. How am I supposed to change this behavior? Or am I completely misinterpreting what's going on??

---

### Post by applefat on 2011-07-14
Well... I seem to have finally working on my own. So this is for anyone else's benefit.

 Turns out, I think a huge part of the problem was that I was installing libnss-ldap and libpam-ldap, rather than libnss-ldapd and libpam-ldapd which are (inexplicably!!) the packages to install for Ubuntu 10.04+. Otherwise the steps were very similar to what I was doing before.

This tutorial got me where I am:

[http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2)

Follow it ** very carefully and precisely**, it's easy to read through too quickly. If something doesn't work, try purging all the packages and starting over. As in the tutorial I first got the "client" running on the server itself by just connecting to localhost. Then once that worked, I transferred the steps to my actual client. I can't believe how much trouble this has caused me!

---

