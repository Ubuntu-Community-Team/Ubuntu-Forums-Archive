---
title: "LDAP authentication using nss_base_passwd + memberOf attribute?"
date: 2011-11-22
forum: Server Platforms
---

### Post by pbeckhelm on 2011-11-22
Greetings, 
I'm having some difficulty in getting authentication working properly in my LDAP deployment.  What I want to do is restrict authentication on a particular host to the members of a group (groupOfNames, actually).  I've found a number of articles that describe this in some detail, but using those configs hasn't gotten me where I want to be. 

My /etc/ldap.conf has nss_base_passwd set like so: 

nss_base_passwd ou=people,dc=example,dc=com?one?memberOf=cn=sysadmin,ou=groups,dc=example,dc=com 

...shadow and group are similar, but leave out the memberOf filter. 

The good folks at CERN have a site that explains this ([http://linux.web.cern.ch/linux/docs/account-mgmt.shtml](http://linux.web.cern.ch/linux/docs/account-mgmt.shtml)), and I've got mine configured very similarly (Theirs is in the "Filtering the results" section): 

nss_base_passwd OU=Users,OU=Organic Units,DC=cern,DC=ch?one?memberOf=CN=lxsoft-admins,OU=e-groups,OU=Workgroups,DC=cern,DC=ch 

Checking the LDAP directory for the uid=exampleuser, looking for the memberOf attribute, we get a hit: 

root@ldap01:/var/tmp# ldapsearch -xLLL -D cn=admin,dc=example,dc=com -h localhost -b "dc=example,dc=com" -W uid=exampleuser memberOf 
dn: uid=exampleuser,ou=people,dc=example,dc=com 
memberOf: cn=sysadmin,ou=groups,dc=example,dc=com 

...as well, just looking for the DN's that meet the intended filter:

root@ldap01:/etc/ldap/schema# ldapsearch -xLLL -D cn=admin,dc=example,dc=com -h localhost -b "dc=example,dc=com" -W "&memberOf=cn=sysadmin,ou=groups,dc=example,dc=com))" dn

dn: uid=pbeckhelm,ou=people,dc=example,dc=com

So, the memberOf overlay is working properly, it seems. 

When I attempt to authenticate via ssh, the LDAP client node reports 
these errors: 

Nov 21 15:15:27 vmdns01 sshd[8977]: Invalid user exampleuser from 192.168.21.64 
Nov 21 15:15:27 vmdns01 sshd[8977]: Failed none for invalid user exampleuser from 192.168.21.64 port 56344 ssh2 
Nov 21 15:15:29 vmdns01 sshd[8977]: pam_unix(sshd:auth): check pass; user unknown 
Nov 21 15:15:29 vmdns01 sshd[8977]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.21.64 
Nov 21 15:15:30 vmdns01 sshd[8977]: Failed password for invalid user example user from 192.168.21.64 port 56344 ssh2 

If I broaden the filter in /etc/ldap.conf, or leave it out entirely, my authentication succeeds.  My primary goal in getting this working is to restrict login access to only those members of groups that I specify (cn=sysadmin, in this case). 

So, has anyone been able to get this to work?

I'm happy to help paint the picture more clearly. 

Cheers, 

pb

---

