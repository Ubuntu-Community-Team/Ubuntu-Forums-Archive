---
title: "Active Directory Authentication"
date: 2012-03-26
forum: Security
---

### Post by bbazian on 2012-03-26
I have several 10.04 servers that I have integrated into AD on a Windows 2003 Domain. All appears to work well but intermittently I will have issues using domain credentials to log into the server. A reboot for the Ubuntu server fixes the issue till the next time it happens. For some reason it is losing its connection to AD and the reboot fixes it. 
 
When I can not authenticate against the domain I can log in with local credentials and when executing a wbinfo -g or wbinfo -u I see all of the objects to AD so they are communicating.
 
 
Any ideas on how to fix this or at least what I need to look at to see what is happening?

---

### Post by HermanAB on 2012-03-26
Howdy,

You need to investigate the problem from the command line, in order to see ht e error messages.

This may help:
[http://www.aeronetworks.ca/howtos/LinuxActiveDirectory.html](http://www.aeronetworks.ca/howtos/LinuxActiveDirectory.html)

From para 3.5 onwards.

---

