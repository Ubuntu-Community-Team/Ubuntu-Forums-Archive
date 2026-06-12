---
title: "Kerberos Questions: It WORKS, but..."
date: 2006-11-24
forum: Server Platforms
---

### Post by charlie. on 2006-11-24
I have "successfully" managed to install and configure a "working" Kerberos 5 KDC and Admin server using Ubuntu 6.06.1 LTS. It runs and I can use kinit to authenticate to it, DNS works in both directions.

Problem 1: It's adde 10 minutes to my server's startup time. The startup sequence sits on "Starting Kerberos Admin Services" and goes no further for ages. I have a nagging feeling that it's waiting for key-presses, because pressing keys is all I can do to make it proceed. The log shows this as "Seeding random number generator". What's up here?

Question 2: Kerberos is up and running and I've managed to install the PAM module for it to test out authentication. Everybody is making a huge noise about LDAP. Why? What will LDAP add to the authentication that kerberos is providing as it is?

Thanks for any help.

---

