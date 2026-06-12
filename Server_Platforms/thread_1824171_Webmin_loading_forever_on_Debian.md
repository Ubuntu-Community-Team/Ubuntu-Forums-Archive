---
title: "Webmin loading forever on Debian"
date: 2011-08-13
forum: Server Platforms
---

### Post by ziyanpowa on 2011-08-13
Hi,

I've installed the latest Debian (with net install cd) to my old notebook (pentium 3 1ghz, 256mb ram). I didn't install any window manager on it, just the 'Standard system', and the 'Laptop' packages. After the installation competed, i installed webmin using [Webmin APT repository]("http://www.webmin.com/deb.html"). Now, when i put [https://192.168.1.103:10000](https://192.168.1.103:10000) (103 is my notebook's ip address), Firefox just shows 'Connecting...' forever. Without https, it displays the following message, so i assume webmin is installed correctly:

Error - Bad Request

This web server is running in SSL mode. Try the URL [https://192.168.1.103:10000/](https://192.168.1.103:10000/) instead.


Any ideas? :confused:

---

### Post by allwimb on 2011-08-13
Could you access it using localhost as address? If yes that mean that you got a firewall that that's blocking the 192.168.1.103

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by ziyanpowa on 2011-08-13
I installed lynx (terminal browser) to the machine, and it works on localhost... :-? I tried it without windows firewall, and on another machine: still "Connecting...", or 'Waiting for..." forever, after accepting the certificate. It may be my router, but putty (ssh), is working well, and the following message appears too if i only put http, not https:
This web server is running in SSL mode. Try the URL [https://192.168.1.103:10000/](https://192.168.1.103:10000/) instead.

I set SSL=0 in /etc/webmin/miniserv.conf, and restarted webmin. There's no  message now, it's just connecting forever with http mode too... :(

---

