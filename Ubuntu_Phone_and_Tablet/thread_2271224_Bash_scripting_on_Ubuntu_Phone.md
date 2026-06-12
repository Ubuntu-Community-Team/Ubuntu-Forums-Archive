---
title: "Bash scripting on Ubuntu Phone"
date: 2015-03-28
forum: Ubuntu Phone and Tablet
---

### Post by fransfrans on 2015-03-28
Hello, I just received my Aquaris E4.5 Ubuntu Edition, and would like to do some bash scripting. I am getting the error in the screenshot (/bin/sh bad interpreter permission denied).
When I execute the script with sh, bash or . before the command, it works properly. 
Does anyone know whether /bin/sh has been blocked for a reason (security?) or that there may be a bug somewhere?
[ATTACH=CONFIG]260947[/ATTACH]

Thanks

---

### Post by grahammechanical on 2015-03-28
I will give you a wild guess that is based on a little knowledge about Ubuntu phones and no experience using one.

Apps on the Ubuntu phone are tightly control by Apport to prevent them doing anything they should not be doing. It seems that bash is allowed to run that script and cat is allowed to print the contents of the script to the screen but maybe the script itself is not allowed to run because there is not an apport profile for it.

Regards.

---

### Post by Lutz_Fechner on 2015-03-31
what about trying to put "sudo" upfront?

---

### Post by rolandbreedveld on 2015-04-21
Works fine:
phablet@ubuntu-phablet:~$ ./test.sh 
hallo
phablet@ubuntu-phablet:~$ cat test.sh 
#!/bin/sh
echo hallo

---

### Post by flaymond on 2015-04-21
./test.sh - permission denied?

Already chmod u+x right?

---

### Post by rolandbreedveld on 2015-04-21
and
/bin/sh is not the bash shell /bin/bash ;)

---

