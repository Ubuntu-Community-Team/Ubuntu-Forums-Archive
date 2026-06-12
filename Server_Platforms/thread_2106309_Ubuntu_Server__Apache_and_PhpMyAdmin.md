---
title: "Ubuntu Server / Apache and PhpMyAdmin"
date: 2013-01-18
forum: Server Platforms
---

### Post by chrisguk on 2013-01-18
I have a DNS server running.  Everything works on the BIND9 setup as desired after completing the basic NSLOOKUP checks.

Now I want to take it a step further.  I have installed the LAMP stack with PHPMyAdmin.

Traditionally if I installed LAMP on a desktop I could just navigate to phpmyadmin like so:

```
http://localhost/phpmyadmin
```

So now I have this lot stored on the server I want to access phpmyadmin from a client on the network.

If I type in the browser:

```
http://192.168.178.130
```

I get the default "It Works!" page.

When I navigate to:

```
http://192.168.178.130/phpmyadmin
```

It downloads a file and doesnt display the login page.

Any ideas?

---

### Post by SeijiSensei on 2013-01-19
As a first step, make sure the libapache2-mod-php5 package is installed.

What if you navigate to [noparse]http://www.example.com/phpmyadmin/index.php[/noparse]?

---

### Post by chrisguk on 2013-01-19
Hi,

Thanks for the tip.  

That wasn't the issue though.  I mis-configured my DNS server.

This has been fixed now but thank you.

---

