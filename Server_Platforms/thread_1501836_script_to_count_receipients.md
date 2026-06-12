---
title: "script to count receipients"
date: 2010-06-04
forum: Server Platforms
---

### Post by dtech on 2010-06-04
Hi,

I want to protect the mailinglists from my fraternity from so-called "CC-spam": internal groups adressing a lot of receipts for their promotions.

To do so I want to put a script in /etc/aliases. A entry would change from:
```

mailinglistname: "|/usr/lib/ecartis/ecartis -s mailinglistname"

```
to
```

mailinglistname: "/root/bin/processMailingList.sh mailinglistname"

```

But I have one problem: I cannot figure out how to count the number of receipts in a bash script. Can anyone help me?

---

### Post by zpletan on 2010-06-04
I don't know too much about what you are trying to do, but I know how to use bash quite well (if I say so myself).  Can you please post an example of the content that you would be trying to parse?

---

