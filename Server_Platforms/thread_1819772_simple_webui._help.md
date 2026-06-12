---
title: "simple webui. help"
date: 2011-08-06
forum: Server Platforms
---

### Post by rocker2344 on 2011-08-06
I am working on a web ui and some of the commands need sudo. so far this is what i have

The sudoers file
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

www-data ALL=(ALL)NOPASSWD: /usr/sbin/useradd, /bin/mkdir

```

Then the form
HTML
```
<form action="adduser.php" method="post">
    username:  <input type="text" name="username" /><br />
    password: <input type="text" name="password" /><br />
    <input type="submit" name="submit" value="create user" />
</form>

```
Then the php script
```
<?php
//run the command to add a user and create directory
$user = $_REQUEST["username"];
$password = $_REQUEST["password"];
echo system('sudo /usr/sbin/adduser $user -p $password');
echo system('sudo /bin/mkdir /home/$user');
?>
<p> user created </p>

```
nothing happens. i have no idea what is wrong, i have used exec/system/passthru.

---

### Post by kevinthecomputerguy on 2011-08-07
You could use webmin \ usermin

Set it up in webmin, add it as a custom command button, and the allow custom command button module access for users in usermin

[http://webmin.com](http://webmin.com)

---

### Post by rocker2344 on 2011-08-07
i know of webmin, but i was trying to do this to learn and put into my own system.
thanks for the reply anyways

---

