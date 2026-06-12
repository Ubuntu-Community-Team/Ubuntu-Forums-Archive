---
title: "Trying to set up my server, despite difficulty"
date: 2013-05-28
forum: Server Platforms
---

### Post by TheMattVid on 2013-05-28
I am currently following these instructions to set up Multicraft on my Ubuntu server using Putty:
[http://www.creativetux.com/2013/03/multicraft-installation-on-ubuntu-1210.html](http://www.creativetux.com/2013/03/multicraft-installation-on-ubuntu-1210.html)

I am up to the part where it wants me to open a browser and type in myserverip:8015.
This just brings a page that never finishes loading, making me think that I did not set something up correctly. Are there any directions in these steps that I may have missed? What can I do to make this work?

---

### Post by darkod on 2013-05-29
There is not much in those instructions.
Did you try pinging the server IP? Do you get a reply back?

If you enabled the ufw firewall, did you open the necessary port(s)?

---

### Post by Simon_WM on 2013-05-29
I Would suggest you look at Spacebukkit, [http://spacebukkit.xereo.net/](http://spacebukkit.xereo.net/)
 As its a clean and simple install, Which only need

apache2
mysql-server
phpmyadmin

openjdk-6-jre

Also if you'r using UFW, you need to make sure that you have allowed the port though the firewall, 
and then connect though yourip:port

---

### Post by TheMattVid on 2013-05-29
> **darkod said:**
> There is not much in those instructions.
Did you try pinging the server IP? Do you get a reply back?

If you enabled the ufw firewall, did you open the necessary port(s)?

Yes, I did get a reply when I pinged my server ip.
What are the ports that I need to open up?

---

### Post by darkod on 2013-05-29
If you are trying [http://myserverip:8015](http://myserverip:8015) that means port 8015 as minimum. That tutorial mentions port 8040 too, in case you are using it you need to open it too.

---

### Post by TheMattVid on 2013-05-29
> **darkod said:**
> If you are trying [http://myserverip:8015](http://myserverip:8015) that means port 8015 as minimum. That tutorial mentions port 8040 too, in case you are using it you need to open it too.
Okay, I have the port 22 open (like that tutorial said) and I have also opened up 8015 and 8040. When trying [http://myserverip:8015](http://myserverip:8015) it results in a page stating:[h=1]Not Found[/h][COLOR=#000000][FONT=Times New Roman]The requested URL / was not found on this server.[/FONT][/COLOR]

---

### Post by TheMattVid on 2013-05-29
I also just realized that when typing in apache2ctl graceful, it give the error:
apache2: Could not reliably determine the server's fully qualified domain name, using 76.72.174.175 for ServerName
[Date] [warn] NameVirtualHost *:8015 has no VirtualHosts

---

### Post by TheMattVid on 2013-05-29
Is this tutorial better, or is the other one better?
[http://www.multicraft.org/site/page?view=hylianux](http://www.multicraft.org/site/page?view=hylianux)

---

