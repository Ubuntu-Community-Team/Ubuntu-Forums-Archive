---
title: "Cannot make LTSP boot clients login via LDAP"
date: 2009-10-28
forum: Server Platforms
---

### Post by tarekeldeeb on 2009-10-28
Hello all,

I have a problem, let me tell what I did till now:

- Install Alternate-CD with LTSP Server mode
- ltsp-build-client, this made a thin client. It works perfect, but each client takes about 200 MB of Ram from my server, which is not acceptable. I made a Fat client according to [https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients](https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients) (using the steps, not the provided link)
- Installed a NFS and LDAP server side packages (following: [http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2](http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2))

Client boots till it reaches the login screen GDM (not LDM as the thin client). The problem arises here. Whenever I try to login, enter user, then password, it displays: "User not known to the underlying Authenticating module"
The message is displayed even when I enter wrong usr/pass 

How can I test if the LDAP server works properly? Can I emulate a fake login and see the result?

How can I check the client can access the LDAP server correctly?

Please help.

---

### Post by Ryan-sd63 on 2009-10-28
Perhaps you did this, but didn't mention it, but have you configured an LDAP server to allow you to authenticate against it?

---

### Post by tarekeldeeb on 2009-10-28
> **Ryan-sd63 said:**
> Perhaps you did this, but didn't mention it, but have you configured an LDAP server to allow you to authenticate against it?

I really don't know what do you mean.
I think it could be my missing part ..
can you please clarify ..:o

---

### Post by Ryan-sd63 on 2009-10-29
> **tarekeldeeb said:**
> I really don't know what do you mean.
I think it could be my missing part ..
can you please clarify ..:o

Before you can use LDAP to authenticate, you have to setup your LDAP server and create accounts. It's a non-trivial task.

There's a guide here: [http://www.linux.com/archive/feature/114074](http://www.linux.com/archive/feature/114074)

---

