---
title: "Use internal network from putty."
date: 2007-11-21
forum: Server Platforms
---

### Post by itzpapalotl on 2007-11-21
So I am sitting here at home and puttying around inside the new (old really)  Dapper server at  my school. I want to put a Squid proxy and some content filtering services and some stuff on there, and I want to just kind of use it to guard the gates, and keep track of our databases through WAL logging, most critically, I want to do it all from the comfort of my own home rather than driving 15 miles each way to work. 
I have putty access to the server.
What I need to be able to do is talk to the other machines on the network. Map a shared folder or two, transfer some files form one machine to another, that sort of thing. 
Can I do all that from the command line? I thought samba would take care of it, but I cant seem to make it work. Any help would be appreciated.

---

### Post by James79 on 2007-11-21
Who's shares do you want to map, and where? Do you want linux to mount the shares from the clients, or the other way around? 

What OS are the "other" machines using?

Assuming that the other machines are Windows, and you want to mount their shares on from your server, you won't need samba. Google around for "mount cifs". Here's an example:

```
mkdir /mnt/mountpoint
mount -t cifs -o username=xxx,password=xxx  //192.168.0.100/sharename /mnt/mountpoint
```

Where "192.168.0.100" would be the IP of the Windows machine. Once mounted, you'll be able to copy files to and from as if they were local.

---

### Post by netlogic on 2007-11-21
Don't forget that in order to get the full permissions from the server, your gid and uid arguments have to be set based on your permission on the server. If this is the higher level share hierarchy, you might just want to set, "no perm" option. However, no perm has issues too. From "man mount.cifs," 
 noperm 

Client does not do permission checks. This can expose files on this mount to access by other users on the local client system. It is typically only needed when the server  supports  the CIFS  Unix Extensions but the UIDs/GIDs on the client and server system do not match closely enough to allow access by the user doing the mount. Note that this does not affect the  normal  ACL  check on the target machine done by the server software (of the server ACL against the user name provided at mount time).

type "mount.cifs" for all your options.

---

