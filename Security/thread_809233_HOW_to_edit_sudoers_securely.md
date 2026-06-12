---
title: "HOW to edit sudoers securely"
date: 2008-05-27
forum: Security
---

### Post by CFIL on 2008-05-27
Hello , 

I would like to edit /etc/sudoers to get root access for a user, 

I know that the command is that , 

user ALL=NOPASSWD: ALL

but this is not secure to get all the privilege to the user, I want to choice the software that could run as root and the command that it could be use. For example, 

software: /home/user/test.sh
commands: ls and rm

How this "user ALL=NOPASSWD: ALL" will be after add these conditions ? 

Thanks in advance:)
CFIL

---

### Post by Monicker on 2008-05-27
[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

---

### Post by wdaniels on 2008-05-27
The first ALL means that the configuration applies to all machines. The last ALL refers to all commands. So, in place of the last ALL you can list the specific commands (and/or directories) for which the user can gain root privileges, e.g.

```
user ALL=NOPASSWD: /bin/kill
```

Note that where you have NOPASSWD: this is a tag which means that for all subsequent commands in the list, the user does not need to enter his password to use sudo - that may or may not be what you want. You can just leave out the NOPASSWD: tag if you want the user to authenticate before being able to sudo.

You can always use the man command to get this kind of information:

```
man sudoers
```

But admittedly, it can often be a little complicated/confusing, especially if you're not a native English speaker.

---

### Post by CFIL on 2008-05-27
Thank you all,

MR wdaniels, I understood now how can i configure commands for a user. 

I have another thing which is if I want to configure it to "nobody" account which can be works with scripts , like this
nobody ALL=NOPASSWD: ALL
How can I specify only one software that could work with root privileges without other scripts.For example : 
the software in : /var/www/test.php 
That will work under Apache that mean it has nobody privilege if i want to do "nobody ALL=NOPASSWD: ALL" Then all scripts will run as root and this is not a good idea. How can i choice just my script works with root privileges. I guess there is something like this :
nobody ALL=NOPASSWD: /var/www/test.php
Thanks in advance :)
CFIL

---

### Post by wdaniels on 2008-05-27
> **CFIL said:**
> For example : 
the software in : /var/www/test.php 
That will work under Apache that mean it has nobody privilege if i want to do "nobody ALL=NOPASSWD: ALL" Then all scripts will run as root and this is not a good idea. How can i choice just my script works with root privileges. I guess there is something like this :
nobody ALL=NOPASSWD: /var/www/test.php

No, you are misunderstanding sudo here - it will not tell Apache which user to run a script as. Also note that if you are using the default Ubuntu (Debian) config and packages for Apache, the user that Apache runs as is called "www-data" not "nobody".

It is much more difficult to get a script to run as another user in Apache. It's easier with CGI than PHP, but still a bit complicated.

However, if you only need your PHP script to run shell commands with elevated privileges then you can just use sudo in the shell_exec command in PHP:

```
<?php shell_exec("sudo /bin/kill whatever"); ?>
```

...and then add this command to the sudoers file for user www-data:

```
www-data ALL= NOPASSWD: /bin/kill
```

---

### Post by CFIL on 2008-05-27
Thanks mate .! 

But if there is another script in the same server and run that 
[PHP]<?php shell_exec("sudo /bin/kill whatever"); ?>[/PHP]
then he will get the result because all the scripts run under www-data account ..!! Big problem , no anyone want to do that ... 
But is there any way to do that for just my script and i enter the path of my script so that command
[PHP]<?php shell_exec("sudo /bin/kill whatever"); ?>[/PHP]
will just work if the script path is : [COLOR="Navy"]/var/www/test.php[/COLOR] , but if the other scripts run the same command but different path then it will deny . In php i guess its very hard to configure that.
Do you have any idea to do that ? 

Thanks
CFIL

---

### Post by wdaniels on 2008-05-27
There's no simple and elegant solution really. Sudo has nothing more for you here. You can start doing complicated things with Apache to control access to stuff, or you can bite the bullet and use [suPHP]("http://www.suphp.org/Home.html") (or PHPSuExec), which brings in it's own set of issues, but if you have a fair amount of control over how the server is used and you're prepared to invest a little time in it, this is probably your best solution.

Basically, what it does is allows a script to run as it's owner, which is exactly the functionality you need, only it involves a whole different way of dealing with script permissions on the server which some web software does not understand or accommodate (or at least not by default).

---

### Post by CFIL on 2008-05-27
Thanks , I like the idea behind suPHP . It's really safe and more secure than just allow sudo for everyone. 

I will go to read more about suPHP. 

Thank you for the help mate :)
CFIL

---

