---
title: "[SOLVED] My First Server"
date: 2008-01-22
forum: Server Platforms
---

### Post by dethredic on 2008-01-22
Ok, so I followed [this tutorial]("http://www.howtoforge.com/perfect_server_ubuntu7.10") and every thign seemed to work fine (other than postfix).

Well, I tried typing localhost into the address bar, but that did not work. (Server is taking too long to respond)

Also where is the folder where my web root will be? 

How what nameservers do I use to point the domain to my computer?

Any other first timer things I should know?

---

### Post by insineratehymn on 2008-01-22
Wow, that is one heck of a tutorial.

On page 6 it mentions using init.d to restart apache2:

/etc/init.d/apache2 force-reload

Did you do that? If so, try substituting force-reload with stop and start.

Your root web folder (unless you change it) is:

/var/www

Nameservers? You can use any one you want. If you want a top-level domain then you will have to pay for it. Or you can use no-ip.org and get a free one (it won't be top-level).

First timer things: cgi-bin is in /usr/lib

---

### Post by dethredic on 2008-01-22
Ok, I tried force-reload, stop /start, and a reboot. Nothing.

So that still doesn't work.

Namecheap let me register nameservers, and link them to my IP, so I will see how that works out.

I got my web directory changed, I just hope I can get apache working... Well i still have 24-48 hours before the nameservers change...

---

### Post by AaronMiller on 2008-01-22
are you typing 'localhost' into the address bar on the server machine itself or from another machine?

---

### Post by dethredic on 2008-01-22
from the server machine.

---

### Post by rosegarden78 on 2008-01-22
The only luck I've had running my first server was a LAMP on Ubuntu.  You should check the repositories for Apache2 PHP5 and MySql because they will be installed and linked-up with the dependencies.  To access the web server you type localhost in the location bar.  Or use the ip address range given by your network or router.  For example 192.168.1.1 is my desktop Apache server and 192.168.1.2 is my wireless laptop running Apache and 192.168.2.1 is the custom router address to login.

---

### Post by dethredic on 2008-01-22
well, that does not work either. For some reason I somethign is not working.

---

### Post by koenn on 2008-01-22
> **dethredic said:**
> 
Well, I tried typing localhost into the address bar, but that did not work. (Server is taking too long to respond)
you need to get your loopback interface up -- see that other thread about "telnet localhost 25"

---

### Post by dethredic on 2008-01-22
yes I did, that work, thanks

Reference see here:

[http://ubuntuforums.org/showthread.php?p=4187042#post4187042]("http://ubuntuforums.org/showthread.php?p=4187042#post4187042")

---

