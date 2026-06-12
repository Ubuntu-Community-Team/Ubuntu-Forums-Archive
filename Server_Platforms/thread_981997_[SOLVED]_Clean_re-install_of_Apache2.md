---
title: "[SOLVED] Clean re-install of Apache2"
date: 2008-11-14
forum: Server Platforms
---

### Post by Insane_Homer on 2008-11-14
Hi there,

I've been dabbling with the Ubuntu 8.04 server TWiki install from aptitude.

I installed the server with LAMP and then did the Twiki install from the repositories.

However, this TWiki install is old and bugged. But we've already populated it with some data I'd like to migrate.

So I downloaded and installed the latest install for TWiki from Twiki.org however Apache2 settings keep pointing to the old installation of TWiki and not he new one.

In an effort to get it working I've fudged Apache2 rather well,

If it wasn't for the fact I've got some data that needs to be migrated, I'd have just rebuilt the whole thing from scratch and start again.

I've tried 

```
sudo-apt remove apache2
``` 

and then re-install


Ideally all I need is a single new clean install of Apache2. This I can point it to the new TWiki directories via the supplied .conf file and then migrate the old data files across to the new directories as per the TWiki 'upgrade' guide.

How do I remove all the bits of Apache2 of the old one and install it clean from the repository?

---

### Post by oneloveamaru on 2008-11-14
Apache doesn't have a lot of files spread all over the place. The best way to get rid of everything and start clean..

sudo aptitude purge apache2

---

### Post by Deadmode on 2008-11-18
ya```
sudo apt-get remove --purge
```

---

