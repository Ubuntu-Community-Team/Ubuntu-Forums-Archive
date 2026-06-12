---
title: "OpenLDAP over TLS/SSL"
date: 2012-06-05
forum: Server Platforms
---

### Post by kennethconn on 2012-06-05
And so it continues...
 
I am trying to get OpenLDAP configured with TLS (using openssl as opposed to certtool for certificates using own CA). The problem seems to be with not being able to read the files (although I have changed ownership of files to openldap and also given full permissions to everyone in attempts to get this to work).
 
While searching I came accross a post that said to try
 
su - openldap -s /bin/bash -c 'openssl x509 -noout -subject -in 
/etc/ldap/ssl/newcert.pem'
 
Prior to this command, when I try this command as sudo:
 
sudo -s /bin/bash -c 'openssl x509 -noout -subject -in 
/etc/ldap/ssl/newcert.pem'
 
I get output (details of CN, OU etc). However running the command as the ldap user (openldap), I get prompted for a password (which I had to set up), and once correct password is entered, I get no output, just back to the prompt (I get an authenticate failure message if I try incorrect password). So OpenLDAP seems to have a problem reading the cert files, and that is why there is a problem with TLS setup, I think. I have also copied files into /etc/ldap and changed ownership of same to openldap, still no luck.
 
Any ideas how I can get openldap server account to read the cert files? Any other suggestions on what to try next?

---

