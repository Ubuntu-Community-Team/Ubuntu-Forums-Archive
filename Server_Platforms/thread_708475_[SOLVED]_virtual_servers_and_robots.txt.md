---
title: "[SOLVED] virtual servers and robots.txt"
date: 2008-02-26
forum: Server Platforms
---

### Post by rbprogrammer on 2008-02-26
basically i have a server running with dyndns.org hostnames pointing to my servers IP,  my question is:

i have a few virtual servers running within apache2, do i need a /robots.txt file in each of the virtual servers root directory??  the default server has this:
```

# /robots.txt
User-agent: *
Disallow: /

```

my guess is that it wont, i would like to have different robots.txt files for each virtual server.  basically disallow everything but on some servers allow the robots to cache/index/whatever they do, certain directories.  i can figure out that part, but again, i would need robot files for each server, right??

---

### Post by rapiscan on 2008-02-26
Yes, place the robots.txt file at the web root for each of your virtual servers.  The bots that traverse your domains will look there, it is irrelevant to the bot that you have multiple websites on the same server.

---

### Post by faulkes on 2008-02-26
Correct.

For each server you require a specific robots.txt file, especially if each file will
define what content should or should not be indexed.

Faulkes

---

### Post by rbprogrammer on 2008-02-27
yup that seems like the logical thing to do, thanks...

---

