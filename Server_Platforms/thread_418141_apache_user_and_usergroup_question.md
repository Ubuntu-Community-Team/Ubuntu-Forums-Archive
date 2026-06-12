---
title: "apache: user and usergroup question"
date: 2007-04-22
forum: Server Platforms
---

### Post by mephisto56 on 2007-04-22
Something I don't understand. I though apache used the www-data user/group. But the directory /var/www is owned by root. How is apache able to write to the /var/www directory if it isn't in the root group?

---

### Post by jtc on 2007-04-22
It isn't.

---

### Post by mephisto56 on 2007-04-22
Let's say I create a file there through a php script, or a directory. Won't that cause any problems then?

---

### Post by jtc on 2007-04-22
It will.

In such a scenario the directory in question needs to be somehow be writable by your apache user, which in this case is www-data. One way to accomplish this is to set www-data as owner of the directory. Another one is make the directory in question globally writable. No matter the method, I'd say it's preferred to use a subdirectory instead of the Documentroot (ie: /var/www).

A diffrent approach is having your php scripts run as the user who owns them. That has the advantages of giving you a better flexibility of the directory ownerships. If you want your php scripts to run as their owner I'd suggest a look at suPHP.

---

