---
title: "Bug in setting system-wide ulimits?"
date: 2008-08-26
forum: Server Platforms
---

### Post by alecm3 on 2008-08-26
I am trying to change system-wide ulimits so that the changes survive upon reboot.
This is a very common task in setting up a production server.
Specifically, I am trying to up nofile:

/etc/security/limits.conf :

adding

*     hard    nofile          262144   
 
has no effect upon reboot.
adding

USERNAME             hard    nofile          262144

affects that username upon reboot, as it should.

man limits.conf says:

   
The syntax of the lines is as follows:

       <domain> <type> <item> <value>

       The fields listed above should be filled as follows:

       <domain>

           ·   a username

           ·   a groupname, with @group syntax. This should not be confused with netgroups.

           ·   **the wildcard *, for default entry.**


Is this a known Ubuntu bug?

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

---

