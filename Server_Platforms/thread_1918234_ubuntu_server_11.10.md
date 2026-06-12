---
title: "ubuntu server 11.10"
date: 2012-01-31
forum: Server Platforms
---

### Post by paulwilson5x on 2012-01-31
totally new to ubuntu, im setting up a ubuntu server 11.10 on my laptop for a college project. i have my laptop connected to my home router by ethernet cable. i am trying to view a test php file on a desktop pc with is connected to the router by wireless. what networking conditions must i set up on the laptop server, router and desktop pc.

---

### Post by lisati on 2012-01-31
*Thread moved to **Server Platforms**.*

Once you have your server up and running, you can open your favourite browser on any machine on your local network and put the server's IP local address in the browser's address bar.

---

### Post by kindledwind on 2012-01-31
Dig through this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Also:
-typing "ifconfig" at the server command prompt will tell you the IP address of the server.
-ping the server IP from the windows (terminal) machine. That would verify basic connectivity between them.
-in the ubuntu.com tutorial, it says to visit [http://localhost](http://localhost) from the Ubuntu machine...that's not too graceful from a server terminal. Visit [http:///192.168.0.1](http:///192.168.0.1) (substitute the server IP) from the windows machine instead.
-if you do the LAMP setup, the default directory for html & php files is /var/www on the Ubuntu box.
-if you don't like the /var/www idea, check out the files in /etc/apache2/sites-enabled & write your own.
-check out ufw as well on the ubuntu machine. You might be interested in some firewall rules to keep web spiders from indexing your site & indexing your Ubuntu machine for the interweb.
-learn the a2ensite & a2dissite stuff...along with other a2 directives.

That should be enough to get you started...the network configuration should only have to allow port 80 between the server & the windows machine. Unless you've done some config in the router, it probably already does.

---

### Post by shumifan50 on 2012-01-31
If this is your first venture into Ubuntu, I would suggest using 10.04 as I have had some unpredictable behaviour on 11.10 on networking, with occasional freezes. These don't happen on 10.04.

---

### Post by arrrghhh on 2012-01-31
> **shumifan50 said:**
> If this is your first venture into Ubuntu, I would suggest using 10.04 as I have had some unpredictable behaviour on 11.10 on networking, with occasional freezes. These don't happen on 10.04.

I would echo this, but state even stronger - servers should **always** be setup on LTS releases, for various reasons... one listed above ;).

---

