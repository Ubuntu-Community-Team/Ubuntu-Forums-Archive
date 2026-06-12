---
title: "mod_ruid2 + mod_php threaded - is it stable?"
date: 2013-03-28
forum: Server Platforms
---

### Post by sandyd on 2013-03-28
For a while now, I have been using mod_ruid2 + mod_php (threadsafe) as my php configuration, along with a threaded mpm (event). However, after reading about security bugs in mod_ruid2 like [http://seclists.org/oss-sec/2013/q1/724](http://seclists.org/oss-sec/2013/q1/724), I have been rethinking my position on using mod_ruid2 (I don't really care about my mod_php being threadsafe as I havent had trouble with it yet).

The main reason for me using mod_ruid2 was that all user files/folders could be chmodded 700, and Apache would still be able to access them. Ive thought about moving to mod_fastcgi, which will likely require a chmod of 740, and a owner of *user*:www-data

What I am worried about: If someone compromises apache2, then wouldn't they be able to read the files of all of the users?

Are there any other configurations (please don't mention litespeed) that will allow me to achieve the same level of security as mod_ruid2?

---

