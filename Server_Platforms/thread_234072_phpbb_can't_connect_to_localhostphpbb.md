---
title: "phpbb can't connect to localhost/phpbb"
date: 2006-08-10
forum: Server Platforms
---

### Post by Eddy Gordo from Tekken on 2006-08-10
I installed phpbb2 set it up tested it on my home network. tested it on remote computers.  all worked.  today i wanted to make admin changes so i went tried [http://localhost/phpbb](http://localhost/phpbb) and get the unable to connect error.  from my xp comp on the network i can see the server using the WAN address.  i am able to log in with admin priveleges from xp, but i can't even make a localhost connection from the computer thats hosting...i don't know where to begin looking to remedy this...

---

### Post by macca87 on 2006-08-11
Can you access the web server at all?, not just the phpbb section?.

If you cant access the web server at all...
perhaps the hosts file does not contain localhost?, /etc/hosts
also have u tried [http://127.0.0.1/](http://127.0.0.1/) instead of localhost?,
If that doesnt work perhaps the loopback interface is not activated in /etc/network/interfaces. Ensure that it is.

Also your web server conf file might be disallowing connections from localhost.
just a few ideas hope this helps

---

### Post by Eddy Gordo from Tekken on 2006-08-11
The etc/host file contains localhost in the first line:

> 127.0.0.1	localhost.localdomain	localhost

the etc/network/interfaces file contains loopback in the 2nd line:

> auto lo
iface lo inet loopback

if i use the WAN addy, i can get on the server. if i use localhost, i get can't-connect-error.  which apache2 conf files should be looking in for localhost?  i looked in http.conf, apache2.conf.  the string localhost doesn't exsist in either.  where does it go?

---

### Post by macca87 on 2006-08-11
Could you please post the exact error message?

---

### Post by az on 2006-08-11
How did you install LAMP and phpbb2?  It sounds like you either removed the libapache2-mod-php5 package, you changed or renamed the database or that the mysql daemon is not being started at boot like it should.  

[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)

---

### Post by Eddy Gordo from Tekken on 2006-08-12
> **macca87 said:**
> Could you please post the exact error message?

> Unable to connect

Firefox can't establish a connection to the server at localhost.

    *   The site could be temporarily unavailable or too busy. Try again in a few moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.


i installed following:
[www.howtoforge.com/book/print/1332](www.howtoforge.com/book/print/1332)

libapache2-mod-php5 is installed

using the WAN address, i can access the server from my networked XP, and my friend is able to connect from outside my network.  the server pc can access it using the WAN address, but not the localhost address

---

### Post by Eddy Gordo from Tekken on 2006-08-14
i upgraded to latest version of apache....mistake?

---

### Post by Eddy Gordo from Tekken on 2006-08-16
the phpbb directory is in:

> /var/www/phpbb

am i missing a link in

> /etc/apache2

which apache2 conf files should be looking in for localhost? i looked in http.conf, apache2.conf. the string localhost doesn't exsist in either. where does it go?

---

### Post by Eddy Gordo from Tekken on 2006-08-17
i fixed it.
etc/apache2/ports was not listening to 80.  i'd switched it to 8000 because of ISP issues.  so i had to add the port to the addy

[http://localhost:8000/phpbb](http://localhost:8000/phpbb)

i edited the file to listen to port 80 as well.  although the ISP has issues, i can use it on my network.

thanks to those that helped.

---

