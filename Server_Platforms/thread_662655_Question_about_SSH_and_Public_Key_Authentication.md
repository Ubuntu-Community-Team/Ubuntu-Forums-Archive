---
title: "Question about SSH and Public Key Authentication"
date: 2008-01-09
forum: Server Platforms
---

### Post by Caligatio on 2008-01-09
Hello All,

I just started playing around with Ubuntu Server and have Samba and OpenSSH tweaked to my liking.  Currently the server is for my private network at home but I was thinking about poking a hole through my NAT for SSH.

I already have public key authentication working and password logins disabled (overkill, I'm aware).  Admittedly public key authentication is less convenient if I'm traveling around and using different machines that don't have my private key on.  However, I want to make sure that any user that has sudo privileges is required to use public key authentication.

My question is this: is it possible to force users, in the admin group for example, to use public key authentication while other users can use passwords?  Based upon my research, it appears to be a global setting between the two.

Thanks!

---

### Post by Jussi Kukkonen on 2008-01-09
> 
I already have public key authentication working and password logins disabled (overkill, I'm aware).
Not overkill at all. This is smart, especially when it's a multi-user machine -- the probability of at least one idiot with a bad password approaches 1 as amount of users increases... Key-based authentication may be impractical at times, but it's definitely not overkill.

> My question is this: is it possible to force users, in the admin group for example, to use public key authentication while other users can use passwords? Based upon my research, it appears to be a global setting between the two.

I don't think it's possible, except of course by running another sshd with "admin"-settings on another port...

---

### Post by Caligatio on 2008-01-09
Hehe, the only reason I say it's overkill is this is for my home network of 3 users (mom, dad, and my laptop when I come home for various holidays).

I suspected as much about my question but I thought since it seems like a decent idea (and my ideas are usually already taken) that a dev added the functionality.

---

