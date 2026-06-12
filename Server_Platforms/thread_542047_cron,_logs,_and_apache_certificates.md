---
title: "cron, logs, and apache certificates"
date: 2007-09-03
forum: Server Platforms
---

### Post by psyncho on 2007-09-03
I have apache serving a certificate that is password protected for port 443 or encrypted web traffic. This works great. The problem is, when cron tries to rotate the logs (I think on cron.weekly), it restarts apache, can't enter the certificate password, and so apache never comes back up.

Thus, I wander along and find that my webserver goes down weekly.

I'm wondering, is there a way around this without stripping the password out of my certificate? 

On that note, I've read a bunch on why having the certificate password protected is so great, but I'm not sure I really understand why. Someone could grab it and then use it and act like you? I only use it for my web server, so that means someone could do a man in the middle attack? Am I missing something?

thanks,
John

---

### Post by psyncho on 2007-10-07
With no response, I simply stripped the password out of my certificate. 

I'd like to better understand the security risks of this if anyone felt like enlightening me. 

The only thin I can think of is that if someone hacked into my machine they could then grab my certificate and use it, which is of course bad, but if someone got into my machine the game is pretty much over already for me. (and can't you always revoke certificates?)

The only other guess I have is that someone could some how grab your private key from the certificate, ...so I guess I'm just stripping out the password protection on the password with private key. I forget this stuff as fast as I learn it.

oh well...good luck to anyone else facing a similar problem.

---

### Post by MJN on 2007-10-07
> **psyncho said:**
> With no response, I simply stripped the password out of my certificate.

Sorry about that - it's quite a common issue so I'm surprised noone (me included) didn't pick up the thread.

For what it's worth you took what is arguably the only realistic option.

> I'd like to better understand the security risks of this if anyone felt like enlightening me. 

The only thin I can think of is that if someone hacked into my machine they could then grab my certificate and use it, which is of course bad, but if someone got into my machine the game is pretty much over already for me.

That's right - your certificate (or rather your private key) is only as secure as how protected it is and in removing its encryption you've just peeled a layer off that. However, as you say, if someone has cracked your machine - with root privileges - then it can indeed be considered game over.

> (and can't you always revoke certificates?)

Yes, whoever signed your certificate can (in theory at least) revoke your certificate although the effectiveness of this depends on whether the certificate revocation list (CRL) for your signing authority is checked by clients (many don't do this).

If your certificate was self-signed then it'd be down to you to revoke the certificate (but it's likely you wouldn't be publishing a CRL anyway for anyone to check).

> The only other guess I have is that someone could some how grab your private key from the certificate, ...so I guess I'm just stripping out the password protection on the password with private key. I forget this stuff as fast as I learn it.

That is correct - it is the private key that is encrypted, not the certificate.

In case it's not already, make sure your private key is owned, and only readable, by root.

Mathew

---

