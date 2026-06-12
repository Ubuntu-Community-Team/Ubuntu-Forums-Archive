---
title: "Network-only Email System"
date: 2009-02-02
forum: Server Platforms
---

### Post by Upas on 2009-02-02
I was wondering if there was a way I could setup an email server on a machine to only operate over LAN. (I'm thinking Dovecot and Postfix, with an Apache/PHP/SquirrelMail frontend for the servers running on the same machine)

Lets say I have a server named example.

Is there a way I could setup email just for the LAN so that within the LAN, people can send mail to jdoe@example and have it work?

I'm willing to set up a DNS server if necessary.

If you need clarification, please ask.

Also, for Dovecot/Postfix, does every user need an actual UNIX account on the server?

Thanks in advance.

---

### Post by HermanAB on 2009-02-02
Citadel of course: 
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

It takes about 20 minutes to install and then everything will work.

Cheers,

Herman

---

