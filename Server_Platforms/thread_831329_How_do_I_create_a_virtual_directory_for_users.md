---
title: "How do I create a virtual directory for users?"
date: 2008-06-16
forum: Server Platforms
---

### Post by haryoh on 2008-06-16
Hello, I'm doing a research on how to create a virtual directory for all my users and bind them to my /var/www/publicUsers.
so a user can access his web page and also his files.
Like: user.mydomain.com

Is it possible? and how can i do it?

---

### Post by heebus on 2008-06-17
Create a script that'll add that virtual host when you add a user.  Then you could sym link the /var/www/publicUsers from their home directory.  Each user would need their own v-host.  

An easier and more logical way is here:
[http://ubuntuforums.org/showthread.php?p=81529#post81529](http://ubuntuforums.org/showthread.php?p=81529#post81529)

The users homepage will be [http://server/~User](http://server/~User)

---

### Post by haryoh on 2008-06-18
Thanks. I read the thread and it's really cool. I'll give you an update about the result. thanks.

---

