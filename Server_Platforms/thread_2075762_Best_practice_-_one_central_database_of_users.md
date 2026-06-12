---
title: "Best practice - one central database of users"
date: 2012-10-24
forum: Server Platforms
---

### Post by flycast on 2012-10-24
If I have multiple servers in different locations on a vLAN but want to manage users on one server and have the other servers get the user info from that central server when an user is added, changed, deleted, etc. what is best practice?

---

### Post by chadk5utc on 2012-10-31
ssh key-based auth between the servers and then setup rsync this way it uses a key for connection security and rsync to copy any changes youve configured to the other servers as needed.

---

### Post by 2F4U on 2012-10-31
What about LDAP? I guess it is the classic solution to tackle problems like yours:

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

To take it a step further, Single-Sign-On may be the thing to look at next:

[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)

---

### Post by SeijiSensei on 2012-11-02
OpenLDAP, RADIUS, and NIS are all possible options.  I think there are also some pam modules that let a Linux machine authenticate against an SQL database.

---

### Post by HermanAB on 2012-11-03
There is no single best solution - it depends on what you as the network admin is comfortable with.  LDAP is used by Microsoft and is very popular, but I never liked it.  So there is the ancient NIS and RADIUS as well.

The newer pam_mysql should be in the repos, but it is not necessarily any better than the others.

---

