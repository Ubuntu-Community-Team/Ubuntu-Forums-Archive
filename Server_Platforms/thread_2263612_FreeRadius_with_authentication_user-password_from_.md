---
title: "FreeRadius with authentication user-password from LDAP"
date: 2015-02-02
forum: Server Platforms
---

### Post by rani2 on 2015-02-02
Hi I'm begginer trying to configure my server with freeradius and ldap
I'll use my LDAP for save user account and password, and I use my free radius to ask authentication via LDAP . . .

Here my LDAP
```
root@ubuntu:~# ldapsearch -x -b "dc=linuxserver,dc=com" "uid=iska"
# extended LDIF
#
# LDAPv3
# base <dc=linuxserver,dc=com> with scope subtree
# filter: uid=iska
# requesting: ALL
#

# Iska Gunarytkyat Fakhry Fakhry, HotspotClient, linuxserver.com
dn: cn=Iska Gunarytkyat Fakhry Fakhry,cn=HotspotClient,dc=linuxserver,dc=com
cn: Iska Gunarytkyat Fakhry Fakhry
givenName: Iska Gunarytkyat Fakhry
gidNumber: 500
homeDirectory: /home/users/iska
sn: Fakhry
loginShell: /bin/sh
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: top
uidNumber: 1000
uid: iska

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
```

and my FreeRadius
```
root@ubuntu:~# radtest iska vermouthandgin localhost 18120 testing123
Sending Access-Request of id 38 to 127.0.0.1 port 1812
        User-Name = "iska"
        User-Password = "vermouthandgin"
        NAS-IP-Address = 127.0.1.1
        NAS-Port = 18120
        Message-Authenticator = 0x00000000000000000000000000000000
rad_recv: Access-Reject packet from host 127.0.0.1 port 1812, id=38, length=20
```

Thanks for your Advance, if you need I to send my configuration file I will , , ,

---

