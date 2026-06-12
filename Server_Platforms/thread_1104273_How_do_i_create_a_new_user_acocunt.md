---
title: "How do i create a new user acocunt?"
date: 2009-03-23
forum: Server Platforms
---

### Post by BradleyAtkins on 2009-03-23
Hi all

How do I create a new user account in Server edition 8.10?

I have tried: -

useradd -c Guest -d /home/guest -g admin -m -p welcome -s /bin/ksh guest

This seems to create the account but the password is not accepted. The man page says the password should be as returned by crypt (3) but I have no man entry for crypt or anything shown by "which crypt".

I want to create a spare account with sudo rights so I can get myself out of trouble if I screw up my account login while teaching myself Linux administration.

Cheers

Brad

---

### Post by hictio on 2009-03-23
You might create the account first, and then, set a password for that account:

```

sudo passwd username.here ENTER

```

It'll ask for the password twice.

---

### Post by BradleyAtkins on 2009-03-23
:D Cheers that did it

---

