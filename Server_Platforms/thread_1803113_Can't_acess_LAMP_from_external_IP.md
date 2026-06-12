---
title: "Can't acess LAMP from external IP"
date: 2011-07-12
forum: Server Platforms
---

### Post by leomoon on 2011-07-12
Hello,

I'm having a very strange problem. The LAMP server works in local network but when I try over the internet, browser says connection was reset...

I installed Ubuntu Desktop 11.04 and then I installed LAMP using tasksel.

I ONLY setup passwords and the rest of the LAMP configuration is default. Server's internal IP is 192.168.0.116 and I forwarded private port 80 of 192.168.0.116 to 8081. I also checked if the port 8081 is open using "canyouseeme.org" and it was open.

When I go to the external IP with the forwarded port, (xxx.xxx.xxx:8081) it says the connection was reset!!!

I'm out of ideas. Can someone please tell me what am I missing here?

---

### Post by doas777 on 2011-07-12
are you trying to connect to a subdomain like **www**.domain.com ? 
if so, make sure your public dns registration points both hosts to the same server. not somthing that would usually come up on the lan. 
some people recommend changing "max_execution_time" to 500 in my php.ini, but I would only do that if the error takes a few seconds to show.

[http://www.apachefriends.org/f/viewtopic.php?f=16&t=43736](http://www.apachefriends.org/f/viewtopic.php?f=16&t=43736)
[http://forum.hostican.com/virtual-private-servers-VPS-f9/how-to-troubleshoot-the-connection-with-the-server-was-reset-t959/](http://forum.hostican.com/virtual-private-servers-VPS-f9/how-to-troubleshoot-the-connection-with-the-server-was-reset-t959/)

---

### Post by leomoon on 2011-07-12
I'm accessing it through a dyndns account so it is a subdomain but even if I access it using the external IP it still says connection was reset.

This is very frustrating!

---

### Post by leomoon on 2011-07-13
Anybody?

---

### Post by spynappels on 2011-07-13
Is Apache listening on port 80? or on port 8081?

You need to forward this port FROM your router TO your LAN IP, the way you describe it in the OP sounds like you did it the other way about?

---

### Post by leomoon on 2011-07-13
Thanks for your reply.

I didn't change anything in LAMP configuration. The only thing I did was making a password for mysql. So by default apache should be listening to port 80. Shouldn't it?

I also tried to reverse the port forwarding and when I did, it said connection timeout. So I think the way I had it was the correct way. So I changed it back to what it was:
[IMG]http://dl.dropbox.com/u/3053521/_img/portforwarding.jpg[/IMG]

I think there is a configuration missing in apache and I don't know what it is. And the interesting part is that everything works locally!

---

### Post by csdco on 2011-07-13
"forwarded private port 80 of 192.168.0.116 to 8081"

Why are you setting up port forwarding like this within the server?

**You need to forward port 80 on your router to port 80 of your machine's internal IP.**

---

### Post by leomoon on 2011-07-13
It's because port 80 is blocked by ISP. So I'm saying if someone accessed port 8081, router will send it to port 80 on that machine. I did the same thing with a Windows XP and XAMPP and it worked perfect. But LAMP is missing some sort of configuration.

---

### Post by linuxnizer on 2011-07-13
also, make sure that apache is listing on ALL IPs.

type "netstat -nlpt"

put the results here

also, does [http://localhost](http://localhost) work?

---

### Post by leomoon on 2011-07-13
Here is the result:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      732/mysqld      
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2827/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      408/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1042/cupsd      
tcp6       0      0 :::139                  :::*                    LISTEN      505/smbd        
tcp6       0      0 :::22                   :::*                    LISTEN      408/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1042/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      505/smbd        



Yea. Localhost works just fine. Even if I access the server's IP from another computer in the network, it will work.

---

### Post by linuxnizer on 2011-07-13
good, it's not your linux server :)...
it's routing issue with your router...

do "ifconfig -v" and post results here.

99% it's your router...but just to be sure.

---

### Post by linuxnizer on 2011-07-13
also, have you tried using [http://ROUTERIP : port]("http://ROUTERIP:PORT") to access your box from outside?

---

### Post by linuxnizer on 2011-07-13
> **leomoon said:**
> 

I ONLY setup passwords and the rest of the LAMP configuration is default. Server's internal IP is 192.168.0.116 and I forwarded private port 80 of 192.168.0.116 to 8081. I also checked if the port 8081 is open using "canyouseeme.org" and it was open.


wait a sec...what do you mean by ( I forwarded private port 80 of 192.168.0.116 to 8081)?!!
Did you play with the routing table on your linux box?

---

### Post by leomoon on 2011-07-13
Ok so here is what's going on.

I installed LAMP in Ubuntu using tasksel. I didn't change anything in Ubuntu or in LAMP. Everything is default.

My ISP blocks port 80 and I have a router behind this Ubuntu server. Ubuntu's local IP is 192.168.0.116. I used my router to forward port 80 of Ubuntu server to 8081 of public. Which should technically work. Cuz I tried this method with Windows XP with XAMPP and it works both locally and using router's IP (external IP).

I also tried to access the server using router's IP with 8081 port in front of it (xxx.xxx.xxx:8081) and it still says connection was reset.

This is the result of ifconfig -v:
eth0      Link encap:Ethernet  HWaddr 00:0c:29:de:c6:5a 
          inet addr:192.168.0.116  Bcast:192.168.0.127  Mask:255.255.255.128
          inet6 addr: fe80::20c:29ff:fede:c65a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:219257 (219.2 KB)  TX bytes:14949 (14.9 KB)
          Interrupt:19 Base address:0x2000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by linuxnizer on 2011-07-13
ok, what does "netstat -nr" report?

---

### Post by linuxnizer on 2011-07-13
also, can you browse the net from your linux box?

---

### Post by leomoon on 2011-07-13
Yea the linux machine can browse internet.

netstat -nr report:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.128 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by linuxnizer on 2011-07-14
Ok, routing seems fine, although unusual.

So, please do (tail /var/log/apache2/access.log -n50) and (tail /var/log/apache2/error.log -n50) and be kind, please use code tag when yo post here :)

also, do "cat /etc/apache2/sites-available/default" and put result here.
also, do "ls -la /etc/apache2/site-enabled"..also results here...

Abdul

---

### Post by leomoon on 2011-07-14
Tnx. Here are all the reports in <code> tag.

tail /var/log/apache2/access.log -n50
```

127.0.0.1 - - [12/Jul/2011:13:40:59 -0700] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [12/Jul/2011:13:40:59 -0700] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [12/Jul/2011:13:40:59 -0700] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [12/Jul/2011:13:40:59 -0700] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [12/Jul/2011:13:40:59 -0700] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [12/Jul/2011:13:45:38 -0700] "GET / HTTP/1.1" 200 485 "-" "Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0"
127.0.0.1 - - [12/Jul/2011:13:45:38 -0700] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0"
127.0.0.1 - - [12/Jul/2011:13:45:38 -0700] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0"
192.168.0.30 - - [13/Jul/2011:19:13:31 -0700] "GET / HTTP/1.1" 200 485 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:19:13:34 -0700] "GET / HTTP/1.1" 304 210 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:20:13:50 -0700] "GET / HTTP/1.1" 304 211 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:20:13:52 -0700] "GET / HTTP/1.1" 304 210 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:20:13:55 -0700] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:21:21:38 -0700] "GET / HTTP/1.1" 304 211 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:21:46:43 -0700] "GET / HTTP/1.1" 304 211 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:22:03:26 -0700] "GET / HTTP/1.1" 304 211 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [13/Jul/2011:23:19:57 -0700] "GET / HTTP/1.1" 304 211 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
127.0.0.1 - - [14/Jul/2011:09:09:16 -0700] "GET / HTTP/1.1" 304 211 "-" "Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0"
127.0.0.1 - - [14/Jul/2011:09:09:18 -0700] "GET / HTTP/1.1" 304 210 "-" "Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0"
127.0.0.1 - - [14/Jul/2011:09:09:20 -0700] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0"
192.168.0.30 - - [14/Jul/2011:09:09:23 -0700] "GET / HTTP/1.1" 200 485 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [14/Jul/2011:09:09:24 -0700] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [14/Jul/2011:09:09:24 -0700] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [14/Jul/2011:09:09:24 -0700] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
192.168.0.30 - - [14/Jul/2011:09:09:24 -0700] "GET / HTTP/1.1" 200 484 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"

```

tail /var/log/apache2/error.log -n50
```

[Tue Jul 12 13:40:58 2011] [notice] Apache/2.2.17 (Ubuntu) configured -- resuming normal operations
[Tue Jul 12 13:40:59 2011] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue Jul 12 13:40:59 2011] [notice] Apache/2.2.17 (Ubuntu) configured -- resuming normal operations
[Tue Jul 12 13:45:38 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Jul 12 13:45:38 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Jul 12 13:46:00 2011] [notice] caught SIGTERM, shutting down
[Tue Jul 12 13:46:55 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Tue Jul 12 13:47:39 2011] [notice] caught SIGTERM, shutting down
[Wed Jul 13 19:13:03 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jul 13 20:13:06 2011] [notice] caught SIGTERM, shutting down
[Wed Jul 13 20:13:07 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jul 14 09:08:29 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations

```

cat /etc/apache2/sites-available/default
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

ls -la /etc/apache2/sites-enabled
```

total 8
drwxr-xr-x 2 root root 4096 2011-07-12 13:40 .
drwxr-xr-x 7 root root 4096 2011-07-12 13:40 ..
lrwxrwxrwx 1 root root   26 2011-07-12 13:40 000-default -> ../sites-available/default

```

---

### Post by linuxnizer on 2011-07-14
Hi again,
  As expected, no external traffic have reached the http daemon (no external IP present in the logs). So, let's see if the external traffic reaches the network layer at least.

  In your external machine, do [http://xxx:8081](http://xxx:8081), then immediately, type (netstat -ntp) on linux box then post the results here...

also, if you could review the full logs yourself and double check that no external IP present.

one last thing, check if any firewall running (ufw status)

Good luck

---

### Post by leomoon on 2011-07-14
the firewall is inactive.

I did 2 test. One reaching the linux locally:
```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp6       0      0 192.168.0.116:80        192.168.0.30:58960      ESTABLISHED -               

```

And reaching the linux externally:
Gave 2 results while it was trying to connect.
```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.0.116:80        96.53.39.126:64532      SYN_RECV    -               

```
```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp6       0      0 192.168.0.116:80        96.53.39.126:64532      ESTABLISHED -

```

---

### Post by linuxnizer on 2011-07-14
great, so, network is working, it does connect to apache, so....what kind of error do you get in the browser with external IP?

it's really weird that you can't find the external IP in your apache log files!!

---

### Post by leomoon on 2011-07-14
Yea I know it's VERY strange! When an external pc reaches the linux machine, browser will load for about 17 seconds and it will say "The connection was reset".

---

### Post by linuxnizer on 2011-07-14
please try reaching linux box from different machine using different connection....it would help if you could put a screen shot of the browser error.

also, double and triple check the apache log files and look for any external IP. It just doesn't make sense.  A connection DID happen to apache from external IP, it should show on log files.

---

### Post by leomoon on 2011-07-14
It only logs local connections for some reason!

I tried on 3 different devices with different connections:
[IMG]http://dl.dropbox.com/u/3053521/_img/iphone.jpg[/IMG]

[IMG]http://dl.dropbox.com/u/3053521/_img/firefox.jpg[/IMG]

[IMG]http://dl.dropbox.com/u/3053521/_img/ie.jpg[/IMG]

---

### Post by leomoon on 2011-07-14
Here is something very interesting!

I installed ubuntu with XAMPP with same port (8081) again and it couldn't be accessed from an external IP.

I installed Windows XP with XAMPP with same port (8081) and I can access it from an external IP!!!

So it can't be the router. It should be a configuration in linux. :|

---

### Post by linuxnizer on 2011-07-15
I agree, it's apache for sure. I would do full upgrade to the system (apt-get clean/update/upgrade) then try again. If still not working then the only advice I can give is back up your data, wipe the current installation and install 10.04, do full upgrade, and try again, sorry, that's the only advice I can give.

---

### Post by doas777 on 2011-07-15
one interesting note, the error is actually coming from the sockets layer, not the HTTP layer (Connection was Reset is not an HTTP error), so I am curious what the raw output of the socket is.

@Op: this will probably not lead you anywhere particularly useful, but if you want, try this:

open a terminal and run:
```
telnet <publicIPofServer> 8081
```
you will see text like:
> 
Lucid:~$ telnet localhost 139
Trying ::1...
Connected to localhost.
Escape character is '^]'.



Below the "Escape character is '^]'.", the cursor will be blinking with no prompt. 
Carefully enter (replacing ServerIP, and perhaps index.html):

```
HEAD /index.html HTTP/1.1\host:<serverIP>
```

And paste back anything it spits out. if it says "connection closed by foreign host", before printing any output, then  the HEAD command was not formatted correctly, so try again. Telnet is most unforgiving about input errors.

---

### Post by linuxnizer on 2011-07-15
doas777, telnet is too cumbersome to use, but your post gave me another idea. 

@OP, why not install wireshark and attach the dump here to analyze. I guess there is a gap between network layer and apache...

---

### Post by leomoon on 2011-07-15
I got it working but I never found out what was the problem.

Here is what I did:
- Installed Ubuntu 10.04 Server with nothing on it. Just the OS.
- Installed XAMPP and it works now!

I still have the old image that didn't work. I'll do the telnet and wireshark today and maybe we'll figure out what is the problem! :D

Thanks for all your help. :) REALLY APPRECIATE IT. :popcorn:

---

### Post by linuxnizer on 2011-07-16
Great news leomoon, I guess 11.04 is still not ready for prime time :).
I've been running 10.04 on production server for more than a year so far. 

Don't forget to update us on 11.04,

Cheers,

---

