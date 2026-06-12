---
title: "Maximum simultaneous connections to a share"
date: 2014-07-15
forum: Server Platforms
---

### Post by drakuel on 2014-07-15
Please could someone tell me if there is a maximum number of simultaneous connections to a share on an ubuntu server system, 14.04. I know on a windows pc there is a limit of about 25 connections to a shared folder (I think), but is there such a limit on a linux server? I need to be able to have upto 60 users access a share on a linux server simultaneously.

---

### Post by lukeiamyourfather on 2014-07-15
Windows Server uses what they call a CAL, client access license, and it needs one for each connected user. Ubuntu Server doesn't have any licensing restrictions like that so you can have as many connected users as the hardware is capable of handling.

---

### Post by TheFu on 2014-07-17
> **lukeiamyourfather said:**
> Windows Server uses what they call a CAL, client access license, and it needs one for each connected user. Ubuntu Server doesn't have any licensing restrictions like that so you can have as many connected users as the hardware is capable of handling.

Exactly.  I've seen CIFS servers handle 500+ clients and NFS servers over 1,000.  The samba CIFS implementation is really very efficient.  It will really be an issue for disk and network I/O before client connection counts get in the way.

---

### Post by klonengan on 2014-11-18
What about if I want to use (on my server machine) Ubuntu Client instead of Ubuntu Server? Will I still be able to get the unlimited restriction?

(please respond to my email [email]klonengan@outlook.com[/email] too, thanks)

---

### Post by lukeiamyourfather on 2014-11-18
> **klonengan said:**
> What about if I want to use (on my server machine) Ubuntu Client instead of Ubuntu Server? Will I still be able to get the unlimited restriction?

There's no difference between the Samba packages for the Ubuntu Desktop release and the Ubuntu Server release. Neither platform has restrictions on the number of simultaneous connections. Windows cripples the number of concurrent connections purely for licensing purposes (more connections means more money). However that isn't the case with Ubuntu or any other Linux distribution that I'm aware of.

> **klonengan said:**
> (please respond to my email [email]klonengan@outlook.com[/email] too, thanks)

Please subscribe to the thread so you get email notifications. It's not reasonable to expect people to reply directly by email. Also it defeats the purpose of using a forum because the forum acts as a constantly expanding knowledge base. If we all just private messaged and emailed each other then nobody else would be able to benefit from the knowledge and discussion.

---

