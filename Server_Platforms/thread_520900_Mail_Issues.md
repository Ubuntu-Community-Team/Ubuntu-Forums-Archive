---
title: "Mail Issues"
date: 2007-08-08
forum: Server Platforms
---

### Post by scorpiox on 2007-08-08
Hi 
I have my server, with Ubuntu, and its got all the stuff installed ready to use. My big issues at the moment are BIND, which i dont know how to config, and mail (EXIM) which i dont know anything about at all. I jsut cant make it work, either of them
The server is running 6LTS and has Webmin present just for config, i manually installed everything else. What i need to do it get DNS working to create teh zones, and mail working for a single account, and possibly a few forwarders. I followed instructions and made an exim database, and modified the exim.conf, but further than that im really stuck, I dont know how to setup the accounts.
All i want to do it be able to move my domain onto the server, which is setup for any domain to goto /var/www and for it to work.
Can anyone help? I would really really appreciate it :)

---

### Post by scorpiox on 2007-08-08
Just as an update - i installed the stuff using the following tutorial :)

[http://www.xmn-berlin.de/~marte/exim/exim4_mysql_amavis_spamassasin.html](http://www.xmn-berlin.de/~marte/exim/exim4_mysql_amavis_spamassasin.html)

---

### Post by foxylad on 2007-08-08
I seriously recommend ditching BIND - it is a complex beast, and most admins use it so infrequently they have to re-read teh manual each time. Most domain registrars now offer full DNS services for free with the domain name, and you can do weird internal network stuff by hacking your hosts file.

---

### Post by scorpiox on 2007-08-09
im With Compila, i dont know how to setup that. Im getting to the point where i would give someone some $ to teach me how to setup mailer - i need it in the next few days. Im really desperate, please help!! 
Thanks

---

