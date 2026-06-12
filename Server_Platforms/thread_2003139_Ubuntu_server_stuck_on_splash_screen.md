---
title: "Ubuntu server stuck on splash screen???"
date: 2012-06-13
forum: Server Platforms
---

### Post by HeroOfCanton on 2012-06-13
Setup an ubuntu 10.04 server for hosting subversion yesterday. Used dav with apache2 to allow access via url as per the instructions [here]("http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/http://"). Also added SSL and forwarded an SSL port to allow access from beyond the intranet.

Had everything up and running perfectly. Then today I ssh in and the system says a restart is required. So I restart... Try to access the url on the intranet and nothing. So I check apache. Not running and will not restart 

```
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
```Attached a monitor to the server and rebooted only to find what appears to be the Ubuntu **GUI** startup screen running indefinitely.  What the heck is going on here? Where is my CLI???

Note: I did install with "auto updates". Perhaps that was a bad plan?

---

### Post by LHammonds on 2012-06-13
A GUI is showing?  Do you have the installation CD still in the CDROM?

---

### Post by HeroOfCanton on 2012-06-13
Just the splash screen. The old 10.04 Orange bg with the four dots. Can't get past it to see what else is trying to load (although I can SSH in). Don't recall seeing that screen while the server boots before. Could be wrong though, since I don't actually see the servers boot very often.

No USB or CD's plugged in.

---

### Post by fuzzyworbles on 2012-06-13
i think the error apache2 is reporting means that another application is already listening on port 80. run 'sudo netstat -tlnp' to see what it could be.

---

### Post by HeroOfCanton on 2012-06-13
> **fuzzyworbles said:**
> i think the error apache2 is reporting means that another application is already listening on port 80. run 'sudo netstat -tlnp' to see what it could be.

It lists apache2 as the process. When I run status again and it says apache2 is not running. :confused:

---

### Post by HeroOfCanton on 2012-06-14
Okay, I'm an idiot... That was the normal boot screen. Guess I need to attach a monitor to the servers once in a while. :rolleyes:

Tracked the problem and eventually found it to be a known bug with password protected SSL certs. Must have just restarted apache instead of rebooting and didn't notice the bug before. Remade the cert and everything is good to go.

Thanks for the suggestions!

---

