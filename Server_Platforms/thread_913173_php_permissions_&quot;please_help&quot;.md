---
title: "php permissions &quot;please help&quot;"
date: 2008-09-07
forum: Server Platforms
---

### Post by emadwilliam on 2008-09-07
How to execute commands from php with "some different user" as its owner ?

So that when I type in php (exec 'cd ~ \n ls'; ) it lists the files in the home directory of the user who logged on from the webpage not the files in "/var/www".

---

### Post by onlivimal on 2008-09-07
I had already replied in the other thread...
neway the following code should solve your issue...

exec 'cd /var/www \n ls';

---

