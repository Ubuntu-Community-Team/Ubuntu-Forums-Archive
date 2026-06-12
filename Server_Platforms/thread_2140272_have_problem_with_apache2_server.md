---
title: "have problem with apache2 server"
date: 2013-04-29
forum: Server Platforms
---

### Post by sipetron on 2013-04-29
please help when i try to start apche server its give me this error 
[h=3]Failed to start apache : 
 * Starting web server apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80 no listening sockets available, shutting down Unable to open logs Action 'start' failed. The Apache error log may have more information.    ...fail! 

what should i do ????
[/h]

---

### Post by smeerbartje on 2013-04-29
There is already an instance running...

---

### Post by sipetron on 2013-04-29
and how can i fix it ?

---

### Post by smeerbartje on 2013-04-29
- Open [http://serverip](http://serverip) and see what happens. Do you see a website?
- "sudo service apache2 status". Does this output: "Apache2 is running (pid ####)."??

IMHO, if you can't solve this... do not continue with it ;).

---

### Post by sipetron on 2013-04-29
Apache2 is NOT running.
and i need to fix it

---

### Post by Doug S on 2013-04-29
Well, something appears to be using port 80 already. The question is what? Use the netstat to observe what is listening to tcp protocol. Example:```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat -lnpt[/COLOR]
[sudo] password for doug:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      31291/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      31010/smbd
tcp        0      0 0.0.0.0[COLOR=#ff0000]:80              [/COLOR]0.0.0.0:*               LISTEN      1489/apache2
tcp        0      0 173.180.45.4:53         0.0.0.0:*               LISTEN      1184/named
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1184/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1184/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      31425/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1405/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1184/named
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      31010/smbd
```

---

### Post by sipetron on 2013-05-04
I done it and i found this 
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      3993/nginx  
i tried to delete it or change the default port , but nothing happen

---

### Post by Doug S on 2013-05-04
So, you seem to already be running the nginx web server, and it has already claimed port 80.
You didn't say why you couldn't delete it, but it seems to me you should be able to.
You should also be able to stop nginx, and thus free up port 80:```
sudo service nginx stop
```
Be certain the below is what you actually want to do first:
To uninstall try (leave the config files):```
sudo apt-get remove nginx
```Or (also removes config files)```
sudo apt-get purge nginx
```

---

### Post by sipetron on 2013-05-08
nothing to remove , but the service still working ,

---

### Post by Doug S on 2013-05-08
It is not clear to me what you are trying to say. A few more words and details would help.
Are you saying that you got this?:```
doug@s15:~/sguide-1304/doug_help$ [COLOR=#ff0000]sudo apt-get remove nginx[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR=#ff0000]Package nginx is not installed, so not removed[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```That would suggest that ngnix was installed manually and the package managment system does not know it is there (I think). If that's the case, then I'm hoping someone else can help you further, as I am not sure how to proceed.

---

### Post by CharlesA on 2013-05-08
I'm with Doug on this one. @OP: How did you install Nginx?

---

### Post by sipetron on 2013-05-09
i dont know how he in my server in first place !!!!!

---

### Post by sipetron on 2013-05-09
yap thats what i get it

---

### Post by CharlesA on 2013-05-09
> **sipetron said:**
> i dont know how he in my server in first place !!!!!

Huh. Run this please.

```
find / -name nginx -print
```

It will probably spit back a bunch of stuff.

---

### Post by sipetron on 2013-05-11
/usr/sbin/nginx
/usr/local/nginx
/usr/local/nginx/sbin/nginx
/usr/share/nginx
/var/lib/nginx
/var/lib/update-rc.d/nginx
/var/log/nginx
/etc/logrotate.d/nginx
/etc/ufw/applications.d/nginx
/etc/default/nginx
/etc/init.d/nginx

---

### Post by CharlesA on 2013-05-11
Yeah, it looks like nginx was compiled from source, otherwise it would be in /etc/nginx

In order to remove it, you would need to run make uninstall from wherever you installed it from.

---

### Post by sipetron on 2013-06-02
:(

---

