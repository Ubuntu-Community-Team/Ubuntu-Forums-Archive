---
title: "Password/access management servers"
date: 2011-12-28
forum: Security
---

### Post by niels_linux_forum on 2011-12-28
Hey everybody,

I was wondering how you guys manage your server passwords and give access to different people.

At the place I'm working we have several ubuntu instances running, something like 72 I believe.
Now because our server count is running out of control, we are looking for a way to manage secure access to these servers.
For the moment we all access the servers with ssh and pki.

And besides this issue we also have several services running on these servers with there own passwords.

Is there anybody with idea how we can solve this problem? Maybe a software solution available?
Or some personal experiences he wants to share ?

One of my idea's was to setup a ssh with Yubico-pam module, but then I still need a way to manage and distribute the config files.

Maybe an integration with ldap?

I hope you guys have some experience you want to share.

Thanks in advance.

Regards,

Niels

---

### Post by Lars Noodén on 2011-12-28
The first one I would look at would be [Kerberos](https://help.ubuntu.com/community/Kerberos).  It allows centralized management of passwords and is highly secure.  It's designed under the assumption that the network itself is insecure.  There are two variants MIT and Heimdal, but they are both interoperable and fully compatible.

---

### Post by niels_linux_forum on 2011-12-28
Thanks for the fast reply!

I already stumbled on Kerberos, what do you thick of OpenRADIUS.
The problem I keep facing is that not everybody must be able to access all servers.

Is that possible with solutions like Kerberos or OpenRADIUS ?

---

