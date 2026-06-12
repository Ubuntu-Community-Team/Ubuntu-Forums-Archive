---
title: "PHP not working after 10.04 upgrade"
date: 2010-04-30
forum: Server Platforms
---

### Post by Aries-Belgium on 2010-04-30
Hi

Today I upgraded to 10.04 but now PHP isn't working anymore on my localhost. Apache is running and it serves static HTML pages but PHP file are just being downloaded by the browser, unparsed.

In the error.log I can see this:
```

[Fri Apr 30 15:15:23 2010] [notice] caught SIGTERM, shutting down
[Fri Apr 30 15:15:23 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4 with Suhosin-Patch configured -- resuming normal operations

```

How can I fix this?

Regards,
Aries-Belgium

---

### Post by ghost_ryder35 on 2010-04-30
> **Aries-Belgium said:**
> Hi

Today I upgraded to 10.04 but now PHP isn't working anymore on my localhost. Apache is running and it serves static HTML pages but PHP file are just being downloaded by the browser, unparsed.

In the error.log I can see this:
```

[Fri Apr 30 15:15:23 2010] [notice] caught SIGTERM, shutting down
[Fri Apr 30 15:15:23 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4 with Suhosin-Patch configured -- resuming normal operations

```

How can I fix this?

Regards,
Aries-Belgium


What you see in the error looks perfectly normal.  You will see that message anytime apache is restarted.  What does the access log look like for the PHP requests.

---

### Post by Aries-Belgium on 2010-04-30
Solved it.
The problem was the user_dir module for Apache2.

For those who have the same problem:
1) sudo vim /etc/apache2/mods-enabled/php5.conf
2) comment all lines from <IfModule mod_userdir.c> to the next </IfModule>
3) sudo service apache2 reload

If your browser has an aggressive cache you may have to clear it.

---

### Post by ILikeLinux on 2010-04-30
Thanks a lot. Helped me in not losing much time in search for a solution.

---

### Post by ms.shams on 2010-05-02
my problem don't fixed with this solution. do you have another idea?

---

### Post by PetruM on 2010-05-02
> **ms.shams said:**
> my problem don't fixed with this solution. do you have another idea?

I've had this problem and after I've fixed it on the server, I needed to clear the browser's cache. If you use Firefox, see Tools -> Clear Recent History..., check 'Cache' from the list and make sure you select 'Everything' at 'Time range to clear'. Then refresh the page using CTRL+F5. :D

---

### Post by ms.shams on 2010-05-03
yes, its true :D
my problem fixed too. thank you for your help.

---

### Post by biji on 2010-06-29
This *feature* is stupid. It took one day to solve this issue, for old ubuntu user like me. I was stressed until reading this thread. damn ubuntu!

---

### Post by Vegan on 2010-06-29
I installed 10.04 clean and I have not had problems. I tested an upgrade and it was no good.

---

### Post by biji on 2010-06-29
You probably not using public_html for your php.

---

### Post by baxterworshop on 2010-06-30
I've been wrestling with this and I'm not making any progress.
Apache still spits out PHP as if it were HTML. .php files come up like plain text.
so far I've:

Reinstalling a LAMP components
turning off "short-tags"
"AddType ... .php"
a2enmod php5 (it was alread enabled)
commenting out <IfModule mod_userdir.c>

each time I restarted apache
and of cource, I was clearing my cache before tying to view again.

What am I missing?
I've done this several times before with no trouble.

Thanks

---

### Post by biji on 2010-06-30
can you paste apache2 error log?
major step is:
1. comment user_dir section in php5.conf
2. clear firefox cache

---

### Post by baxterworshop on 2010-06-30
Thanks for responding

I had already done those two steps

Also tried "engine = On" (it was already on)

Here is the log. I couldn't see anything glaring...

[Wed Jun 30 04:12:32 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Wed Jun 30 04:12:35 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 04:12:35 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Wed Jun 30 04:23:02 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 04:23:02 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 04:31:35 2010] [notice] caught SIGTERM, shutting down
[Wed Jun 30 04:31:36 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 07:42:00 2010] [error] [client 221.192.199.35] script '/home/baxterworkshop/public-html/prx2.php' not found or unable to stat
[Wed Jun 30 14:47:43 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 14:47:44 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 14:48:07 2010] [error] [client 192.168.10.3] File does not exist: /home/baxterworkshop/public-html/favicon.ico
[Wed Jun 30 14:48:07 2010] [error] [client 192.168.10.3] File does not exist: /home/baxterworkshop/public-html/favicon.ico
[Wed Jun 30 14:48:10 2010] [error] [client 192.168.10.3] File does not exist: /home/baxterworkshop/public-html/favicon.ico
[Wed Jun 30 15:14:54 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 15:14:54 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 15:15:26 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 15:15:26 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 15:23:07 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 15:23:08 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 16:19:53 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 16:19:54 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 16:24:35 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 16:24:35 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 20:44:21 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 30 20:44:21 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 30 21:47:21 2010] [notice] caught SIGTERM, shutting down
[Wed Jun 30 21:54:14 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations

---

### Post by biji on 2010-07-01
PHP seems loaded,
what url do you try to load?

---

### Post by baxterworshop on 2010-07-01
localhost
127.0.1.1
and my current IP

---

### Post by SecretLegend on 2010-07-01
> **Aries-Belgium said:**
> Solved it.
The problem was the user_dir module for Apache2.

For those who have the same problem:
1) sudo vim /etc/apache2/mods-enabled/php5.conf
2) comment all lines from <IfModule mod_userdir.c> to the next </IfModule>
3) sudo service apache2 reload

If your browser has an aggressive cache you may have to clear it.
Hey thanks this helped me too :)

---

### Post by baxterworshop on 2010-07-01
Nothing is working - this is driving me nuts. 

I've tried installing Umbuntu server and I get the same problem.

I've commented the lines,
added the associations
changed the options in the various conf files
everything that's listed on the net for this problem

other then umbuntu, what distribution would you suggest to do LAMP?

---

### Post by baxterworshop on 2010-07-02
OK!

sudo apt-get install lamp-server^

is the only thing that works. (after commenting out the mod-libc tag in php5.conf)

---

