---
title: "does desktopcouch automatically sync with ubuntuone?"
date: 2010-02-27
forum: Ubuntu One (CLOSED)
---

### Post by cometdog on 2010-02-27
Hi folks,

I'm playing around with quickly a little bit, and was just experimenting with putting a CouchGrid into an application.  It's kind of amazing how easy it is to get structured, persistent data by doing that.

But I would like to understand a little more about the synchronization with UbuntuOne.  It has been mentioned here and there that there are hooks in UbuntuOne to synchronize particular apps across different computers, using desktopcouch.  That's great and all, but I am actually concerned a bit about data security.

Does anyone know -- if I am working on a computer where I have UbuntuOne enabled, and where I'm using the free 2GB UbuntuOne account, and I write a quickly app that stores some information using desktopcouch; does that information automatically make its way to Canonical's servers?  I'm really hoping that the answer is no, and that I would explicitly have to choose to enable some kind of synchronization with the UbuntuOne cloud.  But it's really not clear yet from anything I've looked at.

Thanks!

---

### Post by duanedesign on 2010-02-28
You can specify particular databases that you do not want to replicate: look in your management database, and find the record that describes the pairing with Ubuntu One 

```
http://localhost:PORT/_utils/database.html?management/_design/ubuntu_one_pair_record
```

If you add a key "excluded_names" to that record, and make its value a JSON list of database names ( [ "db1", "db2", "db3" ] ), those names will not be replicated.

---

