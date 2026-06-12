---
title: "nss_ldap authentication problem"
date: 2010-03-09
forum: Server Platforms
---

### Post by TwoWordz on 2010-03-09
Hello,

I am trying to get my servers to authenticate with with Active Directory through LDAP. 

I know it's possible to do it using likewise-open, I do not want to use it so please don't mention it. 

I can query the AD server by using ldapsearch to test the communication:

```
ldapsearch -x -D ldapauth -W -H ldap://192.168.1.15 -LLL "(sAMAccountName=some_user)"
Enter LDAP Password:
dn: CN=some_user Lastname,OU=SBSUsers,OU=Users,OU=MyBusiness,DC=example,DC=
 local
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: user
cn: some_user lastname
sn: lastname
...
```

I have PAM setup to use LDAP for authentication using libnss-ldap. When I try to login to the server, this is what I see in /var/log/auth.log:

```
Mar  9 14:34:37 ldap-testing sshd[4111]: nss_ldap: failed to bind to LDAP server ldap://192.168.1.10: Invalid credentials
Mar  9 14:34:37 ldap-testing sshd[4111]: nss_ldap: failed to bind to LDAP server ldap://192.168.1.15: Invalid credentials
Mar  9 14:34:37 ldap-testing sshd[4111]: nss_ldap: could not search LDAP server - Server is unavailable
Mar  9 14:34:37 ldap-testing sshd[4111]: pam_unix(sshd:auth): check pass; user unknown
Mar  9 14:34:37 ldap-testing sshd[4111]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host.example.local
Mar  9 14:34:37 ldap-testing sshd[4111]: pam_ldap: error trying to bind (Invalid credentials)
Mar  9 14:34:38 ldap-testing sshd[4111]: Failed password for invalid user test-user from 192.168.1.46 port 40598 ssh2
```

My ldap.conf has the same user/pass I previously used for the ldapsearch test. I have the password in /etc/ldap.secret. I don't understand what is wrong. 

Is there a way to get more verbose from PAM? 

Also, I do not see the connection attempt in the windows event viewer.

Any idea?

TW

---

### Post by TwoWordz on 2010-03-11
Anyone has nss_ldap authentication working?

TW

---

