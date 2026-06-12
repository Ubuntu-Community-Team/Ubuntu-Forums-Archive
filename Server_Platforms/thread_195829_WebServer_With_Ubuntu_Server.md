---
title: "WebServer With Ubuntu Server"
date: 2006-06-13
forum: Server Platforms
---

### Post by Isoss on 2006-06-13
I installed Ubuntu Server on my PC with the IP 192.168.0.1
Then I installed apache, php, mysql and openssh server and all the packages related. 

Everything is set right, I can use mysql -u root -p and use databases, I can SSH from my laptop to any folder on the server ... I have my websites files in /var/www and I have SSH access to it also.

Now, how can I view the localhost of the server using firefox on my laptop?
I tried [http://192.168.0.1](http://192.168.0.1) and didn't work. I checked port 80 and it's open ... I checked that apache is working and still can't connect to localhost at 192.168.0.1 .

Anyone knows the solution?

Thanks in advance.

Isos

---

### Post by jimbren on 2006-06-13
When you say "it didn't work," what did you see?

Have you tried restarting apache?

```
sudo /etc/init.d/apache2 restart
```

---

### Post by Randomskk on 2006-06-13
Can you access the server from the server itself?
If you have no desktop on the server, try this command:
wget [http://localhost](http://localhost)

It should download your index.html or whatever else Apache serves up.

If you can access the web server on the server, but not on the laptop, check no firewall rules are in the way and check Apache is listening on the external network address (192.168.0.1).

---

### Post by skafiskafnjak on 2006-06-13
type ifconfig and see which local IP is assigned to your server than open your router and open port 80 for that IP.

Than type in: [http://yourIP](http://yourIP) or [http://yourlocalIP](http://yourlocalIP)

---

### Post by Isoss on 2006-06-16
I solved it! it was the browser. I went to firefox Edit->Preferences ->Connection Settings and I added 192.168.0.1 Where it says: No Proxy For: localhost, 127.0.0.1 ... 
Thanks for your help.

---

