---
title: "E-mail replication?"
date: 2008-07-21
forum: Server Platforms
---

### Post by Cadmus on 2008-07-21
After a mail server at a friend's workplace failed spectacularly I started thinking. Of the common e-mail servers for Ubuntu are there any that support some form replication such that any failures are transparent.

---

### Post by windependence on 2008-07-21
Many e-mail servers such as Postfix can store their mail in a database such as MySQL or Postgresql. Almost all of these have built in replication support.

If you want to do your own homw grown solution, you can replicate your data with rsync or other tools. The best way would be to set up a cluster and load balance it if you have those requirements.

-Tim

---

### Post by Cadmus on 2008-07-21
Ahhh, so we can guarantee that the e-mail itself is safe using DB replication.

But what about making sure the mail is still received and sent? Can you have two instances of postfix use the same DB?

---

### Post by windependence on 2008-07-21
Well, you could but I wouldn't. I would build 2 identical machines with virtualization, and put the mailserver in one VM and the DB on another on each machine. Replicate them, and set them up so if one fails the other takes off.

-Tim

---

