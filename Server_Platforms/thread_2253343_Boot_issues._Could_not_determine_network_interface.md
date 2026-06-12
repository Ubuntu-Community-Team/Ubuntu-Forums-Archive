---
title: "Boot issues. Could not determine network interfaces"
date: 2014-11-19
forum: Server Platforms
---

### Post by dalsim on 2014-11-19
Hi everybody.

I have a problem with my ubuntu install. Everything was running fine till we had a storm come through and the UPS decided to give out. Now my Ubuntu server won't start up and is getting stuck on "ERROR: Could not determine network interfaces, you must use a interfaces config line". The server in question is my file server which is running samba. From googling about I get the idea that it is a smbd issue but I can't figure out how to fix it. Or what I have read presumes that I can boot into ubuntu, but I can not get past this error (pic attached). 

Thanks in advance for any help on this.

Jeff

---

### Post by slickymaster on 2014-11-19
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Jonathan L on 2014-11-19
Hi Dalsim

It's just a guess, but perhaps your network interface is faulty and not being auto-detected, and the first thing which really complains is Samba.  My suggestion would be to try to bring the system up single-user and see if you can get the ethernet interface to work (with ifconfig, ping and so on).  Or at least rule it out.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by dalsim on 2014-11-19
Hi Jonathan,

It was indeed samba no longer auto detecting the network interface, both of them. I ended up having to pull the hdd and mount it on another pc and modify the /etc/samba/samba.conf file and include "interfaces = ip address/netmask" , remounted in the server and started it up. I have no idea what caused that to happen but it is working now. 

Thanks for the help.

---

