---
title: "“Terminal Service” style of server but on a Ubuntu"
date: 2006-10-23
forum: Server Platforms
---

### Post by drashman on 2006-10-23
Linux newbie

Just need a bit of an idea on how to set up “Terminal Service” style of server but on a Ubuntu Linux box. I am in university and need to allow students to login from Windows to this box using there ADS credentials and allow them slightly restricted access. If anyone has setup a simular system or can point me in the right direction it would be greatly appreciated.

Thanks

Daniel

---

### Post by kidders on 2006-10-24
Hi there,

I'm assuming the active directory thingy belongs to someone else (your university admins, maybe), but that you can access to it from your Ubuntu box, which is perfect :-)

What you need is to install an SSH server and LDAP-based authentication. That should allow you to authenticate university network users, without knowing their passwords.

---

### Post by tall-male on 2006-10-24
Hi,

Besides the LDAP mentioned before, you could use VNC, in comination with xinetd. VNC is able to query xdmcp, so connecting to the VNC server gives a nice GDM login screen. There's enough VNC-viewers available for windows.
One might take a look at freeNX [http://www.nomachine.com]("http://www.nomachine.com")

---

### Post by merkur2k on 2006-10-24
LTSP probably does what you need. [http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)

---

