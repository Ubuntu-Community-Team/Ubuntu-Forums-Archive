---
title: "Apache dead after power flicker"
date: 2008-11-02
forum: Server Platforms
---

### Post by R.Bucky on 2008-11-02
My 7.10 Ubuntu server times out for my domain [http://buckyspalace.net](http://buckyspalace.net). I had a momentary power flicker (yes, behind a surge protector), which did not turn off my server. Now, I am unable to view my web pages. 

I have checked error.log and access.log with nothing out of the ordinary. Apache httpd is running. I took the liberty of restarting my machine with no success. Additionally, I restarted my modem and router.

Any suggestions?

~Mark

---

### Post by HermanAB on 2008-11-02
Before testing Apache, you need to ensure that the lower level stuff is working.

See whether you have an IP address
$ sudo ifconfig

See whether you have a default route to your gateway:
$ sudo route

See whether you can Ping something:
$ ping [www.yahoo.com](www.yahoo.com)

By now you should have a better idea of where the problem lies.

Cheers,

Herman

---

### Post by R.Bucky on 2008-11-02
Yup, all responses appear as they should be. Connectivity is not a problem. I am uploading a torrent now... This same problem occurred in the past. The solution was a fresh start. That was not desirable.

---

### Post by cariboo on 2008-11-02
Do you get any error messages when you restart apache2, at the prompt type:

```
sudo /etc/init.d/apache2 restart
```

note if their are any error mesaages.

Jim

---

### Post by lykwydchykyn on 2008-11-02
Post the outputs of 
```

sudo netstat -tunap
sudo iptables -L

```
On the server.  

I ran a port scan on your URL and port 80 is being filtered.  I see several possibilities here:
 - Your modem or router got reset, and your port forwarding/firewalling settings got reset
 - If you're using a dynamic DNS service, your public IP may not have been updated correctly.  (is the WAN ip on your modem 24.18.97.15?)
 - Something is setting up an iptables firewall on reboot.

Check those things out.

---

