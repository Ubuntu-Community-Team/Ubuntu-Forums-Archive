---
title: "Apache Problem!"
date: 2005-12-15
forum: Server Platforms
---

### Post by nformosa on 2005-12-15
HI all,

I have installed the new Ubuntu Server 5.10 and it should be used as a web server (apache + php5 + mysql). I installed everything though i'm having trouble to access the server. Its very slow and mainly results in an error page. My main thought is the iptables.

Can someone pls tell me how to setup the iptables to accept connections to and fro on port 80? plus how to save the configuration so on the next boot up the settings are ready!

Also i have run netstat -a and the only ports availble on tcp are 21, 25 and mysql port. The port 80 is only seen on tcp6?!which i don;t actually use yet!


Thanks for any help
Nick

---

### Post by diebels on 2005-12-15
[QUOTE=nformosa]HI all,

I have installed the new Ubuntu Server 5.10 and it should be used as a web server (apache + php5 + mysql). I installed everything though i'm having trouble to access the server. Its very slow and mainly results in an error page. My main thought is the iptables.[/quote]Share the errors with us. If you are getting an error page(web page), then nothing's wrong with iptables is my guess.

---

### Post by Liberteh on 2005-12-15
diebels is right. try to ping your server, and show us the output. and its also wise to just open port 80.

---

