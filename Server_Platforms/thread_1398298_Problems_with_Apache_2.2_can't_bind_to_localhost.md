---
title: "Problems with Apache 2.2: can't bind to localhost"
date: 2010-02-04
forum: Server Platforms
---

### Post by TheAlien on 2010-02-04
Hi,

I've installed the LAMP software trough Ubuntu's repositories.

I've configures Apache to listen to localhost:80 as in [COLOR=Red]Listen localhost:80[/COLOR][COLOR=Black] in ports.conf.

When i try to start Apache, I get this error:

[/COLOR]```
(98)Address already in use:make_sock:could not bind to address 127.0.0.1:80
no listening sockets available, shutting down"
```I've searched Google for this problem and tried the following:

1. Look for multiple [COLOR=Red]Listen localhost:80[COLOR=Black] lines/text within /etc/apache2/, but I've got only one and that is correct.
2. Removed all apps that have listened to localhost, including MYSQL and IPP.
3. Stopped avahi-daemon

I still get the error message when I start Apache.

Though, if I change the Apache's listen address to 127.0.1.1:80, it works. But I need to use [/COLOR][/COLOR][COLOR=Red][COLOR=Black]127.0.0.1:80.

All suggestions are very appreciated, thanks! :)
[/COLOR][/COLOR]

---

### Post by suseendran.rengabashyam on 2010-02-05
Hi,


       Try any one of the following steps and let me know if it works


       1) Open the file /etc/apache2/apache2.conf and look out for the  line,


       ```
Listen localhost:80
```       if you have that line, go ahead and comment it. Also make sure that  this line is present in the file /etc/apache2/ports.conf


       2) Run the following command to check if a running process is  holding the port needed by apache2


```
sudo netstat -plant | grep 80

```Once you see these results, note down the program name which is using port 80 and try to  terminate it.


3) Try to do the following instead of passing the restart switch 



```
sudo /etc/init.d/apache2 stop
```and then


```
sudo /etc/init.d/apache2 start
```

---

### Post by TheAlien on 2010-02-07
Hi, suseendran.rengabashyam!

Thanks for your help! I was actually looking for that command to see what programs that use certain ports. But since 127.0.1.1 works, I just changed everything to that address, and now Apache2 works fine. But if I'll ever need to use 127.0.0.1 again, I may come back to you on this one. Thanks! :)

---

