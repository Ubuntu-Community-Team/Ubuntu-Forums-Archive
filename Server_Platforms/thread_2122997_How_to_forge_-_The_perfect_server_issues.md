---
title: "How to forge - The perfect server issues"
date: 2013-03-06
forum: Server Platforms
---

### Post by titanicx on 2013-03-06
Hello all,
Working on getting my new server up and running from the instructions listed on How to forges pages for the perfect server. I have gotten through most the instruction without issues, however i have hit a road bump and cannot continue forward with it until I can get this working: [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p4) I am stuck at section 14.1 where it asks you to log into the sever from a web page. It states that you should be able to log into the server like this: 

*[COLOR=#000000][FONT=verdana]The ISPConfig apps vhost on port 8081 for nginx comes with a phpMyAdmin configuration, so you can use [/FONT][/COLOR][COLOR=#000000][FONT=Courier New][I][http://server1.example.com:8081/phpmyadmin](http://server1.example.com:8081/phpmyadmin)*[/FONT][/COLOR][COLOR=#000000][FONT=verdana] or [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]*[http://server1.example.com:8081/phpMyAdmin](http://server1.example.com:8081/phpMyAdmin)*[/FONT][/COLOR][COLOR=#000000][FONT=verdana] to access phpMyAdmin.

[/FONT][/COLOR][/I][COLOR=#000000][FONT=verdana]How ever I am unable to get this to happen. It it because I am not on the machine? (This is a terminal based server we access remotely). Or is there some other issue perhaps. I am new at this sort of configuration so I have no idea where to even start troubleshooting this issue. I would appreciate any help that can be given. Thanks.[/FONT][/COLOR]

---

### Post by lfacchinelli on 2013-03-07
Starting from the ground .
You can access to that site normally , right ?
Which user are you using to log in ? root user ?? (User from MySQL NOT local users)

Regards
Luciano

---

### Post by mckenna1977 on 2013-03-08
Can you access using http://<IP_address>:8081/phpMyAdmin

Could just be a question of updating your hosts file or DNS...

---

