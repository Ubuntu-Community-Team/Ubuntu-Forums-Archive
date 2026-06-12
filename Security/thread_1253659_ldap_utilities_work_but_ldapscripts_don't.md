---
title: "ldap utilities work but ldapscripts don't"
date: 2009-08-30
forum: Security
---

### Post by floatingworld on 2009-08-30
I'm trying to set up an LDAP server.  It's a new server (we don't have any existing LDAP server) on Jaunty / 9.04.

I followed the instructions [here]("https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html") and I think that almost everything is working except the ldapscripts.  Using the basic LDAP utilities - ldapadd, for example - and entering the admin password at the prompt works properly.

But when I try adding a user with ldapadduser or adding a group with ldapaddgroup I get "Error adding user X to LDAP" or "Error adding group X to LDAP".  Also, in /var/log/ldapscripts.log the event appears with an additional message "ldap_bind: invalid credentials (49)".

Per the instructions I created and populated and set permissions on the password file /etc/ldapscripts/ldapscripts.passwd with the same admin password that works when I do ldapadd.  I've compared it with /etc/ldapscripts/ldapscripts.passwd.sample and it appears to be correct.

I've also compared the steps I've taken with some slightly more specific instructions [here]("http://andybold.me.uk/2009/07/25/first-steps-with-ldap/") and that seems to check out too.

I get the same failure both sudoing from a normal user account and if I log in as root.  As I'd expect, if I try it as a normal user I get "Unable to read password file..."

So does anyone have a guess as to what I'm doing wrong?

---

### Post by floatingworld on 2009-08-31
It turned out that I had incorrectly set the value for BINDDN in ```
/etc/ldapscripts/ldapscripts.conf
```BINDDN is essentially the user name that will be used to modify the database and should probably look something like ```
cn=admin,dc=example,dc=com
```

---

### Post by ametheus on 2011-02-06
Also, make sure your /etc/ldapscripts/ldapscripts.passwd does not contain a trailing newline. (This is the default behaviour of many editors.)

---

### Post by cariboo on 2011-02-06
Please check the date of a post before replying to it, this thread is over 2 years old and the op may have a found a solution already, or moved on to something else. Closed

---

