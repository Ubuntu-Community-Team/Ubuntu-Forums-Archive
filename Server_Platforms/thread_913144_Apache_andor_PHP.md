---
title: "Apache and/or PHP"
date: 2008-09-07
forum: Server Platforms
---

### Post by emadwilliam on 2008-09-07
How to execute commands from php with "some different user" as its owner ?

So that when I type in php (exec 'cd ~ \n ls'; ) it lists the files in the home directory of the user who logged on from the webpage not the files in "/var/www".

---

### Post by onlivimal on 2008-09-07
try to go to the command line, and type 'cd ~', 'pwd' and then 'ls'. do it one by one and then you will understand why it is listing the files in the user home directory.

exec 'cd /var/www \n ls'; 

the above code should solve the problem.

---

