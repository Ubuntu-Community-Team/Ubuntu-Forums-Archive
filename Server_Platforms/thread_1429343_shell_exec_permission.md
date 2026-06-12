---
title: "shell_exec permission"
date: 2010-03-13
forum: Server Platforms
---

### Post by aremint on 2010-03-13
i have a problem run following script

<?php
$output=shell_exec(sudo /sbin/iptable <command>). 
echo $output;
?>

i already adding "www-data ALL=NOPASSWD: ALL” in my etc/sudoers folder but it still not working. i really appreciate if somebody can help me and give step to solve it.

---

### Post by lisati on 2010-03-13
Shouldn't that be iptable**s**?

---

### Post by aremint on 2010-03-14
it still not working. i have replace new script but nothing happen. 

<?php
$output = shell_exec("echo 'password' | sudo -s /sbin/iptables <command>");
echo "<pre>$output</pre>";
?>

---

### Post by Ryan Dwyer on 2010-03-14
tail /var/log/apache2/error.log

You could also put error_reporting(E_ALL) and ini_set('display_errors','on') before your shell_exec() code.

---

