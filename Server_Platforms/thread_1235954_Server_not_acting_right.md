---
title: "Server not acting right"
date: 2009-08-09
forum: Server Platforms
---

### Post by k33bz on 2009-08-09
My LAMP server was working fine today, this morning anyhow. After I got off of work I went to go access the webpage, and for some reason it does not show online at all. I can still get to my server VIA ssh. But it will not load any pages VIA internet. I am not even sure were to start right now.

I checked my Local as well as my Broadcasting IP address, all is still the same. As I even know that it is not time to renew my domain name.

Can someone please help. I am losing money as I write.

Have also just noticed that although I can ssh to my server, the server itself can not access the internet.

---

### Post by wirelessmonkey on 2009-08-09
Make sure your system has proper dns settings, 
```

cat /etc/resolv.conf

```

Then restart apache and watch for errors, and watch the apache error log.
```

/etc/init.d/apache2 restart

tail -f /var/log/apache2/error.log


```

---

### Post by k33bz on 2009-08-09
> **wirelessmonkey said:**
> Make sure your system has proper dns settings, 
```

cat /etc/resolv.conf

```

Then restart apache and watch for errors, and watch the apache error log.
```

/etc/init.d/apache2 restart

tail -f /var/log/apache2/error.log


```
All is the same, but here is the print out.

cat /etc/resolv.conf

```
namesever 192.168.1.3
```
which is the local ip addy for my server

sudo /etc/init.d/apache2 restart
```
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

```
It has always done that though, and has worked.

tail -f /var/log/apache2/error.log
```
[Sun Aug 09 07:57:57 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Aug 09 17:35:57 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Aug 09 17:41:21 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Aug 09 17:41:31 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Aug 09 18:09:23 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Aug 09 18:09:33 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Aug 09 18:12:20 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Aug 09 18:12:30 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations

```

---

### Post by wojox on 2009-08-09
Just pinged port 80 and got nothing. Got a firewall or router problem? Any updates lately?

PING 24.116.105.148 (24.116.105.148) 56(84) bytes of data.

--- 24.116.105.148 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4007ms

---

### Post by k33bz on 2009-08-09
> **wojox said:**
> Just pinged port 80 and got nothing. Got a firewall or router problem? Any updates lately?

PING 24.116.105.148 (24.116.105.148) 56(84) bytes of data.

--- 24.116.105.148 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4007ms

No I have not had any updates lately, And there has not been any router or firewall problems, as said I could access my website VIA http this morning before I left for work, when I got back, I can no longer access it through HTTP but can still access it through ssh. The server can not access the Internet at all.

as for 24.116.105.148, all my computers share that IP, my laptop, desktop, xbox, server, wifes laptop and kids computers.

---

### Post by k33bz on 2009-08-09
My server is now able to connect to the internet as well as ping. However I am still unable to connect to my server VIA HTTP.

Any ideas?

---

### Post by k33bz on 2009-08-09
ok, this has been fixed, should of thought about rebooting my router to begin with. Thanks to all that helped.

---

