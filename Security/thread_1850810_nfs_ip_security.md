---
title: "nfs ip security"
date: 2011-09-27
forum: Security
---

### Post by Gatemaze on 2011-09-27
Hi,

I have a NAS system where I am allowing particular shared folders to be accessed by IP. The NAS is in a LAN with more than one users. Wouldn't be possible for one of the users to use the IP of another user and get access to his/her NAS folders? Is there any way to avoid this?

Thanks,
GM

---

### Post by FuturePilot on 2011-09-27
Yes that would be possible. One way around this would be to utilize the way that NFS uses permissions. NFS maps the user on the client to the user on the server. Make the same users on the server without a shell so they can't login on the server, to match the users on the clients. It's important to make sure their UID on the server matches their UID on the client. Then change the ownership of their shared folder on the server to their user. For improved security change the permissions on the root of their shared folder on the server to 700. Finally if you have the "no_root_squash" option in /etc/exports change it to "root_squash" and restart the NFS server process. Now if you have a large amount of users, this is where LDAP would make things a lot easier.

This isn't 100% foolproof, as someone would only need to boot a live CD and create a user with the UID of one of the existing users and get access. Of course you could always disable booting from other media besides the hard drive in the BIOS.

---

### Post by Gatemaze on 2011-09-28
Thanks for the useful answer. :)

---

