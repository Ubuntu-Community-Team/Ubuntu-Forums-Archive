---
title: "Setting up LAMP manually"
date: 2012-04-06
forum: Server Platforms
---

### Post by roffisserver on 2012-04-06
I Googled how to set up LAMP and when I tried to test apache( Type in [http://localhost/](http://localhost/)) Firefox said unable to connect. When I was looking though the command the computer ran it said "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for Servername". Could this be I have not setup a static IP? If it is I need some help setting it up. 
     
                                                                                       Thanks for the help,
                                                                                                                        Roffis

---

### Post by Cheesemill on 2012-04-06
How did you set up LAMP?

The 'Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for Servername' is just a warning, you should still have access on [http://localhost](http://localhost)

Assuming that you meant 127.0.0.1 instead of 127.0.1.1 in the error, otherwise something is very strange indeed.

---

### Post by darkod on 2012-04-06
The localhost is the machine you are running the command onto. If you installed a server machine, and type localhost on your desktop, it will report an error because it is looking for apache on your desktop.

To set a static IP on your server, if you didn't do it during the installation, you need to open /etc/network/interfaces with for example:
sudo nano /etc/network/interfaces

The static IP setup would look something like:
```
auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask 255.255.255.0
   gateway x.x.x.x
```Put in the IP you want and the gateway you use (usually your router IP like 192.168.1.1).

Also, if DNS servers need to be set up manually, they are in /etc/resolv.conf

You can also edit them with nano editor.

If you haven't used nano before, the most often used commands for me, are:
After you finish editing, press Ctrl + O to save.
Press Ctrl + X to exit.

EDIT: Just to add. If you installed LAMP on your desktop machine, [http://localhost](http://localhost) should work. If it doesn't, something went wrong.
If you installed a server machine (because you were asking about CLI in another thread), you need to test with your server IP like [http://192.168.1.x](http://192.168.1.x).

---

### Post by mikaelcrocker on 2012-04-06
I'm going to say that localhost should work, and like said above, localhost should be 127.0.0.1  You may also want to check where the directory is looking by default. such as is it /var/www or a different place that apache may specificy.

---

### Post by roffisserver on 2012-04-06
Thanks really helped! I set up LAMP and it works great. I also set up a static ip.:p:p:p

---

### Post by roffisserver on 2012-04-06
I know it said 127.0.1.1 Cheesemill

---

