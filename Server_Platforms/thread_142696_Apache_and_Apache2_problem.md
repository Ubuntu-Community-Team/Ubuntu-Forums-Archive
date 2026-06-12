---
title: "Apache and Apache2 problem"
date: 2006-03-11
forum: Server Platforms
---

### Post by secici on 2006-03-11
Two days ago, I installed apache and no problem was experienced. I could easily reach to see the famous **placeholder page**.

But after I tried a Python based web application I began to experience some problems. Now the circle of firefox turns round and round but there is no response.

I installed and reinstalled apache and apache2 (not both at the same time) a number of times but nothing changes. I know about the /etc/init.d/apache and apache2 stop, start and restart. I used these commands after being root. There is no problem as I could see.

Where to check to find out where the problem derives from?

---

### Post by amohanty on 2006-03-11
> But after I tried a Python based web application I began to experience some problems. Now the circle of firefox turns round and round but there is no response.


Could you be a bit more specific, as to what you did, what py app you installed, what is the script?
Also what do the error logs a fole called error_log say when you try to hit the main site?

AM

---

### Post by secici on 2006-03-11
Pardon me...

It is not a Python based, it is a Perl based application

sql-ledger, an accounting application... Can be found by searching Synaptic.

I completely removed all packages that were related with apache. When I call localhost when the server is not running or not installed, Firefox waits for a long time. This is normal. I install apache or apache2. They start succesfully without an error. But nothing changes. Firefox waits and waits.

What keeps apache away from showing the startpage?

I am totally confused.

---

### Post by secici on 2006-03-11
here s what I could obtain from /var/log/apache2/error.log

> [Sat Mar 11 14:44:51 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Sat Mar 11 15:07:31 2006] [notice] caught SIGTERM, shutting down


Apache doesn't face any request.

---

### Post by secici on 2006-03-11
I discovered that my problem is much more deeper.

I reinstalled ubuntu from verison 5.10 CD with the **server** parameter. Installed apache2. Activated universe repository.

Installed xubuntu-desktop. Successful.

But still [http://localhost](http://localhost) not responding.

I also tried to ping **localhost** and **127.0.0.1 ** they also cannot respond. The weird thing is: I am writing this message to you from the same machine. This means TCP/IP and web services are working. I removed apache2. Nothing changed.

I can't understand anything.

---

### Post by secici on 2006-03-12
The scope of my problem changed so I opened a new thread:

[http://www.ubuntuforums.org/showthread.php?t=143259](http://www.ubuntuforums.org/showthread.php?t=143259)

---

