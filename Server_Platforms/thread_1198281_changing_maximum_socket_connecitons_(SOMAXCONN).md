---
title: "changing maximum socket connecitons (SOMAXCONN)"
date: 2009-06-27
forum: Server Platforms
---

### Post by tutunmayan on 2009-06-27
Hi, 
I have a PHP socket server running on my UBUNTU server.

I noticed that when I **echo SOMAXCONN** using PHP I get a result of **128**, means that only 128 user can connect my chat server. With a google search I found 

**sudo sysctl -a | grep somaxconn **

This command also prints out **128**

I tried to change max connectin capacity by **sudo sysctl -w net.core.somaxconn=1024** 

than I again **sudo sysctl -a | grep somaxconn ** and saw that it looks ok and updated max conn number.

STRANGE thing is when I try to echo SOMAXCONN with in PHP it still prints out **128**   ?#!%&?


What does this mean? May I beleive in linux or PHP? Which one is the real connection limit?

I cannot try to connect with over 128 clients.

---

### Post by dragos2 on 2009-06-27
somaxconn should be maximum parrallel opened sockets that the kernel will server at one time (correct me if I am wrong).

the sysctl -w option take effect instantly, but you may need in some cases to restart
the application server to observe the chages since sometimes they are cached

Please note that after a reboot the value you have set using -w will be lost, in order
to make the changes persistent you should add at the end of
**/etc/sysctl.conf** this line: **net.core.somaxconn=65535**

Note to developers: I have to admin that 128 is a low value for a server !

---

### Post by jeep.cherokee.chief on 2009-08-04
this thread is so old i know but same problem i got here!

i tried the **sudo sysctl -w net.core.somaxconn=1024**  and it works fine.

but still PHP says SOMAXCONN = 128!
[B]echo SOMAXCONN
print out 128

[/B]any idea?

---

### Post by lygie on 2010-11-10
Hallo if anyone steps over this comming from google like i did, here is the solution:

php sets SOMAXCONN at the time it is compiled.

1) apt-get install build-essentials
2) [FONT=monospace]**vi /usr/include/bits/socket.h**[/FONT]

change
*#define SOMAXCONN   128*
in
[I]#define SOMAXCONN   2048

3) compile new Version of php

I have written a more substantial documentation [/I]in german language here:
[I]
[http://foobar.lamp-solutions.de/howtos/programmierung/php/einzelansicht-php/article/angepasste-php-version-unter-ubuntu-selbst-kompilieren.html](http://foobar.lamp-solutions.de/howtos/programmierung/php/einzelansicht-php/article/angepasste-php-version-unter-ubuntu-selbst-kompilieren.html)

[/I]

---

### Post by jeep.cherokee.chief on 2010-11-10
> **lygie said:**
> Hallo if anyone steps over this comming from google like i did, here is the solution:

php sets SOMAXCONN at the time it is compiled.

1) apt-get install build-essentials
2) [FONT=monospace]**vi /usr/include/bits/socket.h**[/FONT]

change
*#define SOMAXCONN   128*
in
[I]#define SOMAXCONN   2048

3) compile new Version of php

I have written a more substantial documentation [/I]in german language here:
[I]
[http://foobar.lamp-solutions.de/howtos/programmierung/php/einzelansicht-php/article/angepasste-php-version-unter-ubuntu-selbst-kompilieren.html](http://foobar.lamp-solutions.de/howtos/programmierung/php/einzelansicht-php/article/angepasste-php-version-unter-ubuntu-selbst-kompilieren.html)

[/I]


lol! after 1 year i received a reply at this topic!
thank youuuu!!!! :P

---

### Post by yavuz.maslak on 2011-12-11
Hello

I use ubuntu 11.10 64 bit

I increased net.core.somaxconn using sysctl

but I can't see /usr/include/bits/.. 

is that suppose to do change the value into socket.h  ?

---

