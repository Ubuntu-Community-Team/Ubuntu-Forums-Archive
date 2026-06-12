---
title: "PHP shell_exec permissions"
date: 2008-02-01
forum: Server Platforms
---

### Post by Johnsie on 2008-02-01
Hi, I want a php script to execute the following command:

> killall sc_trans_linux -USR1


To do this Im using the following line of php code:

> 
shell_exec("killall sc_trans_linux -USR1");


My problem is that apache2/php doesnt have permission to run this command. How (in detail) can I give the webserver permission to carry out this command?

Normally only root has permission to do this command.

---

### Post by cdenley on 2008-02-01
You can use sudo. I think the line would be something like this
```

www-data ALL= NOPASSWD: /usr/bin/killall sc_trans_linux -USR1

```
and you would add this line with "sudo visudo". Then your php code would be
```

shell_exec("sudo /usr/bin/killall sc_trans_linux -USR1");

```

---

### Post by Johnsie on 2008-02-02
Cheers,m worked great. Thanks :-)

---

### Post by lgastmans on 2008-05-17
Hi guys,

I am desperately trying to get this command to work: It should print the file <filename> to a dot matrix printer. When I run the command directly **in the shell it works fine**. The file is created in the /tmp folder.

$res = shell_exec("sudo /usr/bin/lpr <filename> -oraw");

$res is blank, and nothing happens (ie printer does not react).
I have tried it like this too:

$res = shell_exec("sudo -U<username> -p<password> /usr/bin/lpr <filename> -oraw");

but does not work either.

I added the following line:
www-data ALL= NOPASSWD: /usr/bin/lpr -<username>
but that did not do the trick.

Any feedback would be greatly appreciated

---

