---
title: "Mailman new list"
date: 2007-12-10
forum: Server Platforms
---

### Post by poisonmushroom on 2007-12-10
Hello, i have followed the tutorial on 
```
https://help.ubuntu.com/7.10/server/C/mailman.html
```

I reached to the point where i have to create a new mail list using this command:

```
sudo /usr/sbin/newlist mailman
```

It asked for the list name, i typed: mail
then asked for the email of the owner, i typed: [email]admin@mushroom.com[/email]
then asked for a password, and i typed it.

Then it gives me a big help file with this text in the end:

```
The list admin address need to be a fully-qualified address, like
owner@example.com, not just owner.

Illegal list name: mail@localhost
```

Why is it giving me an illegal list name? i never wrote @localhost, i even tried with other things like [email]mushroom@mushroom.com[/email] but it always tells me "whateveriwrote@localhost.com" is illegal.

---

