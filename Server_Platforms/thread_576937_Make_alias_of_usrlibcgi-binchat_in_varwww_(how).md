---
title: "Make alias of /usr/lib/cgi-bin/chat in /var/www (how?)"
date: 2007-10-15
forum: Server Platforms
---

### Post by Xarok on 2007-10-15
I want to run a small chatroom on my site that uses simple cgi scripts, which I have located in the directory /usr/lib/cgi-bin/chat

I've read that in order to have it on my site I should make an alias to my chat scripts in my web root directory.

How can I do this?

Thanks for any help you can give me

Peace

---

### Post by falcon15500 on 2007-10-15
I always get the order of the arguments mixed up, but perhaps:

ln -s /usr/lib/cgi-bin/chat /var/www/chat

falc

---

### Post by Brazen on 2007-10-15
If you look in /etc/apache/sites-available/default
there is already an example of alias-ing in a cgi-bin directory.

---

