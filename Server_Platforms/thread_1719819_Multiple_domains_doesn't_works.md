---
title: "Multiple domains doesn't works"
date: 2011-04-02
forum: Server Platforms
---

### Post by Kozley on 2011-04-02
Hi!

I'm following howto instruction by [http://library.linode.com/lamp-guides/ubuntu-10.04-lucid/#configure_virtual_hosting](http://library.linode.com/lamp-guides/ubuntu-10.04-lucid/#configure_virtual_hosting)
I cannot get sites working. Anyone know how do this solution?

---

### Post by volkswagner on 2011-04-02
You need to provide more information.

Did you setup the DNS records at your registrar?

Are your sites enabled?
```
ls -alt /etc/apache2/sites-enabled
```

Do you get any errors in logs or when restarting apache2?

What exactly is not working?  What happens when you navigate to your linode ip address in a browser?

---

### Post by Kozley on 2011-04-02
> **volkswagner said:**
> You need to provide more information.

Did you setup the DNS records at your registrar?

Are your sites enabled?
```
ls -alt /etc/apache2/sites-enabled
```Do you get any errors in logs or when restarting apache2?

What exactly is not working?  What happens when you navigate to your linode ip address in a browser?

Yes, I did setup the DNS record. All my sites is already enabled:
```
totalt 8
drwxr-xr-x 2 root root 4096 2011-04-02 18:24 .
lrwxrwxrwx 1 root root   40 2011-04-02 18:24 firstsite.com -> ../sites-available/firstsite.com
lrwxrwxrwx 1 root root   30 2011-04-02 18:24 anothersite.com -> ../sites-available/anothersite.com
drwxr-xr-x 7 root root 4096 2011-04-02 18:20 ..
lrwxrwxrwx 1 root root   26 2011-04-02 17:55 000-default -> ../sites-available/default
```
I don't see any error on the error log. Exactly problem is what it is both loclamachine and outsite localmachine to domain can't found and also [http://localhost](http://localhost) tell me it's error "Not Found"

---

### Post by Adrianna_2 on 2011-04-02
are you behind a router ? .. Have has looked into /etc/network/interfaces  to see the network interfaces available on your system,  and /etc/hosts for yours domain-names and IPv6 capable hosts ?

---

### Post by volkswagner on 2011-04-02
No I'm really confused.

What is your setup?  You are following a how-to for Linode which is an Online VPS provider, yet you mention localhost?

Please explain your setup (where is your server, what OS, etc.).

You can change the /etc/apache2/ports.conf to:
```
Listen 80

```

Then restart apache.

---

### Post by Kozley on 2011-04-02
> **Adrianna_2 said:**
> are you behind a router ? .. Have has looked into /etc/network/interfaces  to see the network interfaces available on your system,  and /etc/hosts for yours domain-names and IPv6 capable hosts ?

Yes, I'm behind a router. I'm not using IPv6 and having did on etc/hosts but it does work only on localmachine.

> **volkswagner said:**
> No I'm really confused.

What is your setup?  You are following a how-to for Linode which is an Online VPS provider, yet you mention localhost?

Please explain your setup (where is your server, what OS, etc.).

You can change the /etc/apache2/ports.conf to:
```
Listen 80

```Then restart apache.

I'm really sorry because my english is not so good. Listen 80 on ports.conf is default. Server is at my home and OS is Ubuntu 10.04 Desktop Edition. All setup on DNS record is correct if I'm not using vhosts and it works. Apache2 is latest version. Oops, I didn't see VPS there so I need help to another soluation to correctly vhosts and all sites should works.

---

### Post by Kozley on 2011-04-02
Sorry for double post. I found [the post]("http://ubuntuforums.org/showthread.php?p=10016541") by SeijiSensei. That's only solve my problem to show both sites and it seems works now but it is a problem about redirecting. When I enter [www.anothersite.com]("http://www.anothersite.com") and it redirect to [www.firstsite.com]("http://www.firstsite.com"). How could this happen?? :(

EDIT: Now it works! I did just disable default site.

---

### Post by volkswagner on 2011-04-02
EDIT: Redundant.... took to long to post... OP fixed it!

---

