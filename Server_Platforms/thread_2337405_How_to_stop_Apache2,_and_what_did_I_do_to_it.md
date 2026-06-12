---
title: "How to stop Apache2, and what did I do to it?"
date: 2016-09-17
forum: Server Platforms
---

### Post by tonma on 2016-09-17
Hello,

I'm Using Ubuntu 16.04.1 server on virtualbox.

I launched Apache2 server, typed in the IP in the browser, and got to the Apache2 welcome page that tells me that everything is working.

Then, I shut down the virtual machine, but I was still able to login to the ip and see that page. So I looked for ways to shut it down, and I did eventually with the following: [COLOR=#666666][FONT=Consolas]$ sudo service apache2 stop
[/FONT][/COLOR]
But prior to that, I tried to follow the instructions on official Apache website and used: apachectl -k stop, and that didn't work << what exactly did it do? (Source: [https://httpd.apache.org/docs/current/stopping.html](https://httpd.apache.org/docs/current/stopping.html))

Ty

---

### Post by cariboo on 2016-09-17
Ubuntu now uses systemd to control services ( among other things). I use the following command to start apache:2:

```
sudo systemctl start apache2.service
```

and to stop apache2:

```
sudo systemctl stop apache2.service
```

To check if apache2 is running, use the following command:

```
ps ax | grep apache2
```

which should result in something like this, if it is running:

```
cariboo@willy:~$ ps ax | grep apache2
 1727 ?        Ss     0:03 /usr/sbin/apache2 -k start
 3653 ?        S      0:00 /usr/sbin/apache2 -k start
 3654 ?        S      0:00 /usr/sbin/apache2 -k start
 3655 ?        S      0:00 /usr/sbin/apache2 -k start
 3656 ?        S      0:00 /usr/sbin/apache2 -k start
 3657 ?        S      0:00 /usr/sbin/apache2 -k start
13318 pts/0    S+     0:00 grep --color=auto apache2
```

---

