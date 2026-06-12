---
title: "Disable waiting to enter password at SSH login"
date: 2010-03-18
forum: Server Platforms
---

### Post by dragos2 on 2010-03-18
I have a thing that bothers me whenever I login to one of the servers running Ubuntu Server 8.04 after I enter the username it waits for about 5 seconds before it allows me to enter the password and I don't know from where to change this wait time/ disable it.

Any ideas of what is causing this ?

---

### Post by dragos2 on 2010-03-18
I found the answer here:
[http://ubuntuforums.org/archive/index.php/t-630623.html](http://ubuntuforums.org/archive/index.php/t-630623.html)

and in short add UseDNS no to /etc/ssh/sshd_config

because it somehow tries to resolve something and that causes to wait for
a DNS server to answer, etc.

---

### Post by dudumomo on 2010-03-18
Glad to know it works !

---

