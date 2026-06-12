---
title: "What is in package ssl?"
date: 2010-06-04
forum: Server Platforms
---

### Post by leesiulung on 2010-06-04
I ran the following command:

```

sudo apt-get install ssl

```

It is suppose to give me SSL support for Apache 2.2, but I couldn't find any package information about it at [http://packages.ubuntu.com/lucid](http://packages.ubuntu.com/lucid). A search only returns ssl-cert package.

So what is in the ssl package for Lucid 10.04 LTS? 

How do I know what package contains what in the future?

---

### Post by Bachstelze on 2010-06-04
> **leesiulung said:**
> I ran the following command:

```

sudo apt-get install ssl

```

It is suppose to give me SSL support for Apache 2.2

No, it is not. The SSL module for Apache 2.2 is installed by default, you just need to enable it:

```
sudo a2enmod ssl
```

To answer your question, you can view the contents of a package with

```
dpkg -L <packagename>
```

---

### Post by leesiulung on 2010-06-04
I'm embarrassed and I can't believe I did that, but I misread my own directions! You are right, there is no ssl package!

What a waste of my time for being an idiot!

I appreciate your help!

---

