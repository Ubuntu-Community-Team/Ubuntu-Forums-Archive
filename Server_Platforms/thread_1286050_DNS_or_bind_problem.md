---
title: "DNS or bind problem"
date: 2009-10-08
forum: Server Platforms
---

### Post by matthewboh on 2009-10-08
I've been running a server with DNS and it's been great for a year.  However, I'm now having problems.  I don't know if it's related to a recent password change for my account, but unsure of where to look.

Symptoms - I can get to every box on the network by using IP addresses, but not using their names.

I can get to the Internet with no problem.

I have a series of errors in syslog that repeats about every 3 seconds
```
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 op=1 SRCH base="dc=imparisystems,dc=local" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=mlb))" 
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 op=1 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass 
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 op=2 SRCH base="dc=imparisystems,dc=local" scope=2 deref=0 filter="(&(objectClass=shadowAccount)(uid=mlb))" 
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 op=2 SRCH attr=uid userPassword shadowLastChange shadowMax shadowMin shadowWarning shadowInactive shadowExpire shadowFlag 
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Oct  8 14:10:45 ubuntu slapd[5061]: conn=281 fd=33 closed (connection lost) 

```

If I capture the network traffic, it goes to the correct machine to find the DNS server, but it responds back 

Standard query response, Server failure

Where should I look?  Any help appreciated.

---

### Post by koenn on 2009-10-08
Those syslog entries look like ldap queries to me. Is there any ldpa implementation associated with your DNS ? Active Directory environment maybe ? If so, you might want to elaborate on that.

If not, you'd want to post *DNS *errors from your logs

---

### Post by matthewboh on 2009-10-08
No, no Active Directory and I'm running openLDAP 

The syslog just contains those same entries over and over - about once every 3 seconds

This is the only other errors I could find in any of the logs

```
Oct  8 13:54:10 ubuntu e/webmin/ldap-useradmin/index.cgi: nss_ldap: could not search LDAP server - Server is unavailable
Oct  8 13:54:14 ubuntu e/webmin/ldap-useradmin/edit_user.cgi: nss_ldap: could not search LDAP server - Server is unavailable
Oct  8 13:54:39 ubuntu last message repeated 2 times

```

But I can browse the LDAP using Webmin - I'm baffled!

---

### Post by matthewboh on 2009-10-08
Figured it had to be a problem with BIND DNS, so I searched syslog for named and found the following

```
Oct  8 15:15:24 ubuntu named[4664]: zone 1.168.192.in-addr.arpa/IN: journal rollforward failed: journal out of sync with zone
Oct  8 15:15:24 ubuntu named[4664]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct  8 15:15:24 ubuntu named[4664]: /var/lib/bind/imparisystems.local.hosts:22: TTL set to prior TTL (300)
Oct  8 15:15:24 ubuntu named[4664]: zone imparisystems.local/IN: journal rollforward failed: journal out of sync with zone
O
```

I went ahead, stopped named and deleted the journal files in /var/lib/bind and everything is fixed!

Thanks for the help!  Based on your feedback went and looked for the errors.

---

### Post by koenn on 2009-10-08
good to hear that, 
glad you got things fixed.

---

