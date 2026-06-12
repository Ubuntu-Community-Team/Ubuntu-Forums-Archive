---
title: "domain controller question"
date: 2007-08-17
forum: Server Platforms
---

### Post by neill on 2007-08-17
hi

i want to use an ubuntu server as a primary domain controller with full roaming profiles etc etc, but i need to host the actual /homes of the users on a different machine

i've done this sort of thing before but always with all the data on the same box as the PDC and with the users all having accounts on the server

in this case the PDC will be a very lightweight box and all the user data will be stored on a domain aware NAS. the users will have no need (in fact i don't want them to) access the PDC but when they logon their /home on the NAS should be mapped exactly as it would have been if the data was on the PDC

is that possible :confused:

/neill

---

### Post by iskatyel on 2007-08-28
I don't know if it's possible, but I would probably try mounting the NAS volume on your PDC and then pointing the path directive for the profiles share to the mount point and see if it works.  Let us know how this turns out.

---

### Post by toupeiro on 2007-08-28
What kind of a domain is this?  If its unix/linux only, just setup an NIS server.

[http://www.linux-nis.org/nis-howto/HOWTO/ypserv.html](http://www.linux-nis.org/nis-howto/HOWTO/ypserv.html)

pretty standard no matter which OS you are running. 

Set a netgroup which will include all machines in your domain, then on a NAS export of some kind of export, set rw=@yournetgrouphere and use that export for your home directories.  assign your permissions as needed.

for your workstations, you can configure a service like AMD ) automounter Daemon to control your dynamic home directory mounting.

you should be able to get ample google help for the specifics of AMD and your yp services.

---

