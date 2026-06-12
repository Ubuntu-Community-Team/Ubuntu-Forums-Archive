---
title: "PHP's shell_exec won't run sudo commands"
date: 2013-05-29
forum: Server Platforms
---

### Post by roooii on 2013-05-29
Hello,

The problem is I can't get php to execute sudo commands with shell_exec().
Any idea why php won't create the directory?

For a test I created the bash script in a completely insecure area, but don't look at that.

[PHP]
$result = shell_exec('ksh bash.ksh');
echo 'Result: ';
var_dump($result);
[/PHP]

/etc/sudoers:
```

www-data ALL=NOPASSWD:/var/www/domains/mydomain/http/bash.ksh

```

/var/www/domains/mydomain/http/bash.ksh
```

#!/bin/ksh
sudo -u root mkdir -p /var/www/domains/mydomain/http/bananen
```

Best regards!

---

### Post by roooii on 2013-05-29
Anyone? :)

---

### Post by slickymaster on 2013-05-29
> **roooii said:**
> ...
/etc/sudoers:
```

www-data ALL=NOPASSWD:/var/www/domains/mydomain/http/bash.ksh

```
...!
I think you are missing a space between **www-data ALL=NOPASSWD:** and **/var/www/domains/mydomain/http/bash.ksh**
Try to change it to ```
www-data ALL=NOPASSWD: /var/www/domains/mydomain/http/bash.ksh
```and test it.

---

### Post by roooii on 2013-05-29
This works: > www-data ALL=(ALL) NOPASSWD:ALL

I tried it without the space, but it won't make a difference.

Btw how unsafe is this solution to give www-data sudo to the .ksh script?

Edit: I might have misunderstood the method of the sudoers file. I read this: [http://ubuntuforums.org/showthread.php?t=809233](http://ubuntuforums.org/showthread.php?t=809233) and I was thinking the same as this guy.

But still one last question. Now I can run all commands in my php file with sudo. Which is pretty unsafe as I would be able to use commands to take over the complete server. How can I for example only allow the command "mkdir" or "service apache2 reload"?

---

### Post by SeijiSensei on 2013-05-29
> **roooii said:**
> Btw how unsafe is this solution to give www-data sudo to the .ksh script?

Giving the www-data user sudo privileges substantially compromises the security of the server.  Suppose, for instance, the person tries to access [noparse]http://example.com/../../etc/shadow[/noparse]?  If you have not limited URLs like that, essentially every file on your machine is open to view.

*No machine exposed to the Internet should ever run Apache with root privileges*.

If you want to trigger the system to run a shell command with root privileges, the best solution is to use a "semaphore" method where the PHP script writes a triggering file to a known location.  Create an entry in root's crontab to check for the file every minute and perform the required action if the file exists.

---

