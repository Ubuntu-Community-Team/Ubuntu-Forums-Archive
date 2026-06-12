---
title: "Trying to set up a Linux Network"
date: 2010-10-02
forum: Server Platforms
---

### Post by Maineac54 on 2010-10-02
I have a Linux Server I built running Debian Lenny.  I have LDAP, SAMBA, PAM, NSS and SASL all running on the server.  I have the firewall disabled at the moment.

I would like to use this server to provide a common user space for a number of different clients.

The first client I am trying to connect is a Linux Laptop running Ubuntu 10.4.  I would like to use single sign on (SSO) .  Both machines are connected to the same router, IP addresses are 192.168.1.4 (laptop) and 192.168.1.10 (server).

The server is configured as PDC and DNS.

What do I need on the Ubuntu laptop to be able to join the domain and use my LDAP logon?

What are the commands or where can I find them?  Every search I have done only finds instructions for how to set up LDAP, SAMBA, etc.  I haven't been able to find anything on how to join the domain once it's set up.

HELP!!   plz :P

---

