---
title: "Site asking me if I wanted to save &quot;index.php&quot;"
date: 2010-10-19
forum: Server Platforms
---

### Post by xebedee on 2010-10-19
To put my problem simply - 

If I go to a virtual host it asks me if I want to save "index.php"

(Typing in the host name followed by index.php also works).

But if I go the main site it does not.

This happened after an upgrade to Ubuntu 10.04

Here are some additional details -
[INDENT] apachectl -M shows rewrite_module (shared)

the host config file has AllowOverride All

the dir and php5 modules are loading fine.
[/INDENT]Any ideas would be greatly appreciated.
(I previously posted this under another heading)

---

### Post by arrrghhh on 2010-10-19
[ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) - see the section on "Troubleshooting PHP 5"

---

