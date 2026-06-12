---
title: "apache2 complains about a missing ServerName on a clean install"
date: 2006-11-09
forum: Server Platforms
---

### Post by tensor on 2006-11-09
I have made a clean install of edgy on my development laptop.
Apache2 prints the following error to the screen if I do '/etc/init.d/apache2 restart':

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

On dapper, everyhing seems to be okay.
The problem seems to be with default config files.
I have reinstalled (with purge) apache2 and all apache related packages and it did not solve my problem.
/etc/hosts seems to be correct.
The problem is fixed by including the bogus "ServerName localhost" directive in /etc/apache/apache2.conf. But that is not a proper solution.

Is anyone experiencing this?

---

### Post by MJN on 2006-11-09
In what way is it bogus, and indeed not a proper solution? (indeed it's arguably not a problem for a default setup given it's only a warning message and advising how it's worked around it)
 
Apache needs to know what the server's called in order to faciliate name-based virtual hosting and to enable some redirects/rewrites. In the absence of a Servername directive it runs a reverse lookup on your IP and, as that's failing, is complaining.
 
If your server doesn't have a 'real' name then, as you've done, just stick localhost (which is one of your server's default aliases) in the servername directive.
 
Mathew

---

### Post by Jaymoon on 2008-01-27
Simply add this line anywhere to your **/etc/apache2/apache2.conf** file:

```
ServerName *whatever*
```

* replace *whatever* with your machine name, or [www.whatever.com](www.whatever.com) URL.

The line wasn't in the file when I did a fresh install.  So add it, restart apache, and you will notice that annoying message is gone. :)

```
/etc/init.d/apache2 restart
```

---

### Post by MJN on 2008-01-28
That's what the OP did.
 
The issue was that they didn't think it was a valid solution (but, as explained, it was/is).
 
Mathew

---

### Post by audioduck on 2008-07-03
> **Jaymoon said:**
> Simply add this line anywhere to your **/etc/apache2/apache2.conf** file:

```
ServerName *whatever*
```

* replace *whatever* with your machine name, or [www.whatever.com](www.whatever.com) URL.

The line wasn't in the file when I did a fresh install.  So add it, restart apache, and you will notice that annoying message is gone. :)

```
/etc/init.d/apache2 restart
```
Nice tip mate. I got the same error and used the same fix.

I wonder why the servername directive isn't in the default config for Apache2. I'm sure that it was there in the old Apache.

---

