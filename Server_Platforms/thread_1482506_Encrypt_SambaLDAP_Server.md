---
title: "Encrypt Samba/LDAP Server?"
date: 2010-05-13
forum: Server Platforms
---

### Post by Redline21 on 2010-05-13
I am setting up a new server that will replace my existing samba server and also function as an LDAP server. I am debating whether or not to encrypt the home directory which is where all the user's files will be stored. I am worried about a performance hit with encryption. 

I am using two 300GB SATA 10K RPM drives in hardware RAID1. The system will probably average anywhere from 50-100 users at a given time. They will mainly be accessing office documents and pdf files. It may also run a small MySQL database for a handful of users.

Security is very important to me, but not at the expense of a noticeable performance loss. Any adivce?

---

### Post by Redline21 on 2010-05-14
I did some searching online, but I can't find any benchmarks relevant to a file server. Unless someone advises otherwise I think I am going to go ahead and encrypt the server. It is a new server and will be faster than the old on anyway, so hopefully that will offset any performance hit from encryption.

---

