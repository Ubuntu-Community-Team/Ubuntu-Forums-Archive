---
title: "AppArmor and ca-certificates"
date: 2008-09-08
forum: Security
---

### Post by QMike on 2008-09-08
Hi all,

I recently struggled setting up slapd with syncrepl replication in Hardy using my own certification authority. I eventually came out it was a problem with apparmor :

As I said, we use our own certificate root authority that I usually put in /usr/share/ca-certificates/myROOT/rootCA.crt after having installed ca-certificates package. Then I just need to add a line in /etc/ca-certificates.conf (and comment out those I do not need) and run update-ca-certificates to have /etc/ssl/certs updated correctly, as well as /etc/ssl/certs/ca-certificates.crt bundle file.

1- is that the correct way to deploy my own root CA ?

Having done that, I tried to set up sync repl using slapd, and then added "TLS_CACERT	/etc/ssl/certs/rootCA.pem" to /etc/ldap/ldap.conf to have my root CA recognized by slapd. The problem is that that file is a symlink to /usr/share/ca-certificates/myROOT/rootCA.crt and it is not allowed by default in /etc/apparmord.d/usr.sbin.slapd, neither in /etc/apparmor.d/abstractions/ssl_certs. I use that file only and not the bundle file since I don't want slapd to recognize any other authority.

I solved the problem by adding "/usr/share/ca-certificates/*/* r," to /etc/apparmor.d/abstractions/ssl_certs so that I don't struggle again with another app protected by apparmor...


2- Shouldn't that line (or a similar one) be included by default in apparmor, or when you install ca-cartificates packages ? You can end up with the same problem, if you want to use one of the certificates from that package, not even a home made one... Maybe there are some security implication I don't see ?

Michael

---

### Post by QMike on 2008-09-08
PS: Ubutun version : 8.04 LTS

---

