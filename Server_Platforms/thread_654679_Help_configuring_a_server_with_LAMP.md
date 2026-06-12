---
title: "Help configuring a server with LAMP"
date: 2007-12-31
forum: Server Platforms
---

### Post by jtsai256 on 2007-12-31
Hello all! 

I've been a long-time fan of Ubuntu, but only now getting into the whole LAMP thing. 

In any case, I have everything set up using tasksel, and I can access everything through localhost. I was wondering how I can set up this server so that other computers on my network can also connect to this server and access phpmyadmin as well as the mysql database, while still not allowing the public to access my server until I'm ready. Is this a possibility?

Thanks for the help!

---

### Post by obrient on 2007-12-31
If you have the LAMP server set up with a static IP you can easily type that IP address into your web browser and you should be able to see the machine including PHPMyADMIN.

It wouldn't be open to the public unless you allow outside requests to the machine through your router.

---

### Post by jtsai256 on 2007-12-31
Thanks for the reply. I just figured out my static IP address using ifconfig.

---

