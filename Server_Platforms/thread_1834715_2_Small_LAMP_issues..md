---
title: "2 Small LAMP issues."
date: 2011-08-28
forum: Server Platforms
---

### Post by Watchlord on 2011-08-28
I got LAMP actually working now...well, partially.

Current Website Setup

>www
  -index.html
  -other files
  >proxy
    -proxy files (mostly php)
    -htaccess file

Problem 1:

I coppied my htdocs folder (xampp on Windows) contents to my /var/www folder. My website's index.html page works. Going to <website url> works, but when I try to go to to "<website url>/proxy" it prompts me to download a PHTML files instead of prompting for a password or bringing up the proxy page. I'm not even sure the htaccess file even works.

Problem 2:

LAMP runs when I start my computer, but I am unable to restart LAMP or start it once I've stopped it. I get this error:

```
watchlord@excelsior:~$ /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
```

---

### Post by meastwood on 2011-08-28
In /etc/apache2 there is a file called httpd.conf.

You need to be root or use sudo.
Edit httpd.conf (probably empty) and add the line

```
root@mark:/etc/apache2# more httpd.conf
ServerName localhost

root@mark:/etc/apache2# more /etc/hosts
127.0.0.1	localhost

```

This should get rid of the 'reliable hostname' error.

There is a problem with the user apache is trying to run under.  You need to be root to run start up scripts so - do not forget the 'sudo' bit:

```
watchlord@excelsior:~$ sudo /etc/init.d/apache2 restart
```

---

### Post by Watchlord on 2011-08-28
> **meastwood said:**
> In /etc/apache2 there is a file called httpd.conf.

You need to be root or use sudo.
Edit httpd.conf (probably empty) and add the line

```
root@mark:/etc/apache2# more httpd.conf
ServerName localhost

root@mark:/etc/apache2# more /etc/hosts
127.0.0.1    localhost

```This should get rid of the 'reliable hostname' error.

There is a problem with the user apache is trying to run under.  You need to be root to run start up scripts so - do not forget the 'sudo' bit:

```
watchlord@excelsior:~$ sudo /etc/init.d/apache2 restart
```

Now I get this error:

```
watchlord@excelsior:~$ sudo /etc/init.d/apache2 restart
Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'watchlord@excelsior:/etc/apache2', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

---

### Post by CharlesA on 2011-08-28
Remove the thing you just added and restart the service using sudo.

That error doesn't affect anything.

As for the phtml files, are those php files?

---

### Post by Watchlord on 2011-08-28
> **CharlesA said:**
> Remove the thing you just added and restart the service using sudo.

That error doesn't affect anything.

As for the phtml files, are those php files?

I feel like an idiot. For some reason PHP was never installed, that fixed the phtml problem. I can now stop and restart the server, but I still have that error. Oh well. Thanks guys.

Final problem: I want to password protect the proxy directory and have custome html error pages. My migrated .htaccess no longer work (yes, I tried reseting all that paths).

---

### Post by CharlesA on 2011-08-28
I don't think htaccess is enabled by default. See [here]("https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles") for info on how to enable it.

---

### Post by Watchlord on 2011-08-28
> **CharlesA said:**
> I don't think htaccess is enabled by default. See [here]("https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles") for info on how to enable it.

Thanks, I was able to get that working, but the ErrorDocument redirects in .htaccess are not working.

---

### Post by CharlesA on 2011-08-28
> **Watchlord said:**
> Thanks, I was able to get that working, but the ErrorDocument redirects in .htaccess are not working.
How is that line configured?

---

### Post by Watchlord on 2011-08-28
> **CharlesA said:**
> How is that line configured?

After about an hour I figured out that I had to shorten the address from /var/www/error.html to just /error.html

---

### Post by CharlesA on 2011-08-28
> **Watchlord said:**
> After about an hour I figured out that I had to shorten the address from /var/www/error.html to just /error.html
Glad you got it figured out. :-)

Don't forget the mark the thread as solved from thread tools.

---

