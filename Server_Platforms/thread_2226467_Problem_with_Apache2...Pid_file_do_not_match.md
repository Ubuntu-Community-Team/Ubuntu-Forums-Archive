---
title: "Problem with Apache2...Pid file do not match"
date: 2014-05-27
forum: Server Platforms
---

### Post by dusan3 on 2014-05-27
Hi everybody.

I'm having a problem when I try to restart apache2.
After running command sudo /etc/init.d/apache2 restart i'm getting the following error:

* Restarting web server apache2                                         [fail]
 * There are processes named 'apache2' running which do not match your pid file which are left untouched in the name of safety, Please review the situation by hand.

Can somebody help me to resolve this?

Thanks in advance.

---

### Post by dusan3 on 2014-05-27
ok ... i used 
[COLOR=#000000][FONT=Consolas]kill -9 $(ps -e | grep apache2 | awk '{print $1}')
to kill the proccess and return of apache2.pid was 999 ... now i have other problem ...i have another error:
[/FONT][/COLOR] The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 110 of /etc/apache2/apache2.conf:
User takes one argument, Effective user id for this server
Action 'configtest' failed.
The Apache error log may have more information.
It shows error on line USER  ${APACHE_RUN_USER}
What to do?

---

