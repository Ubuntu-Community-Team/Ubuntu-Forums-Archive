---
title: "runing MOC from web browser"
date: 2010-11-02
forum: Server Platforms
---

### Post by darone on 2010-11-02
Hi!

I have thin client with ubuntu server 10.10 installed on it. I want to run MOC (music on console) server from browser. When I log in to www-data account everything is ok - i can run moc server and I can execute php script which runs moc server. But when i trying do it from browser there is nothing happen. 

My config files:
index.php :
[PHP]   <?php
$out=shell_exec("./moc.sh");
echo "<br />";
echo $out;
   ?>[/PHP]

echo output: "OK"

moc.sh :
```
#!/bin/bash

/usr/bin/mocp -S
echo "OK"
```

/etc/sudoers :
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
www-data ALL=(ALL) NOPASSWD: /var/www/moc.sh
www-data ALL=(ALL) NOPASSWD: /bin/bash
www-data ALL=(ALL) NOPASSWD: /usr/bin/mocp

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=(ALL) ALL


#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

I am using lighttpd server. Please help.

---

