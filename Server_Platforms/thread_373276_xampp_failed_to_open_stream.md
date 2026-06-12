---
title: "xampp failed to open stream"
date: 2007-03-01
forum: Server Platforms
---

### Post by spacegypsy on 2007-03-01
Hi;

I just installed xampp using [this guide]("http://www.apachefriends.org/en/xampp-linux.html#374").

Everything went ok till STEP 4: Test;

When I type localhost in my browser (firefox) I get:

> Warning: fopen(lang.tmp) [function.fopen]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/lang.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/lang.php:2) in /opt/lampp/htdocs/xampp/lang.php on line 4

I found [this thread]("http://www.apachefriends.org/f/viewtopic.php?t=23158") with the same problem.

There they solved the problem with changing the permissions on htdocs to 777.

How do I do this in Ubuntu?

Will it help me solving my problem?


thx

---

### Post by spacegypsy on 2007-03-01
Problem solved;

I did a mistake when unpacking the rar file.

```
tar xvfz xampp-linux-1.6.tar.gz -C /opt
```

forgot to type xvfz into the command :(

---

