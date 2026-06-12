---
title: "Securing system"
date: 2006-01-24
forum: Server Platforms
---

### Post by jatos on 2006-01-24
Right, I am thinking of running Ubuntu Linux as a web server.  I was wondering, if I have SSH, Apache, FTP and Webmin installed what security precautions should I take. Also their anyway of blocking anyone who makes three incorrect login guess's to any of these services.

---

### Post by alamba on 2006-01-24
I have a similar setup running on a debian server. Here's what I do:
1. Keep webmin down as far as possible, whenever I want to use webmin I ssh and then fire it up.
2. FTP: Rather than this, use SCP. It get's installed with the open-ssh package and works just like FTP however doesn't send your username and password in clear text.

Blocking a user with 3 incorrect login: I do believe you can set this up in PAM. maybe google can help, haven't done it myself.

---

### Post by jimwillsher on 2006-01-24
I try to avoid webmain altogether, preferring to "see" what changes are being made (e.g. do them in a shell and make a note of them!).

I like the idea of SCP though, I must try that.


Jim

---

### Post by alamba on 2006-01-24
I prefer doing it via ssh too jim. However a number of administrators prefer GUI mode. However, I do keep webmin installed just incase I have a time constraint and need to get something fixed asap.

Akshay

---

### Post by xerophyte on 2006-01-27
If you are really concern about your system security might spend some time with this manual 

[http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents)

we use that manual to secure linux host

---

