---
title: "Web server network selection"
date: 2013-02-05
forum: Server Platforms
---

### Post by Izzzy9999 on 2013-02-05
I'm running a small server hosting 2 websites with Apache2 on Ubuntu 12.10.

The server has 2 network cards each connected to a different router. Each router has it's own internet connection, 1 personal and 1 business. I'd like to force webserver1 to use the personal internet connection and webserver2 to use the business internet connection for out going requests. I don't want webserver2 using my personal internet connection. Apache2 VirtualHosts for each webserver are set to listen on 2 different domains but how do I know that the outbound requests made by either server is using the proper network connection?

Thanks

---

### Post by SeijiSensei on 2013-02-05
You need to bind the virtual servers to the two network addresses like this.

```

<VirtualHost 10.10.10.10:80>
[definition of virtualhost one]
</VirtualHost>

<VirtualHost 192.168.1.1:80>
[definition of virtualhost two]
</VirtualHost>

```

You can put these in separate files in /etc/apache2/sites-available, or put them together into one file.

---

### Post by Izzzy9999 on 2013-02-10
> **SeijiSensei said:**
> You need to bind the virtual servers to the two network addresses like this.

```

<VirtualHost 10.10.10.10:80>
[definition of virtualhost one]
</VirtualHost>

<VirtualHost 192.168.1.1:80>
[definition of virtualhost two]
</VirtualHost>

```

You can put these in separate files in /etc/apache2/sites-available, or put them together into one file.

Thanks I'll give that a shot.

---

