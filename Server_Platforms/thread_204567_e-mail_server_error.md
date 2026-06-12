---
title: "e-mail server error"
date: 2006-06-27
forum: Server Platforms
---

### Post by renaissance on 2006-06-27
Transaction failed
Server replied: 554 : Relay access denied

I use Postfix MTA and Dovecot.

---

### Post by MJN on 2006-06-27
And? Nothing wrong with that - it's refusing an unauthorised user to relay to a 3rd party exactly as designed.
 
It might help if you say what actions resulted in this error, why you weren't expecting it and what you want it to do. A copy of /etc/postfix/main.cf would be of benefit too.
 
Mathew

---

