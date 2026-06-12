---
title: "how to install cetificate authority in ubuntu?"
date: 2011-08-03
forum: Server Platforms
---

### Post by figo2476 on 2011-08-03
Hi,

* Correct me if I am wrong.

* In web browser, if I go to a SSL site, I need to install a CA from the SSL site, so the web browser trusts it.

* I assume my ubuntu box is working the same way.

* That is if I need to do ldap bind or search, I need to install the CA and put it in /etc/ldap/ldap.conf

* It works well, if I only have 1 CA in ldap.conf. 

* If I put 2 CAs in ldap.conf, only the last one will work. e.g.

BASE dc=a,dc=b,dc=c,dc=d 
URI ldaps://somesite.com
TLS_REQCERT demand
TLS_CACERT /etc/ssl/certs/1.cert

BASE ou=e,o=f
URI ldaps://somesite1.com
TLS_REQCERT demand 
TLS_CACERT /etc/ssl/certs/2.cert

I need to know how to put 2 CAs in ldap.conf

---

### Post by hawkmage on 2011-08-04
Are you using OpenLDAP?

The file that the TLS_CACERT parameter points to can have multiple CA certificates in in.  

Here is a URL to the OpenLDAP config files: 
[5.2.1 LDAP Client Configuration Directives]("http://www.openldap.org/pub/ksoper/OpenLDAP_TLS.html#5.2.1")

---

### Post by figo2476 on 2011-08-04
@hawkmage, there is something I don't understand, so I need to tell you what I try to achieve.

* Basically, I have a php script to query 2 different third party ldaps servers.
* So I need to know how to install them. 

* The following doesn't work for me in ldap.conf
BASE dc=site1,dc=site1,dc=site1,dc=site1 ou=site2,o=site2
URI ldaps://site1.com ldaps://site2.com
TLS_REQCERT demand
TLS_CACERT /etc/ssl/certs/site1.cert /etc/ssl/certs/site2.cert

---

### Post by WhiteHorse on 2011-08-04
Try this:
man ldap.conf

---

### Post by figo2476 on 2011-08-04
* @WhiteHorse, I have looked at the man page.
* Perhaps I miss something, I still don't know how to put 2 different bases together.
* I wonder whether that is possible or not.

---

