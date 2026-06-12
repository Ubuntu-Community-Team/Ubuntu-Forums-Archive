---
title: "Stop Apache2"
date: 2006-05-12
forum: Server Platforms
---

### Post by iluminate on 2006-05-12
Hi,

Probably I am a moron (which by now everyone knows) but it seems like I can not stop Apache.
I have tried apache2 stop and I get an "OK" that the service is stopped.
But still the webserver is available for the public. HowCome?
I checked the system monitor and there are 6 different Apache -k start -DSSL services running (sleeping).

How the heck do I stop Apache then if not with apache2 - stop???

---

### Post by cgjones on 2006-05-12
Have you tried this:
```
apachectl stop
```

And you also need to make sure that it won't start back up when you reboot the computer.

---

### Post by iluminate on 2006-05-12
Hi,

Well apachectl I do not have, but I do have apache2ctl.
Yes I tried sudo apache2ctl stop and still it is up.
How sick isnt this???

---

### Post by wsanders on 2006-05-12
You may have to try
```

sudo killall apache2

```

However, this is not a permanent solution. if apache2 continues to hang like that after you restart it, something else is wrong.

---

### Post by iluminate on 2006-05-12
[QUOTE=wsanders]You may have to try
```

sudo killall apache2

```

However, this is not a permanent solution. if apache2 continues to hang like that after you restart it, something else is wrong.[/QUOTE]

Hi thanks for your reply,

I am trying to narrow everything down to find the problem. First of all when I type in ```
sudo /etc/init.d/apache2 stop
```
I get the response-
 * Stopping web server (Apache2)...      [ ok ]
I then type in the same thing again and I get the same message
 * Stopping web server (Apache2)...      [ ok ]
I then do - 
```
 sudo /etc/init.d/apache2 start
 * Starting web server (Apache2)... httpd (pid 7995) already running
                                                                                                                                     [ ok ]

```
???? How can it be running when I allready have stopped it??
Now if I check ps - aux I have 8 different Apache2 services running -
root      7995  0.0  1.1  19452  8764 ?        Ss   22:02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8053  0.0  1.6  24136 12900 ?        S    22:02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8054  0.0  1.6  24144 12896 ?        S    22:02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8055  0.0  1.6  24136 12896 ?        S    22:02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8056  0.0  1.6  24136 12892 ?        S    22:02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8057  0.0  1.1  19584  8960 ?        S    22:02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8270  0.0  1.6  24136 12892 ?        S    22:03   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  8272  0.0  1.1  19584  8980 ?        S    22:03   0:00 /usr/sbin/apache2 -k start -DSSL

What I did now was to type in sudo /usr/sbin/apache2 -k stop << and this works. What is the difference between doing /etc/init.d/apache2 stop and /usr/sbin/apache2 -k stop ???

Also another questions is what apache2ctl is doing and what is it's purpose?

Hope someone has a good answer!
Cheers

---

### Post by harisund on 2006-05-12
How did you install apache? Do you think there could have a been a problem with the way it was installed? 

I am also thinking there is a problem with the way it was started. Maybe there were multiple attempts to start. 

Anyway, there is nothing to worry about seeing so many apache2 processes. They are child process. Use 'px axjf' to see a nice listing. You will find that there is one main apache2 and that has probably spawned the rest. 

Do one thing. Try to reboot your machine and check if apache2 is running and use 'ps axjf' to make sure there is only one 'instance' of apache2 and the rest are all it's child processes. Then the /etc/init.d/apache2 method should work fine. 

But if you are running some production machine and a restart is not advisable .. hmm.. I'm sorry but you will have to manually try and kill every apache process using the kill function (kill -9 pid) and then starting apache using only /etc/init.d/apache2 start.

---

### Post by iluminate on 2006-05-12
[QUOTE=harisund]How did you install apache? Do you think there could have a been a problem with the way it was installed? 

I am also thinking there is a problem with the way it was started. Maybe there were multiple attempts to start. 

Anyway, there is nothing to worry about seeing so many apache2 processes. They are child process. Use 'px axjf' to see a nice listing. You will find that there is one main apache2 and that has probably spawned the rest. 

Do one thing. Try to reboot your machine and check if apache2 is running and use 'ps axjf' to make sure there is only one 'instance' of apache2 and the rest are all it's child processes. Then the /etc/init.d/apache2 method should work fine. 

But if you are running some production machine and a restart is not advisable .. hmm.. I'm sorry but you will have to manually try and kill every apache process using the kill function (kill -9 pid) and then starting apache using only /etc/init.d/apache2 start.[/QUOTE]

Thank you for your answers, however I tried "px axjf" and the command was not found, so I suspect it was a typo. ps -axjf gives me this -

  1  9024  9024  9024 ?           -1 Ss       0   0:00 /usr/sbin/apache2 -k start
 9024  9025  9024  9024 ?           -1 S       33   0:00  \_ /usr/sbin/apache2 -k start
 9024  9026  9024  9024 ?           -1 S       33   0:01  \_ /usr/sbin/apache2 -k start
 9024  9027  9024  9024 ?           -1 S       33   0:01  \_ /usr/sbin/apache2 -k start
 9024  9028  9024  9024 ?           -1 S       33   0:00  \_ /usr/sbin/apache2 -k start
 9024  9029  9024  9024 ?           -1 S       33   0:01  \_ /usr/sbin/apache2 -k start
 9024  9032  9024  9024 ?           -1 S       33   0:03  \_ /usr/sbin/apache2 -k start
 9024  9033  9024  9024 ?           -1 S       33   0:00  \_ /usr/sbin/apache2 -k start
 9024  9034  9024  9024 ?           -1 S       33   0:01  \_ /usr/sbin/apache2 -k start

And no, sudo /etc/init.d/apache2 -stop did not work and I have tried to reboot the machine, multiple times.
If I sudo /etc/init.d/apache2 start
I get an error message saying httpd (pid 9024) already running (which in my view is saying that the service was never stopped) But it is stopped when i ```
sudo /usr/sbin/apache2 -k stop
``` and all the childprocesses and everything was gone when doing ps -axjf.
So obviously there is something wrong, maybe it is because how it was installed or something else. But what is puzzle:in me is that Breezy is displaying "OK" when stoping the service with /etc/init.d/apache2 stop.....
Thanks for the help!

---

