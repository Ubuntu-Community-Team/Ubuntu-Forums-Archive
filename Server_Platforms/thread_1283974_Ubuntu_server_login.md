---
title: "Ubuntu server login"
date: 2009-10-06
forum: Server Platforms
---

### Post by Dzingis on 2009-10-06
After few weeks of investigating and Googling I need to ask :)

Here is scenario:

1. Ubuntu 9.04 server.
2. Few XP stations, few linux stations

Idea.

Keep profiles and documents of all user on the server.

With windows and samba it's not a problem, but how to accomplish it with Linux?

Is linux server capable of authenticating users (users are not locally created) from server and auto mounting of home directory?

Shorter.

1. User logs on linux box
2. It's authenticated on server
3. Home directory is automonted.

Please, if answer is so obvious don't lough. :lolflag: 

Thx

---

### Post by Dzingis on 2009-10-06
God thing with posting question is that you few minutes later figure out the solution on your own :)

Is LDAP with PAM everything I need? 

Any good HOWTO except: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

---

### Post by Iowan on 2009-10-06
Have you seen the server help pager?
[https://help.ubuntu.com/community/OpenLDAPServer]("https://help.ubuntu.com/community/OpenLDAPServer")
[https://help.ubuntu.com/8.04/serverguide/C/openldap-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openldap-server.html")

---

### Post by Dzingis on 2009-10-07
> **Iowan said:**
> Have you seen the server help pager?
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
[https://help.ubuntu.com/8.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.04/serverguide/C/openldap-server.html)

Thx, I also found 

[http://sanjaybdalal.wordpress.com/2009/06/23/setup-openldap-serversambaauto-mount-in-ubuntu-9-04/](http://sanjaybdalal.wordpress.com/2009/06/23/setup-openldap-serversambaauto-mount-in-ubuntu-9-04/)

It's dealing also with a client side on Linux and Windows machine.

---

