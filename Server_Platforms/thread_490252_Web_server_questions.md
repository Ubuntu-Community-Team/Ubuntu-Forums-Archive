---
title: "Web server questions"
date: 2007-07-02
forum: Server Platforms
---

### Post by william_hunter on 2007-07-02
Hey all. I need some help getting a web server I am building to link up with a domain name I parked with DYNDNS. I have installed LAMP and have a functional web forum set up that can be accessed form outside my firewall, as evidenced by the fact that my testers can log in and have made accounts using the correct IP. 

My problem is, I want to make it easy to get to. The domain name i reserved is rot.game-host.com, FYI. Anyone have some insights into what I need to do next?

---

### Post by Brazen on 2007-07-02
you need to log onto the dyndns website and set that domain name to point to your ip address.

---

### Post by ixus_123 on 2007-07-02
your router will probably also have some dynamic DNS setting so that it will autoupdate

(that's assuming dyndns is short for dynamic dns - if you have a static, life is a little easier)

---

### Post by william_hunter on 2007-07-02
I think I was jumping the gun, but let me explain just in case anyone else has the same problem I did.

I signed up for a free dynamic DNS through DYNDNS.com. This gave me a named host, and it is now working. Most of it was automatic, but I did not wait long enough before bemoaning the fact that the DNS was not working. It is now. DYNDNS automatically detects your IP and links it to your page, as long as you have the correct port forwarded. It was actually very painless in the end, in spite of my impatience. ;)

Now, my problem is apparently with Apache, because when I point my browser toward the chosen host name, I (and everyone else) sees an index that includes apache2, phpmyadmin, and phpbb. THe forum is accessed by clicking on the phpbb link in that index, or by adding /phpbb to the end of the domain name. I am sure there is a way to automatically redirect this to the phpbb site, but as I am dumb, I do not know it.

---

### Post by joewilliams on 2007-07-02
make a text file with this one line in it:

<html></html>

save it as index.html in your web root ( probably /var/www )

*****************************

make another text file with this one line in it:
```

redirect /index.html http://yoursite/newdirectory/new file

```
PAY ATTENTION TO THE SACES

save it as .htaccess in your web root (note the "dot" before the '"h")
["newdirectory" would be the directory where your phpbb installation is located and "new file" would be index.php (I guess) for phpbb]

---

### Post by william_hunter on 2007-07-03
> **joewilliams said:**
> make a text file with this one line in it:

<html></html>

save it as index.html in your web root ( probably /var/www )

*****************************

make another text file with this one line in it:
[b]```

redirect /index.html http://yoursite/newdirectory/new file

```[/b]
PAY ATTENTION TO THE SACES

save it as .htaccess in your web root (note the "dot" before the '"h")
["newdirectory" would be the directory where your phpbb installation is located and "new file" would be index.php (I guess) for phpbb]

Do I need to put in the server's IP or the name assigned by DNS?

---

