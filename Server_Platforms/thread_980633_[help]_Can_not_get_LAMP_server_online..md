---
title: "[help] Can not get LAMP server online."
date: 2008-11-13
forum: Server Platforms
---

### Post by mummim on 2008-11-13
Hi. I have used Linux for a few months, and I do feel lucky that my teacher taught me it. Lately, I have been trying to set up a LAMP server, but I can not get it online to the Internet.

LAMP is running, I can browse "http://localhost" from my computer.
I have enabled port forwarding in my router (WPN824), both 80 and 99.
I have added "Listen 99" to "/etc/apache2/ports.conf"
I have checked through "http://www.canyouseeme.org/" but it couldn't see me (connection refused).
My friend can not browse "http//[myip]".

I have searched but couldn't find anything helpful, another thread with a similar situation was "http://ubuntuforums.org/showthread.php?t=949191&highlight=browse+localhost", but since it was tagged as "solved", I think I should make a new thread to ask for help.

For your time and attention, I thank you.

---

### Post by devonps on 2008-11-13
Do you have a domain registered?

---

### Post by stelth-panther on 2008-11-13
When you are on the LAMP server use canyouseeme.org and try port 80.  If that doesn't work then you have something blocking inbound connections from getting to the server.  you can always try specifying the port by amending ":80" to the end of your ip.

---

### Post by mummim on 2008-11-13
> **devonps said:**
> Do you have a domain registered?
No I don't, but I suppose using IP address would be the same, wouldn't it?
Thanks for replying.

---

### Post by CP1256 on 2008-11-13
Your ISP might be blocking port 80, try another port to see if it works then.

---

### Post by cariboo on 2008-11-13
> I have checked through "http://www.canyouseeme.org/" but it couldn't see me (connection refused)

Means that either you haven't setup port forwarding correctly, or your ISP is blocking any ports that a server would normally run on.

Jim

---

### Post by mummim on 2008-11-13
> **cariboo907 said:**
> Means that either you haven't setup port forwarding correctly, or your ISP is blocking any ports that a server would normally run on.

Jim
I have set the router to transfer port 99 to my IP address, here is the picture:
[[IMG]http://img148.imageshack.us/img148/7820/routerportsg3.th.jpg[/IMG]](http://img148.imageshack.us/my.php?image=routerportsg3.jpg)[[IMG]http://img148.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)


How may I know if my ISP is blocking the ports?

Thanks for your time.

---

### Post by Philio on 2008-11-13
> **mummim said:**
> How may I know if my ISP is blocking the ports?

It's not exactly common for port 80 to be blocked, I would doubt 99 is blocked as well. It's more likely to be a config issue your side. You could always call your ISP and ask about blocked ports.

---

### Post by mummim on 2008-11-14
I really don't know what I should do know. I suppose I have made a mistake somewhere, that is the only logical reason to me, but I can not find out where is the mistake.
Can anyone please tell me what may be the problem?

---

### Post by R.Bucky on 2008-11-14
Do you have the DocumentRoot set in /etc/apache2/httpd.conf? If not, you need to add the line ```
DocumentRoot /var/www/
``` to the httpd.conf. Have you restarted your router, modem, and apache?

---

### Post by devonps on 2008-11-14
> **mummim said:**
> No I don't, but I suppose using IP address would be the same, wouldn't it?
Thanks for replying.

I'm not sure, I've always used a domain and pointed an IP address to the domain.

Besides can you use an IP address within the Virtual Host directives for Apache?

---

### Post by Iowan on 2008-11-14
Can you browse to the server from another machine on your local network?  If so, the problem is with the forwarding... if not, it's in server configuration.  Although I don't have links available (aside from [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") one), I've seen How-To's on changing things to make server accessible via localhost only (something you DON'T want to do).

---

### Post by drubin on 2008-11-14
Do you have your HTTPD.conf file to accept connections from a differnt host name other then localhost?

---

### Post by mummim on 2008-11-15
> **Iowan said:**
> Can you browse to the server from another machine on your local network?  If so, the problem is with the forwarding... if not, it's in server configuration.  Although I don't have links available (aside from [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") one), I've seen How-To's on changing things to make server accessible via localhost only (something you DON'T want to do).

Yes, other machines can connect to my server. I think I must have do something incorrectly.



[quote=drubin]Do you have your HTTPD.conf file to accept connections from a differnt host name other then localhost?[/quote]
I have found this: "http://ubuntuforums.org/showthread.php?t=978659&highlight=httpd.conf" and follow it. Thank for your help.

I have :
```
mummim *:80
```
in my httpd.conf file, mummim is the name of my server.

I also have ```
<VirtualHost *:80>
mummim mummim.no-ip.org
DocumentRoot /var/www/mummim
</VirtualHost>
``` on my sites-available/site.conf

---

### Post by drubin on 2008-11-15
> **mummim said:**
> 
I have :
```
mummim *:80
```
in my httpd.conf file, mummim is the name of my server.

I also have ```
<VirtualHost *:80>
mummim mummim.no-ip.org
DocumentRoot /var/www/mummim
</VirtualHost>
``` on my sites-available/site.conf

I would just have

```
 *:80
```this tells it to listen on all hosts/ip's but your VirtualHosts will handle what gets displayed.

On this point does it not need to be
 ```
<VirtualHost *:80>
ServerName mummim 
ServerAlias mummim.no-ip.org
DocumentRoot /var/www/mummim
</VirtualHost>
```

---

### Post by dynamethod on 2008-11-15
Are you sure that apache2 is listening on your internal IP address or is it listening on loopback?

try sudo netstat -antp

if its listening on 127.0.0.1 then you wont be able to recieve incomming connections, say for example your LAN address is 192.168.1.5 then you must specify apache2 to listen to that IP, sorry if this has already been posted.

---

### Post by mummim on 2008-11-18
I am really sorry for replying too late. I have got some essays that I had to submit. I must have started writing them earlier though. ^^ 


> **dynamethod said:**
> Are you sure that apache2 is listening on your internal IP address or is it listening on loopback?

try sudo netstat -antp

if its listening on 127.0.0.1 then you wont be able to recieve incomming connections, say for example your LAN address is 192.168.1.5 then you must specify apache2 to listen to that IP, sorry if this has already been posted.

I got this when I typed the command.
```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5374/mysqld     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      5978/perl       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5296/cupsd 
```
I suppose you were right that my Apache is misconfigured. I am so released that we seem to find out the problem. However, I still can't know how to change the listening IP for Apache. :( Can you please help me out?

After I changed my apache2/ports.conf to:
```
Listen 192.168.1.2:80
<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

 I got this error when restarting Apache:
```
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(99)Cannot assign requested address: make_sock: could not bind to address 192.168.1.2:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!

```

---

### Post by mummim on 2008-11-19
Can anyone please help me?

---

### Post by mummim on 2008-11-21
Can anyone please help me?

---

### Post by mummim on 2008-11-23
> **mummim said:**
> Can anyone please help me?


I have tried to search on the Internet but I still can't find a solution. I really want to have my server online. Can anyone please help me out?

---

### Post by rslrdx on 2008-11-23
ok... just wondering, have you tried to access it from another computer on your network? if it works you'll see whatever index.html page you on that server. This would tell you if your apache server is listening on port 80, and if you want to test port 99, just do something like server_ip:99.

let me know if that works... 

btw, if it works internally, server is fine, and we can check routing.... 

TTYL

---

### Post by mummim on 2008-11-23
> **rslrdx said:**
> ok... just wondering, have you tried to access it from another computer on your network? if it works you'll see whatever index.html page you on that server. This would tell you if your apache server is listening on port 80, and if you want to test port 99, just do something like server_ip:99.

let me know if that works... 

btw, if it works internally, server is fine, and we can check routing.... 

TTYL

Thank you for replying.
Other computers in my network can browse my index pages.

BTW, I didn't know "TTYL" means "talk to you later" until I see it from this post of yours. ^^

TTYL

---

### Post by rslrdx on 2008-11-23
Hi, 

So, if that works, chances are you just need to check the port forwarding.

Try this, in your router, add a port foward from the external port 8000 to the internal port 80 on your server. 

Then you can check by going to canyouseeme.org and telling it to test port 8000, at least that way you dont have to give out your ip address yet..

It is indeed common to see port 80 blocked on regular home connections. they block it so that people wont host servers on home conections...

LOL... <<< you know this one right? :lolflag:
TTYL.

---

### Post by rslrdx on 2008-11-23
forgot to mention... after you create the port forward from port 8000 to 80, and you want to see the page hosted on your server, open your browser and type your external ip address, with port 8000 at the end if it.. so that would be like ipaddress:8000 in other words, ip_address_colon_port_number

---

### Post by mummim on 2008-11-24
> **rslrdx said:**
> forgot to mention... after you create the port forward from port 8000 to 80, and you want to see the page hosted on your server, open your browser and type your external ip address, with port 8000 at the end if it.. so that would be like ipaddress:8000 in other words, ip_address_colon_port_number

In my router ( a netgear one), I can only add a port forwarding from Internet to an IP on LAN.

Here is what my router page look like:
[[IMG]http://img148.imageshack.us/img148/7820/routerportsg3.th.jpg[/IMG]](http://img148.imageshack.us/my.php?image=routerportsg3.jpg)[[IMG]http://img148.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

BTW, I suppose I can have a wireless connection between my server and my router right?

---

### Post by rslrdx on 2008-11-24
right, only from the internet to your internal ip (LAN IP), and yes, you can use wireless, 

on your router, what comes up if you click on "Add Custom Service" ???

maybe you can tell us the router model number, so that we may try to find some screenshots or emulator on the net.

---

### Post by mummim on 2008-11-24
> **rslrdx said:**
> right, only from the internet to your internal ip (LAN IP), and yes, you can use wireless, 

on your router, what comes up if you click on "Add Custom Service" ???

maybe you can tell us the router model number, so that we may try to find some screenshots or emulator on the net.
[http://portforward.com/english/routers/port_forwarding/Netgear/WPN824v2/Age_of_Empires.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WPN824v2/Age_of_Empires.htm)

Here is my router and how it can be configured. The page also has what comes when I click "Add Custom Service". My router is WPN824v2.

---

### Post by rslrdx on 2008-11-26
sorry for the long time on the replys, work is killing me... but i looked at the screenshots and didnt see a way to do a port foward with redirecion, meaning, incoming conections from one port number, will be redirected to another port

like this 

internet_IP:99 >> 192.168.0.10:80

where anything from the internet that comes on port 99 will go to port 80 on the 192.168.0.10 LAN ip

its been a while since i used a netgear router, you may need to also set the port triggering function... its been a while, i cant be sure. 

while searching for info on your router i found this... please confirm if its the correct product manual

[http://kbserver.netgear.com/pdf/wpn824_ref_manual.pdf](http://kbserver.netgear.com/pdf/wpn824_ref_manual.pdf)

---

### Post by mummim on 2008-11-26
> **rslrdx said:**
> sorry for the long time on the replys, work is killing me... but i looked at the screenshots and didnt see a way to do a port foward with redirecion, meaning, incoming conections from one port number, will be redirected to another port

like this 

internet_IP:99 >> 192.168.0.10:80

where anything from the internet that comes on port 99 will go to port 80 on the 192.168.0.10 LAN ip

its been a while since i used a netgear router, you may need to also set the port triggering function... its been a while, i cant be sure. 

while searching for info on your router i found this... please confirm if its the correct product manual

[http://kbserver.netgear.com/pdf/wpn824_ref_manual.pdf](http://kbserver.netgear.com/pdf/wpn824_ref_manual.pdf)

Yes it is the correct manual.

Do I have to configure the router to forward incomming signal from Internet to a specific port in my server?

Thanks for replying. I am not in a rush to have my server work, I just really want to learn how to set up a webserver.

---

### Post by trentscott4 on 2008-11-26
You need to forward TCP port 80 (from the Internet) to your server box.  Make sure you're running the server on a static IP, otherwise you've opened a port on the router to an address that will exist until say...tomorrow night.

See [this]("http://trentforge.com/?p=33") guide to configuring a static IP on both desktop/server editions.

Good luck!

---

### Post by rslrdx on 2008-11-27
well, as far as we can tell your http server is setup correctly... it works on your local network, the server is working, what we are having trouble with is just routing, and honestly, once we figure out how to do a port foward with the redirection, we can get it online, just not on port 80, because the isp is blocking it, i'm sure.



Do I have to configure the router to forward incomming signal from Internet to a specific port in my server? 

yes, thats the whole idea, we need to redirect traffic from one port to another, and yes, that is traffic comming from the internet to your server, and only on a specific port, port 80 for now.

honestly, your http server (apache) is working, we're just dealing with routing at this point

---

### Post by mummim on 2008-11-27
Men, I thought that setting up a server is easy. Well, I suppose after the first time, it will be. ^^

> **rslrdx said:**
> 
Do I have to configure the router to forward incomming signal from Internet to a specific port in my server? 

yes, thats the whole idea, we need to redirect traffic from one port to another, and yes, that is traffic comming from the internet to your server, and only on a specific port, port 80 for now.

I set up a port forwarding already in my router, but it doesn't let me forwarding to a specific port, only to an IP. I wonder which port it is forwarding to then, because I suppose any incoming signal has to go through a port.

I have found this site, [http://www.no-ip.com/support/guides/routers/netgear.html#3](http://www.no-ip.com/support/guides/routers/netgear.html#3), it contains a tutorial for configuring port forwarding on my router, but the tutorial itself doesn't say anything about forwarding to a specific port, only a specific IP.

Does it mean that my router is not capable for setting up a webserver?

Oh, I almost forgot. Happy thanksgiving and thank you for helping me in such a time. ^^ :)

---

### Post by volkswagner on 2008-11-28
Lets try to keep it simple.

Before trying to hop ports lets see if you can forward your apache port to your server.

I appears you are trying to add your external ip address to forward.  On the router screen shot you have server ip= 10.0.0.5 is that your internal address.  This should be something like 192.168.1.102 or 192.168.0.202

So if Apache2 is still set to listen on port 99 then forward that to your servers ip.  You can confirm your server internal ip by running...

```
ifconfig
```

---

### Post by rslrdx on 2008-11-28
> **volkswagner said:**
> Lets try to keep it simple.

Before trying to hop ports lets see if you can forward your apache port to your server.

I appears you are trying to add your external ip address to forward.  On the router screen shot you have server ip= 10.0.0.5 is that your internal address.  This should be something like 192.168.1.102 or 192.168.0.202

So if Apache2 is still set to listen on port 99 then forward that to your servers ip.  You can confirm your server internal ip by running...

```
ifconfig
```


goog point, i didnt check the ip address, however, the 10.0.0.5 address works fine too, if of course the network address matches it... mummim, what is the outcome of ipconfig on your server? 

also, just to make sure, can you post the contents of these two files ? 

/etc/network/interfaces 

/etc/resolv.conf

---

### Post by mummim on 2008-11-28
@volkswagner: I thought that the IP should be the server's internal IP, which means the IP of it in the LAN.

Here is what I got with the "ifconfig"
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:52:05:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x2000 Memory:f0600000-f0620000 

eth1      Link encap:Ethernet  HWaddr 00:18:de:07:3d:2c  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe07:3d2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:555985 (542.9 KB)  TX bytes:104544 (102.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77004 (75.1 KB)  TX bytes:77004 (75.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-07-3D-2C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Here is the interfaces file:
```
auto lo
iface lo inet loopback

```

Here is the resolv.conf file:
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5186
#
### END INFO



nameserver 10.0.0.1
```

Have I missed something?

Thanks for replying.

---

### Post by rslrdx on 2008-11-28
your config on these parts seems 100% correct.

---

### Post by volkswagner on 2008-11-28
> **mummim said:**
> @volkswagner: I thought that the IP should be the server's internal IP, which means the IP of it in the LAN.

Here is what I got with the "ifconfig"
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:52:05:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x2000 Memory:f0600000-f0620000 

eth1      Link encap:Ethernet  HWaddr 00:18:de:07:3d:2c  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe07:3d2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:555985 (542.9 KB)  TX bytes:104544 (102.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77004 (75.1 KB)  TX bytes:77004 (75.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-07-3D-2C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Here is the interfaces file:
```
auto lo
iface lo inet loopback

```

Here is the resolv.conf file:
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5186
#
### END INFO



nameserver 10.0.0.1
```

Have I missed something?

Thanks for replying.

It appears the name server is on you internal network?

Can you resolve names?  On your server run and post the results for the following command.

```
host google.com 
```

---

### Post by rslrdx on 2008-11-28
he should be able to, not uncommon to see a home router work as a dns bridge... i would not be surprised of that... and even then... it would not affect the incoming connections, only the outgoing part and only if dns was needed...

---

### Post by mummim on 2008-11-29
> **volkswagner said:**
> It appears the name server is on you internal network?

Can you resolve names?  On your server run and post the results for the following command.

```
host google.com 
```

Here it is:

```
google.com has address 74.125.45.100
google.com has address 209.85.171.100
google.com has address 72.14.205.100
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
```

---

