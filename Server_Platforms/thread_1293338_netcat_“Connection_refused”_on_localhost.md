---
title: "netcat “Connection refused” on localhost"
date: 2009-10-16
forum: Server Platforms
---

### Post by edulacomadreja on 2009-10-16
I'm trying to get a value from a netcat connection started at a php file, but it dies with:

    ```
localhost [127.0.0.1] 2000 (?) : Connection refused
```

I don't know why but it works well if I ssh it as apache user (www-data), this is what I've done:

1) Start an endless loop serving a date with a little delay:

    ```
$ (while true; do nc -l -p 2000 -c "sleep 5; date"; done)&
```

2) Check if is working:

    ```
$ su www-data
    $ nc localhost 2000
    Fri Oct 16 21:33:20 COT 2009
```

3) Create /var/www/test.php as follows:

    [PHP]<pre><?php
    exec('nc localhost 2000>>/var/www/dates.txt 2>>/var/www/errors.txt &');
    ?></pre>[/PHP]

4) Run it on a browser:

    ```
http://myserver.com/test.php
```

5) Finally take a look at both txt's, dates is empty (nothing like the response in #2) and errors has the "Connection refused" error.

The server is a LAMP cluster running Ubuntu Server 9.04 with DRBD and Heartbeat.

What is driving me crazy is that this test.php works well in my laptop (LAMP on Ubuntu Desktop 9.04) and the server seems to have the ports already open and listening:

    ```
$ netstat -ntpl
    Active Internet connections (only servers)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
    tcp        0      0 0.0.0.0:4743            0.0.0.0:*               LISTEN      2326/openhpid   
    tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      3364/mysqld     
    tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      9510/nc         
    tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      3470/apache2    
    tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2320/sshd       
    tcp        0      0 127.0.0.1:3551          0.0.0.0:*               LISTEN      2354/apcupsd    
    tcp6       0      0 :::22                   :::*                    LISTEN      2320/sshd
```

Thanks in advanced!!!

---

### Post by Lars Noodén on 2009-10-18
The **su** example, leaves the environment variables settings you had as root.  Try this: 'su **-** www-data' 

Or better, try sudo:


sudo -u www-data sh -c "nc localhost 2000"

sudo -u www-data sh -c "nc localhost 2000>>/var/www/dates.txt 2>>/var/www/errors.txt"

Have you checked the directory and file permissions?  I myself would be very hesitant to have anything in the /var/www hierarchy available for writing by the web server or its processes.  I'd recommend using a different directory and then using the Alias runtime directive to make it *look* like it was under /var/www

---

### Post by edulacomadreja on 2009-10-20
Well, it was a permission problem after all... fixed editing /etc/sudoers with visudo to add:

```
www-data ALL = NOPASSWD: /bin/nc
```

Now it's working, thanks for the correction Lars!

---

### Post by Lars Noodén on 2009-10-20
> **edulacomadreja said:**
> Well, it was a permission problem after all... fixed editing /etc/sudoers with visudo to add:

```
www-data ALL = NOPASSWD: /bin/nc
```

Now it's working, thanks for the correction Lars!

You're welcome.  

With that any and all of your www-data scripts can then run netcat, if they can get a hold of it.  

Might I propose a further modification so that a misbehaving script cannot be used as a generic port scanner?  

```
%www-data ALL = NOPASSWD: /bin/nc localhost 2000
```

Yet another modification might be to use mod_suexec to run that script under its own special group, not www-data, and give the sudo privileges to that special group.  It would prevent nc from being run by just any old script.

---

### Post by edulacomadreja on 2009-10-20
This server is going to work inside a trusted LAN, isolated from the internet; but I'll add that localhost restrictions.

There is so much to learn, thanks again!

---

