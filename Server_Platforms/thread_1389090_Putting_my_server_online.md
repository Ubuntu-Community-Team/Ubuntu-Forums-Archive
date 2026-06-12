---
title: "Putting my server online"
date: 2010-01-23
forum: Server Platforms
---

### Post by humphreybc on 2010-01-23
I have a LAMP server setup with AjaXplorer that runs locally with a static IP address. All you have to do, if you're connected to our network, is go to:

```

http://192.168.1.2/AjaXplorer-2.5.4/

```

... and the AjaXplorer interface will appear.

Now I want to take the next step and make it available on the internet, so that I can access my files from anywhere in the world.

How do I go about doing this, and what precautions do I need to take?

---

### Post by HermanAB on 2010-01-24
Howdy,

Run 'ps -e' and confirm that you are not running unwanted insecure services such as VNC.  You can also do a scan using 'netstat' and stop everything that is not needed.  Run 'passwd' and set all user account passwords to something in excess of 9 characters - preferably at least 16 characters - and delete all other user unwanted accounts.

Then go to your router and forward port 80/TCP to your server.

Et voila!

---

### Post by Ryan Dwyer on 2010-01-24
Most of that information is unneeded. It doesn't matter if you're running VNC because you're only forwarding port 80. You don't need to change your local users passwords because Apache doesn't provide a Unix user login service.

You just need to ensure your Apache version is up to date and that your hosted code doesn't contain any potential exploits. Then forward port 80 and access your site from outside using your public IP.

---

### Post by humphreybc on 2010-01-24
And what permissions/owner should these folders be set to?

www-data (contains the AjaXplorer program)
/data (contains one heap of data)
/documents (contains another heap of data)

---

### Post by humphreybc on 2010-01-24
Hmm I followed these instructions on this page:

[http://portforward.com/english/routers/port_forwarding/Huawei/EchoLife-HG520s/Echolink.htm](http://portforward.com/english/routers/port_forwarding/Huawei/EchoLife-HG520s/Echolink.htm)

Except instead of opening up the ports they suggest, I followed your advice and opened port 80.

Now I can't connect to the router again (it gave me some message like "your local something will change to port 80:80 if this is successful)

How can I test if it's worked? How do I connect to my router?

---

### Post by humphreybc on 2010-01-24
Nevermind, I'm stupid - worked it out.

Instead of 192.168.1.1 for my router, it's now 192.168.1.1:8080

And my server should be accessible from [http://118.93.48.233/AjaXplorer-2.5.4/](http://118.93.48.233/AjaXplorer-2.5.4/)

Although I just want to confirm what my permissions should be set to.

---

### Post by humphreybc on 2010-01-24
Oh will I need a static IP address from my ISP?

---

### Post by BkkBonanza on 2010-01-24
That will likely cost you money. You can use a service like dyndns.com and configure your router to update using dynamic dns. It updates your dns when an ip change occurs. You will have a possible few minute downtime during ip changes but mostly it works ok. Keep the dns ttl values low and they will change over quicker. Most dns services and registrars offer some dynamic dns function so check yours.

---

### Post by humphreybc on 2010-01-24
Thanks,

I can't get it to work. It's listening on ipv6 but not ipv4.

```

benjamin@benjamin-server:/etc/apache2/sites-enabled$ ls
000-default
benjamin@benjamin-server:/etc/apache2/sites-enabled$ sudo nano /etc/apache2/sites-enabled/000-default 
benjamin@benjamin-server:/etc/apache2/sites-enabled$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 localhost:7634          *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     3104     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     2525     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     4012     /var/run/mysqld/mysqld.sock

```

---

### Post by humphreybc on 2010-01-24
Ugh, it was the router firewall. All working now.

Time to try out this dyndns thing!

---

