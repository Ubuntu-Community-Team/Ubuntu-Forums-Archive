---
title: "GIT alias from PHP"
date: 2014-03-25
forum: Server Platforms
---

### Post by vsiege2 on 2014-03-25
Does anyone know how to call a GIT alias from php? I have an GIT alias referencing a shell script outside of the webfoot, yet shell_exec cannot excite it as it says it doesn't have the correct permissions. If I run the php code from CLI, all is fine and the alias is executed.  I gave full file permissions just for testing 777 but unfortunately php still reports.

---

### Post by SeijiSensei on 2014-03-27
First, if PHP is running in safe mode, shell_exec() cannot be used.

PHP scripts run with the same permissions as Apache, those of the "www-data" user.  That means the www-data user must be able to see and execute the file.  If you have root privileges, put the script in /var/www for testing purposes with user and group www-data and execute privileges.  Can you run it from there?  Can you run any script from there, even a simple one like
```
#!/bin/sh
echo "$(date +%c) - I was called" >> /var/www/test-script.log
exit 0

```

---

