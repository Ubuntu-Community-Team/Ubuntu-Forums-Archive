---
title: "apache webserver stops responding after 1 day"
date: 2013-10-02
forum: Server Platforms
---

### Post by devraj2 on 2013-10-02
Hii,


I have a problem with my apache webserver configured in Ubuntu 10.10.

Webserver  stops responding after 2 days. while i am able to telnet, ping. at same  time i am also able to SSH access. but while entering any command it  gets stuck at same point. even i am not able to see logs,  start/stop/restart/status of service etc.
 

But after restart completely it will work for 2 days.

apache error logs is given below.
[SIZE=3]
[/SIZE][h=1][SIZE=3]Client denied by server configuration error [[COLOR=#000000]/var/www/favicon.ico[/COLOR]]("http://stackoverflow.com/questions/11099420/file-does-not-exist-c-wamp-www-favicon-ico-in-apache-error-log")[/SIZE][/h]plz help me to solve this issue

---

### Post by Lars Noodén on 2013-10-02
First off, to make things a lot safer, you should probably turn off telnet access if you are using it to log into user accounts.  If you have it for a non-account related activity then it will be ok but nothing that has user names or passwords as telnet sends them in the clear.  If you have been using telnet instead of ssh, change your passwords and remove telnet, stick with ssh. 

Second, when the server stops responding, is it the whole server or just the web server?   That is, can you still log in with ssh after it stops working?

---

### Post by devraj2 on 2013-10-03
yes whole server stops responding but yes i am able to telnet on tcp port 80 but through web not able to open. at same time i am not able to fire any command.

---

### Post by Lars Noodén on 2013-10-03
If the whole server stops responding such that you cannot log in with ssh, then I would look in /var/log/syslog to see where the problem is.  It is on a fixed IP number and not getting its address via DHCP, right?  If you have access to the console, does that still work when you are locked out with ssh and http?

---

