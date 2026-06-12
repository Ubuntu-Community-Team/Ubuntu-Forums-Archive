---
title: "Allow PHP to run shell commands"
date: 2009-09-14
forum: Server Platforms
---

### Post by dragonfly7358 on 2009-09-14
I have recently set up PHP + Apache on a web server 9.0.4 and can run a php file with a shell command perfectly from shell and not from a browser. From what I was reading, www-data is the user that needs access to run things like ifconfig. Any direction on where I can find how to grant www-data access so I can get the results of ifconfig from a browser?

---

### Post by dragonfly7358 on 2009-09-14
Found this in another forum ><
/sbin/ifconfig
Problem solved. Thanks!

---

### Post by aremint on 2010-03-13
i have a problem run following script

<?php
shell_exec(sudo /sbin/iptable <command>). 
?>

i already adding "www-data ALL=NOPASSWD: ALL” in my etc/sudoers folder but it still not working. i really appreciate if somebody can help me and give step to solve it.

---

