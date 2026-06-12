---
title: "DNS Server problem"
date: 2010-09-03
forum: Server Platforms
---

### Post by noone123 on 2010-09-03
Hi!
I have a Ubuntu Server x64 and for some reasons my Bind server isn't working.
Everything was working fine when suddenly a domain name stopped working.
It's very weird because I have 3 different domains and only one of them stopped working.
Last thing I remembered was that I run 'apt-get update' and 'apt-get upgrade', but didn't see Bind in update list.
How can I check what is wrong?
Domain name seems to be prepaid!

---

### Post by de0xyrib0se on 2010-09-03
> **noone123 said:**
> Hi!
I have a Ubuntu Server x64 and for some reasons my Bind server isn't working.
Everything was working fine when suddenly a domain name stopped working.
It's very weird because I have 3 different domains and only one of them stopped working.


Ok, so BIND is working. Just one of the domains is not configured correctly?

> 
Last thing I remembered was that I run 'apt-get update' and 'apt-get upgrade', but didn't see Bind in update list.
How can I check what is wrong?


Use nslookup to figure out what the server is and isnt answering for.

Are these local or public domains?

Is it a primary server or a secondary receiving updates?

> 
Domain name seems to be prepaid!


What exactly does this mean?

---

### Post by noone123 on 2010-09-03
The thing is that everything was working...
Using online nslookup tools I'm not able to get anything: ** server can't find domain.com: NXDOMAIN

These are public domains.
All 3 domains are on 1 server.

Well it means that I have paid for the domain.

---

### Post by de0xyrib0se on 2010-09-03
Domain name?
Server ip?

---

### Post by noone123 on 2010-09-03
Could I then PM you the address and you could check?

---

### Post by de0xyrib0se on 2010-09-03
Go ahead.

---

### Post by de0xyrib0se on 2010-09-03
I sent you the reply. In case you dont get it;

1. The domain is probably expired, not resolvable from anywhere but your DNS server.
2. Your BIND server is working just fine and is resolving correctly.

Check with your registar to make sure the domain is active.

---

