---
title: "Setting up user network"
date: 2007-06-05
forum: Server Platforms
---

### Post by TorchlightJay on 2007-06-05
Okay, so I want to set up a users on my network but am not sure how to do it. Basically rather than setting up users on each individual computer, I want to have the users on a server and they can log into the server via the computers/terminals. Is there an efficient way to do this with an Ubuntu server? How would I secure it? How would i setup the servers and terminals? Maybe there's a way to set up individal users on the computers and manage them from the server? Please help!

---

### Post by turinglabs on 2007-06-05
OpenLDAP will work, as will NIS or Kerberos. A decent guide to the OpenLDAP server and client setup links:

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

---

