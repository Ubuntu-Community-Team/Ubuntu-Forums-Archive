---
title: "Ubuntu Server proxy settings"
date: 2008-09-18
forum: Server Platforms
---

### Post by erhard_eiselen on 2008-09-18
I have an Ubuntu server installed (7.10) which I upgraded to 8.04

Everything is working just fine, and the http_proxy setting that I put in /etc/bash.bashrc works fine for most tasks, that is if you are logged in.

As soon as you run a cron job, it does not know about the proxy - that is easy enough to sort out in the script file that is run by cron.

My real problem is with my LAMP installation. We have an Intranet site on the server on the Joomla platform. Everyhting works like a charm, but when you install an extension that must access an external website, again it does not seem to know about the proxy.

Surely there must be somewhere on the server where I can tell it to always use the proxy server (which is a different machine), so that all processes/task will automatically pick it up?

Please help!

---

### Post by RealPSL on 2008-09-19
Sounds like /etc/environment might do the trick for you.

[https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables")

As an example you would define the http_proxy variable in /etc/environment as 

```
http_proxy=squid.example.com:80
```

To do this you would open the file using gedit 
```
sudo gedit /etc/environment
```

---

### Post by erhard_eiselen on 2008-09-19
Thanks. I tried that, but does not work. However in the meantime I managed to find a workaround on [http://www.php.net/function.fsockopen](http://www.php.net/function.fsockopen)

---

