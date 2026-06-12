---
title: "ldap client problem nslcd: no available LDAP server found"
date: 2011-05-25
forum: Server Platforms
---

### Post by tonyferrari on 2011-05-25
Hi Everyone,

I'm running Ubuntu 10.04.2 LTS 64-bit
I've configured it to be a LDAP client
I've installed the following packages:
libpam-ldap libnss-ldapd nss-updatedb libnss-db nfs-common nscd ldap-utils

I am able to authenticate to our ldap server, but not always. Occasionally I see this when I run nslcd in debug mode:

nslcd: [9a769b] no available LDAP server found, sleeping 5 seconds

Now after it times out I get authenticated. It does this because I put 'idle_timelimit 5' in the nslcd.conf file. But from a user perspective, it waits, and then authenticates. But sometimes it just logs me in, i.e. the ldap server is immediately reachable. 

I have other cvs clients on the same network, running (Cent OS) sorry, and they don't have this issue.

Anyone have any ideas as to what might be going on? Is this a know issue?

Thanks for your help,

TF

---

