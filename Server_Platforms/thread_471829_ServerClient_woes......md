---
title: "Server/Client woes....."
date: 2007-06-12
forum: Server Platforms
---

### Post by knichel on 2007-06-12
I have been trying (unsuccessfully) for the last few weeks to set my workstations up to authenticate against a server.  Here are the details.  Hopefully someone can help...

I have been using NIS to allow users to authenticate against a server (using 6.06/6.10 on clients) and 7.04 on server (worked with 6.10 also).  When I upgraded my workstations to feisty, this broke.  I am using a theme called kubuntu-list so the users can select their name from a list then enter password.  The list of user accounts shows up, but none can login.

So, using a how-to ([https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28pdc%29%7C%28samba%29](https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28pdc%29%7C%28samba%29)) , I tried to install ldap.  It appears as if the authentication is taking place, but all accounts fail to login.  

If I login using the local admin account for the computer and issue...
ldapsearch -x -D "cn=admin,dc=mydomain,dc=local" -W, I get a list of the users from the server.  So, it seems that ldap is working.

Is there something wrong with PAM or some other authentication modules for Feisty?

I am desparate...

--
Mike

---

