---
title: "LDAP configuration and local server user and groups"
date: 2011-04-19
forum: Server Platforms
---

### Post by tlan on 2011-04-19
is it possible to sync ldap users and groups to a local ubuntu server(s).

i have several groups in ldap that can be seen using getent but not in /etc/group on the server or client for that matter.

is there a misconfiguration somewhere that i missed.

at this point i am using pass thru configuration
ex same group and id on client/ldap/localserver

this is NOT the way i want the setup.

TIA

---

### Post by tlan on 2011-04-19
Well it looks like I stumbled on what i was looking for, 
nslcd

---

