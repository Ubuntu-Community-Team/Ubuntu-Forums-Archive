---
title: "Interface changes back to original IP (ghost in the machine) Edgy Server"
date: 2006-12-21
forum: Server Platforms
---

### Post by frobroj on 2006-12-21
Hi all. I have experienced in multiple installs(bout 11 in all) a very odd occurance. immediately after the Ubuntu Edgy server install  I change the /etc/network/interfaces settings to static entries and then I run /etc/init.d/networking restart. Pretty straight forward. All is well and the ifconfig shows that my new IP is in and the system and is running fine. After about 10 to 20 minutes I lose my netowrk connection to the system. I go directly to it and run ifconfig. Low and behold it has the original dhcp'd address. The /etc/network/interfaces still has the new static settings. It will continue to do this until I restart... 
Bug? Dunno.
Just thought I would share this funny wierdness. Oh and share my frustration becuase I hate to restart a linux box. Its not windows fellas... ;)

---

### Post by Iowan on 2006-12-21
I've read of similar experiences elsewhere.  Check to see if **dhclient** may still be running.  Another thing to try - rename **dhclient.conf**, see if "something" complains.

---

### Post by chrisfay on 2006-12-21
Are you assigning your static IP within the router's DHCP pool you have set?

---

### Post by frobroj on 2006-12-21
> Are you assigning your static IP within the router's DHCP pool you have set?

No I am not.

> I've read of similar experiences elsewhere. Check to see if dhclient may still be running. Another thing to try - rename dhclient.conf, see if "something" complains.

That is one thing I haven't checked. I am about to perform another install. I will give that a try.
Thanks Iowan!
:)

---

### Post by frobroj on 2007-06-07
Issue was resolved. Same IP as another host. Doh! Thanks all for the help...

Can't figure out how to edit the title to say SOLVED or how to close the ticket. Help...

---

