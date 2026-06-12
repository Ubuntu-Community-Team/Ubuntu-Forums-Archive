---
title: "Apache server not working"
date: 2018-03-13
forum: Server Platforms
---

### Post by ay2306 on 2018-03-13
I read a lot of threads and none of them is helping me. I installed apache server and everything was working fine but then I did something (which i don't remember what) and it is since showing error
please help me. My apache server is not running and I getting these outputs for following commands

sudo service apache2 status
 [ATTACH=CONFIG]278927[/ATTACH]

sudo service apache2 restart
[ATTACH=CONFIG]278928[/ATTACH]


apache2ctl /etc/apache2/configtest
[IMG]https://s20.postimg.org/kdwn50hpp/image.png[/IMG]

what should I do? Please help.
Steps I have already taken:
1. Removed all apache2 files multiple times to hard uninstall it and reinstalled it again and again

---

### Post by SeijiSensei on 2018-03-13
I don't know why it cannot find /usr/sbin/apache2.  That should be installed when you run "sudo apt install apache2".  Try removing and reinstalling the apache2 package again, then check to see whether the executable /usr/sbin/apache2 exists.

---

### Post by wyliecoyoteuk on 2018-03-13
try ```
ls -la /usr/sbin
``` to see if apache2 is there, and what its permissions are.

---

### Post by Habitual on 2018-03-14
in a terminal, issue
```
apache2ctl -S
```

and show us the output please.

---

### Post by slickymaster on 2018-03-14
*Thread moved to **Server Platforms**.*

---

### Post by jsmart on 2018-03-15
cat /etc/apache2/apache2.conf
apache2ctl configtest

what do you have?

---

