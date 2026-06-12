---
title: "Error message in apache2 sig term"
date: 2007-02-19
forum: Server Platforms
---

### Post by colyn on 2007-02-19
I have a webserver on my Ubuntu machine running Apache2. I have not installed anything else other than the base apache2 install.
The only .conf file I have modified is 000-default The reason is I could not get direct access to /var/www/ so I had to re-direct to a different location.

I have 2 questions:

(1) Whenever I restart apache2 after making changes I get the message "Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" 

It does however restart..How do I get it to recognize my domain name?

(2) I have noticed several times in the error log
[Sun Feb 18 19:28:35 2007] [notice] caught SIGTERM, shutting down
[Sun Feb 18 19:28:36 2007] [notice] Apache/2.0.55 (Ubuntu) configured - -resuming normal operations

Some times it is down for 1 second and other times approx 1 minute...Any ideas on what the problem is and how to fix it?

---

### Post by MJN on 2007-02-19
1. You need to put a **Servername *your.fullyqualidied.server.name* **in the <virtualhost> section of sites-available/default. In the absence of such a directive Apache is simply using the localhost IP address as its 'name'.

2. Something is shutting it down intentionally - a common 'culprit' (in the loosest sense of the term as its by design) is logrotate se to rotate logs every day. Do the times coincide with any such cron jobs?

Mathew

---

### Post by colyn on 2007-02-19
> **MJN said:**
> 1. You need to put a **Servername *your.fullyqualidied.server.name* **in the <virtualhost> section of sites-available/default. In the absence of such a directive Apache is simply using the localhost IP address as its 'name'.

The file I have is sites-available/000-default which I have placed my domain name below ServerAdmin. Am I supposed to also have one named  sites-available/default??

> **MJN said:**
> 2. Something is shutting it down intentionally - a common 'culprit' (in the loosest sense of the term as its by design) is logrotate se to rotate logs every day. Do the times coincide with any such cron jobs?

Mathew

If you mean a new log file no. It happens at various times throughout the day.

---

### Post by MJN on 2007-02-20
000-default is fine - I just thought that's what is was called in sites-enabled/
 
Did you always have the ServerName directive in place? Or just now? Is it now working?
 
As for the seemingly-random restarts I don't know...
 
Mathew

---

### Post by conjur3r on 2007-02-20
> **colyn said:**
> If you mean a new log file no. It happens at various times throughout the day.

It also logs every time you intentionally restart as well as when it runs into problems.  Did you restart at those times?

---

