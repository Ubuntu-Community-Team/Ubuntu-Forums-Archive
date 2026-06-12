---
title: "Server and OpenLDap freezes!"
date: 2013-10-10
forum: Server Platforms
---

### Post by miguelpires on 2013-10-10
Hi, 
I've a Zentyal Server (is base in ubuntu 12.04) with this setup:

Gateway, DNS, DHCP LDAP and samba

In the workstations we use Ubuntu 12.04

The autentication against the server is via kerberos, and the /homes of the users and shares from the samba are mounted via pam.

My problem:
Today, a workstation with a connected user completly freezes it self (i can do anything because nothing works like keyboard) soo i've to do a hard reboot. Then that user can't login. In that workstation i loged in with another user, everything was ok, make a logout, try to login in another workstation with the second user, and it starts to suffer from the same symptoms.

Soo I reboot the server, and everithyng works ok. 

What I think that appends are, that, betwen the server and the workstation, something gets stucked and the workstation can't use .config files properly.

Can someone helps me pointing how to debbug this?

Best regards
Miguel

---

