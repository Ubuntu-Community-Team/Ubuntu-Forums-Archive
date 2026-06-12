---
title: "Postfix Rewrite From Address"
date: 2009-05-13
forum: Server Platforms
---

### Post by PJDouglas on 2009-05-13
Hi,

Installed postfix to rewrite the from address before sending all mail to a smarthost.

All mail sent to postfix has a from address of domain.com. I want to rewrite the from address to paul.com before sending the mail to the smarthost.

How do I rewrite the from address so that when the mail is delivered to the smarthost has a from address of paul.com instead of domain.com?

I new to both ubuntu and postfix and would appreciate any help.

I've followed the example's on [www.postfix.org](www.postfix.org) but so far had no luck.

Kind Regards


Paul.

---

### Post by a9k3d on 2009-05-14
You want to create a "sender_canonical" file in /etc/postfix and put something like
```
@fake.localdomain                  @paul.com
```
Anytime you edit a postfix "map" files, like sender_canonical, you have to run postmap on it like this:
**postmap sender_canonical**
Then in /etc/postfix/main.cf add this line:
```
sender_canonical_maps = hash:/etc/postfix/sender_canonical
```
Then run **/etc/init.d/postfix reload** and you should be setup.

---

### Post by PJDouglas on 2009-05-15
Thanks a9k3d,

I was missing the '**postmap sender_canonical' **bit.Although it still doesn't seem to be rewriting the address.

Is there anything else I have missed?


Many Thanks


Paul.

---

