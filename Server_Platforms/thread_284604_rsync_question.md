---
title: "rsync question"
date: 2006-10-25
forum: Server Platforms
---

### Post by luvdemheels on 2006-10-25
Is there and Easy way to have a server running rsync to only accept rsync connections from certain ip addresses?? Example I have server a and server b and I only want server b to accept any rsync requests/connections from server a.

Thanks.

---

### Post by MJN on 2006-10-26
It depends on how your running rsync on server b i.e. in daemon mode (listening on a TCP port) or run on a adhoc basis over a shell (rsh/ssh).
 
If the former then you can use the **hosts allow** directive in rsyncd.conf to restrict access to a limited set of IP address (server a speifically in this case).
 
If you're running over a shell then I guess you'll need to look at restricting rsh/ssh access to server a - would this be acceptable? If you're using TCP-wrappers then you could put **sshd : ALL **in /etc/hosts.deny and **sshd: server.a.ip.address/255.255.255.255** in /etc/hosts.allow.
 
It might be worth asking why specifically you want to do this? I'm not saying it's a bad idead, more just querying why the inherent security of SSH is not sufficient to protect access to rsync?
 
There are many ways to skin this cat - one common way, given that rsync is often required to run as root in order to backup entire machines, is to only allow SSH connections as root for executing the rsync command only (i.e. no other purpose). We could run through this if required but, perhaps surprisingly, it's rather long-winded and involved - SSH could really do with supporting this functionality with a simple configuration directive!
 
Mathew

---

