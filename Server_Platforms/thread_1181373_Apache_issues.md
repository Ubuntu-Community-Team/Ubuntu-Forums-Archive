---
title: "Apache issues"
date: 2009-06-07
forum: Server Platforms
---

### Post by twistedlndscapes on 2009-06-07
Hello all. I'm making my first post here but this is the millionth time I got help from here :)  Thanks for all the wonderful posts that have helped so far. But I do have one issue I couldn't find a solution for. I had Apache 2.2.11 and Ubuntu 9.04 installed. I just installed PHP5 which appears to read from /var/www but my Apache reads from /usr/local/apache2/htdocs. How do I update PHP so it reads from the same directory by default as Apache? Thanks in advance!

---

### Post by Iowan on 2009-06-07
Might have changed since Hardy... because Apache was set to access /var/www.  [This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") help page explains how to change DocumentRoot.

---

