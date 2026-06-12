---
title: "Domain/Directory Controll"
date: 2010-04-24
forum: Server Platforms
---

### Post by motapa on 2010-04-24
I have engaged my students in a server project. They are supposed to install and configure a linux server, not necessarily ubuntu, and provide services on that server. One of the services is that unless a machine is registered on the configure domain, it won't gain access to any other services running on that server(including Internet). The server authenticates its clients before opening up to them.

Now I have looked around and still haven't found anything, but is there software that they can run on the server(, which has a client/agent) that they can install to provide this service. I stumbled upon one Open RSM, but the server software only runs on widows, and I don't want my students to install wine on their project.

Any help?

---

### Post by HermanAB on 2010-04-24
Howdy,

Domain logon for what kind of machines?  Windows?

If you want a Windows domain controller, go to the Samba project web site and read the Official Howto.

If you want Linux domain logon, then read up on NIS, LDAP, PAM MySQL and so forth and pick one.  PAM MySQL is probably the best way to do it nowadays, but many still use LDAP (Windows uses LDAP with Kerberos).

Alternatively, buy the Mandriva Linux business server and go click happy, since it has wizards for everything.

---

### Post by motapa on 2010-04-25
The domain will be Linux based, but it should allow both windows and Linux hosts to log in. I am aware of LDap and Samba. I have plaid around with it, and I liked it. My only concern was that I wanted something of a server/client architcture. Installing the server and deploying the client on hosts. Then configuring the policies on the server. Something that works like OCS, but that isn't only inventory.

---

### Post by HermanAB on 2010-04-25
You need a Samba domain controller.  Read the Official Howto.

---

### Post by motapa on 2010-04-26
Thanks.I will try it out.

---

