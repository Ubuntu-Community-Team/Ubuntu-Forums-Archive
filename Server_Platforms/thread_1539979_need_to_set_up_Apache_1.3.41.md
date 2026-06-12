---
title: "need to set up Apache 1.3.41"
date: 2010-07-27
forum: Server Platforms
---

### Post by satyanash on 2010-07-27
We need to set up Apache 1.3.41 and php4 on a server since our other server just broke down.. and our current code is not compatible with apache2 and php5. I have the source files of Apache 1.3.41 and of php4. I do not have any problems in setting up php4 but, after setting up apache2 it gives me that i have successfully built Apache 1.3. 

But when i try to start it through apachectl it gives some errors like 


```
Syntax error on line 329 of /usr/local/apache/conf/httpd.conf:
Invalid command 'Order', perhaps mis-spelled or defined by a module not included in the server configuration
/usr/local/apache/bin/apachectl start: httpd could not be started

```

To try to work this around i opened up httpd.conf and commented the line 329. and then on starting apache 1.3.41 i get this new error:

```
Syntax error on line 330 of /usr/local/apache/conf/httpd.conf:
Invalid command 'Allow', perhaps mis-spelled or defined by a module not included in the server configuration
/usr/local/apache/bin/apachectl start: httpd could not be started

```

After commenting that line too i get the error no. 1 again(just with a different line number), and again after commenting that line i get this new error:

```
Syntax error on line 471 of /usr/local/apache/conf/httpd.conf:
Invalid command 'LogFormat', perhaps mis-spelled or defined by a module not included in the server configuration
/usr/local/apache/bin/apachectl start: httpd could not be started

```

Now after i get this line commented i get another new error:

```
Syntax error on line 483 of /usr/local/apache/conf/httpd.conf:
Invalid command 'CustomLog', perhaps mis-spelled or defined by a module not included in the server configuration
/usr/local/apache/bin/apachectl start: httpd could not be started

```

After i get this one commented Apache seems to have started normally and also gives this message:

> /usr/local/apache/bin/apachectl start: httpd started


But when i point my browser to the server's IP [http://192.168.10.xx/](http://192.168.10.xx/) i get the following line:

> The requested URL / was not found on this server.

Also i can tell Apache is running because at the end of the NOT FOUND page it shows:

> Apache/1.3.41 Server at satyajeet.my.local Port 80

So can anybody please tell me how to build and install Apache 1.3.41 with the required configuration options. Or at least tell me what wrong did i do up there. Also i did not install the components in the support folder.

The server is Ubuntu 10.04 lucid lynx 64-bit

Satyajeet

---

### Post by satyanash on 2010-07-29
bump

---

### Post by satyanash on 2010-07-30
bumpkin

---

