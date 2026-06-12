---
title: "Apache Questions"
date: 2008-01-22
forum: Server Platforms
---

### Post by dethredic on 2008-01-22
Ok, I just got my server up and running, and I have a couple questions.

When it first started working, I got the "It Worked!"

I went to /etc/apache2/apache2.conf and changed the server root to a folder I made on my desktop.

I then reloaded the page, and nothing changed. I restarted apache and still nothing. I the went /var/www/ and deleted the files there and added mine. I then restarted apache, and now I get a "Forbidden - permission to access /index.html on this server.

So, that raises two questions. Why did my web root not change, and why do I not have permission anymore?

Another question, when I type in my external IP into my address bar on a different computer, shouldn't I be able to view my site? (I can't do that) It just tries to connect for a while until it gives up. Will I need to forward a port on my router? (80 maybe)

---

### Post by ericbarch on 2008-01-22
Honestly, I would suggest keeping your webroot in /var/www/. You can make a link to it on your desktop if you wish (ln -s). If you really want to change it, make sure to go through your entire conf file. The Virtual Host probably needs to be changed to reflect the new directory.

About the permissions, your index.html probably belongs to your user account and is not set to be world readable (i.e. the webserver user can't access the file to serve it). If you run the command 'chmod 755 /var/www/index.html' that will set your index file to be readable by anyone but only allow you to write to it.

HTTP servers run on a default port of 80, so that would be the port to forward in your router. However, many ISPs like to block this port so you may have to settle for another port.

---

### Post by dethredic on 2008-01-22
Well, I tried port 80 (I remember I used it before)

Ok, after doing a lot of fiddling around in my router, I could not figure anything out. No connections from the outside work!!!

---

### Post by freebeer on 2008-01-22
You need your server to have a static IP so that your port-forward rules actually forward to the right machine.  Then set up those rules to forward to that IP.

It's not absolutely clear in your message... are you trying to access the server from OUTSIDE the local network, or INSIDE the network.  If inside, you need to use the internal address of the server, not it's public address.  (You probably already know this, but it wasn't clear in your message so I thought I'd toss out the idea.) ;)

---

### Post by dethredic on 2008-01-23
> **freebeer said:**
> You need your server to have a static IP so that your port-forward rules actually forward to the right machine.  Then set up those rules to forward to that IP.

It's not absolutely clear in your message... are you trying to access the server from OUTSIDE the local network, or INSIDE the network.  If inside, you need to use the internal address of the server, not it's public address.  (You probably already know this, but it wasn't clear in your message so I thought I'd toss out the idea.) ;)

Well, I have Ubuntu set for a static IP.

I want to be able to access the server from everywhere, inside and outside the network.

---

### Post by dethredic on 2008-01-23
Ok, I can access the server on another computer inside my LAN, using it's local IP (192.168.x.xxx).

---

### Post by cdenley on 2008-01-23
Then it's just a matter of configuring your router. If you have port forwarding enabled, and your ISP isn't blocking it, people can access it over the internet with your WAN IP. Depending on your router and your router configuration, you may not be able to access it from your LAN using your WAN IP.

---

### Post by dethredic on 2008-01-23
Ok, I was able to plug my modem directly into my server and here are my results.

When I was directly hooked up to my router I did an Ifconfig.

my local IP changed from 192.168.1.137 to 24.57.208.24. I would have expected it to change to my external IP of 24.57.233.201. I then checked my external IP and it changed to 24.57.208.24. I re did the connection to check this was accurate, and it is.

Now, when directly connected to the modem my friend could type in 24.57.208.24 and he could see my site. So, the problem is 100% in my router. I will try to forward port 24.57.208.24

So, if I am hooked up directly to the modem my server works, and my IP changes. I need the router, or I won't have other internet... So, I am going to go back to the default Linksys firmware and see what I can do with that.

---

### Post by freebeer on 2008-01-23
Well that's good news... your ISP isn't blocking port 80, so it's just a matter of getting those ports forwarded properly. :)

Another thing you might want to consider: a dynamic domain name.  You can get free ones from DynDNS and others.  This way the outside world can just use "www.yourdomainname.org to connect and not have to mess with IP addresses.  And if your IP address changes (as it appears to have happened during your test), you can run a script that checks for changes, then updates dynDNS of the change automatically thereby keeping your domain name pointed to the current address.

---

