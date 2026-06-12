---
title: "Netatalk authorizing with Windows Active Directory Clients"
date: 2014-03-14
forum: Server Platforms
---

### Post by Josh_Stevens on 2014-03-14
We have an Ubuntu server that we intend to use to share videos and other content over AFP to our client Macs. AFP works flawlessly by setting the allow list to one single user. The problem arises when we wish to make use of other users in our Windows Active directory. 

```
~/Videos  "Videos" allow:@activeDirName^Staff-Linux,computeradmin allowed_hosts:192.168.10.0/24,192.168.40.0/24  options:upriv,usedots

```

We have added the Ubuntu server into the Active Directory domain, and users can log in with their usernames via ssh. 

How can we allow all the users in the 'Staff-Linux' active directory group to connect to this share?

Thanks in advance.

---

### Post by Josh_Stevens on 2014-03-17
Bump!

---

