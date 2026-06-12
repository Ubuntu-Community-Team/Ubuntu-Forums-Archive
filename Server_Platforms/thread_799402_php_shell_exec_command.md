---
title: "php shell exec command"
date: 2008-05-19
forum: Server Platforms
---

### Post by lgastmans on 2008-05-19
Hi guys,

I am desperately trying to get this command to work: It should print the file <filename> to a dot matrix printer. When I run the command directly in the shell it works fine. The file is created in the /tmp folder.

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

### Post by solcott on 2008-05-19
Give this a try:
```
$res = system("sudo /usr/bin/lpr <filename> -oraw");
```

---

### Post by Dr Small on 2008-05-19
Or try using backticks instead:
```
$res = `sudo /usr/bin/lpr <filename> -oraw`;
```

---

