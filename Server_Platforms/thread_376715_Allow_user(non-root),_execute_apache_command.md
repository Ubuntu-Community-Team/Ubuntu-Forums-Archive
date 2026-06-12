---
title: "Allow user(non-root), execute apache command"
date: 2007-03-05
forum: Server Platforms
---

### Post by dregern on 2007-03-05
Hi, im just curious, is there any other way to allow non-root user to execute apache restart/stop/reload other than using "sudo"..i've tried to change the /etc/init.d/apache2 chmod to all such: chmod 777 /etc/init.d/apache2, but i still could not execute the command, it appears, permission denied. Please help!! :confused:

---

### Post by rjfioravanti on 2007-03-05
Is it successfully entering the script but then failing somewhere inside it? the /etc/init.d/apache2 is just a collection of startup, restart scripts that call other commands on your computer, which I think is where you are having trouble

Your other user has access to that script, but it is calling restricted pieces elsewhere

---

### Post by dregern on 2007-03-05
yeah, when i entered "/etc/init.d/apache2 restart", it appears permission denied:,
what should i do? without using sudo

---

### Post by MJN on 2007-03-05
Sorry to answer your question with another question but why do you want to do this? The answer might help us to suggest a lateral solution to your problem...
 
Mathew

---

### Post by jtc on 2007-03-05
What you need to have in mind is that apache genereally runs as a specific user. To start a process as one user and having it run as another requires some kind of root powers. Unless you want to use sudo you'll have to create a special script and give that script root-powers (chown root, chmod u+s). 

You should know that the later approach basicly is a security hazard waiting to happen. May I ask why you don't want to use sudo? This kind of delegated powers seems like what sudo does best.

---

### Post by Mr. C. on 2007-03-05
Only UID 0 (aka root) may change a processes UID/EUID, etc. to run as some other user, which is what Apache will do.

Setup sudo properly to allow non-root users to run apache.

Setuid shell scripts are discouraged.

MrC

---

### Post by bizza on 2007-03-14
Hello,

root access is required to bind any program to ports in the 1-1024 range. Namjely ports 80 and 443 in this instance.

check out this link

[http://www.debian-administration.org/articles/386](http://www.debian-administration.org/articles/386)

for instructions of how to proxy a non root port for this purpose.

Regards,
Biz

---

