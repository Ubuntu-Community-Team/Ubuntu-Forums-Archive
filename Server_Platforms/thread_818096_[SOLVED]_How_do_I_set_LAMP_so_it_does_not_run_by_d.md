---
title: "[SOLVED] How do I set LAMP so it does not run by default at startup?"
date: 2008-06-04
forum: Server Platforms
---

### Post by Rytron on 2008-06-04
Hi,
How do I set LAMP so it does not run by default at startup?
I'd rather start it up manually as I presume it is just wasting resources by having it running in the background when it is not being used.
Also would running LAMP pose a security risk when I go on the internet?
Thanks.

---

### Post by Sef on 2008-06-04
Moved to Server Platforms.

---

### Post by quelx on 2008-06-04
> **Rytron said:**
> Hi,
How do I set LAMP so it does not run by default at startup?
I'd rather start it up manually as I presume it is just wasting resources by having it running in the background when it is not being used.


from the terminal
```
sudo update-rc.d -f apache2 remove
sudo update-rc.d -f mysql remove 
```

If you're in gnome **System** > **Administration** > **Services** and disable/enable apache2 and mysql

> Also would running LAMP pose a security risk when I go on the internet?
Thanks.

Yes, having ***any*** services running is a security risk, the most secure computer is powered off :)

---

### Post by Kolipoki on 2008-06-04
> **quelx said:**
> Yes, having ***any*** services running is a security risk, the most secure computer is powered off :)

Well this confuses me a bit. I'm trying to make some independent decisions at my job, where Windows servers have been the  traditional option, and at the moment I'm trying to setup an Ubuntu 8.04 web server with a face to the internet (doing this for the first time).  I actually selected Ubuntu thinking of security. 

So how secure/insecure will I be in the internet with Ubuntu server edition? I am aware that probably we are missing some discussion on some possible scenarios, regarding the security issue when setting up a web server for internet. My scenario is a server inside a very small public agency's network, which by local law needs to publish some documents, and, on my initiative, will be joined by some PHP/MySQL applications soon.

I'm positively sure that some clarifying comments here would be very useful, and, on my behalf, greatly appreciated.

---

### Post by cdenley on 2008-06-04
It is a security risk if you configure it wrong. It is also a security risk if a malicious attacker finds an unknown remote security vulnerability. I would be more worried about your php code than any unknown apache vulnerabilities. By default, it is probably as secure as any other default lamp install. It would certainly be more secure than a windows server.

I think what was meant is that running any network service opens a point-of-attack. Without apache running, you would be safe from hypothetical unpatched security vulnerabilities.

---

