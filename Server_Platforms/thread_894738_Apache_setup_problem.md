---
title: "Apache setup problem"
date: 2008-08-19
forum: Server Platforms
---

### Post by ingeva on 2008-08-19
I'm running Ubuntu 8.04.1 desktop, and have tried and tried and tried to set up apache with some local domans for use with we development. No success.

I have left apache2.conf untouched from the installation, and have added http.conf thus:

```
ServerName intertrafico

Listen 127.0.0.2:80
Listen 127.0.0.3:80
Listen 127.0.0.4:80
Listen 127.0.0.5:80
Listen 127.0.0.6:80
Listen 127.0.0.7:80
Listen 127.0.0.8:80
Listen 127.0.0.99:80

```Naturally, each IP address is for one domain. "intertrafico" is the "main" server, which contains common files for all the other domains. The IPs are also defined in the /etc/hosts file.

Each virtual host is set up like this (only shown is "intertrafico" but the others are equal except for domain name and directory).

```
NameVirtualHost intertrafico
<VirtualHost 127.0.0.2:80>
    ServerAdmin webmaster@intertrafico
    ServerName intertrafico
    
    DocumentRoot /home/Ebackup/inge/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/Ebackup/inge/public_html>
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined
    ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 10.10.10.2/255.255.255.0
    </Directory>

</VirtualHost>
```I also tried to set up apache on my windows machine before I switched, but no luck. I would still like to use apache because it's more or less a standard program.

My router has address 10.10.10.1 and gives addresses from 2 to 9; the printer is 10 (10.10.10.10), so I've defined "legal" addresses to be 2-9.

Can anyone see what's wrong or missing?

---

### Post by Potatoj316 on 2008-08-19
try just using 
```
Listen 80
```i dont think you have to, and it might not let you, say the IP to listen on, it doesn't really make sense.  Or perhaps thats your problem, if you can sepecify IP than it might only be accepting connections from your own computer.

---

### Post by ingeva on 2008-08-19
> **Potatoj316 said:**
> try just using 
```
Listen 80
```i dont think you have to, and it might not let you, say the IP to listen on, it doesn't really make sense.  Or perhaps thats your problem, if you can sepecify IP than it might only be accepting connections from your own computer.

I tried this, and now apache generates a whole lot of errors, and reports missing directories that are not missing at all:

```
inge@Pantera:/etc$ sudo init.d/apache2 restart
 * Restarting web server apache2                                                                           Warning: DocumentRoot [/home/Ebackup/inge/public_html] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/noniplus] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/skms] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/test] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/forward] does not exist
[Tue Aug 19 21:00:57 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:00:57 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:00:57 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:00:57 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:00:57 2008] [warn] NameVirtualHost test:0 has no VirtualHosts
[Tue Aug 19 21:00:57 2008] [warn] NameVirtualHost skms:0 has no VirtualHosts
[Tue Aug 19 21:00:57 2008] [warn] NameVirtualHost upandforward:0 has no VirtualHosts
[Tue Aug 19 21:00:57 2008] [warn] NameVirtualHost noniplus:0 has no VirtualHosts
[Tue Aug 19 21:00:57 2008] [warn] NameVirtualHost intertrafico:0 has no VirtualHosts
httpd (no pid file) not running
Warning: DocumentRoot [/home/Ebackup/inge/public_html] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/noniplus] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/skms] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/test] does not exist
Warning: DocumentRoot [/home/Ebackup/inge/public_html/forward] does not exist
[Tue Aug 19 21:01:07 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:01:07 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:01:07 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:01:07 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Tue Aug 19 21:01:07 2008] [warn] NameVirtualHost test:0 has no VirtualHosts
[Tue Aug 19 21:01:07 2008] [warn] NameVirtualHost skms:0 has no VirtualHosts
[Tue Aug 19 21:01:07 2008] [warn] NameVirtualHost upandforward:0 has no VirtualHosts
[Tue Aug 19 21:01:07 2008] [warn] NameVirtualHost noniplus:0 has no VirtualHosts
[Tue Aug 19 21:01:07 2008] [warn] NameVirtualHost intertrafico:0 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

So this did not help much .... :)

---

### Post by ingeva on 2008-08-19
> **Potatoj316 said:**
> try just using 
```
Listen 80
```i dont think you have to, and it might not let you, say the IP to listen on, it doesn't really make sense.  Or perhaps thats your problem, if you can sepecify IP than it might only be accepting connections from your own computer.

I found a typing error and corrected it.
After that I get the following:

```
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by ingeva on 2008-08-20
Maybe this wasn't the right place to ask -- but my Apache problem is on the desktop version, and not by the server although they shouldn't be that different (?).

Does anyone have a virtualhost file that you might want to share?

None of mine work.

The http.conf file is now:

```
ServerName intertrafico

Listen 127.0.0.2:80
Listen 127.0.0.3:80
Listen 127.0.0.4:80
Listen 127.0.0.5:80
Listen 127.0.0.6:80
Listen 127.0.0.7:80
Listen 127.0.0.8:80
Listen 127.0.0.9:80
Listen 127.0.0.99:80

```

---

### Post by MJN on 2008-08-20
> **ingeva said:**
> ```
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```
 
Always take any errors, particularly at process startup, seriously.
 
In this case it is telling you two things - it could not bind to port 80 and hence it is not starting at all. So, if Apache isn't running on port 80 what is?
 
Find out with **sudo lsof -i :80** and post the results.
 
Incidentally, as you are using name-based virtual hosting you only need the one Listen 127.0.0.1:80 directive (all hosts should then be configured <Virtualhost 127.0.0.1:80> to match).
 
Mathew

---

### Post by Ximbiot on 2008-08-20
> **ingeva said:**
> Does anyone have a virtualhost file that you might want to share?

The [Apache Virtual Hosts documentation]("http://httpd.apache.org/docs/2.0/vhosts/") has some [examples]("http://httpd.apache.org/docs/2.0/vhosts/examples.html") I've found useful in the past.

---

### Post by Potatoj316 on 2008-08-20
> **ingeva said:**
> Maybe this wasn't the right place to ask -- but my Apache problem is on the desktop version, and not by the server although they shouldn't be that different (?).

shouldnt be a problem.

your current problem sounds like its not able to connect/isnt connecting to port 80.  try changing it to 
```
Listen 9999
```
(or some other random port above 1024)
I also still dont think the IP is necessary when specifying what port to listen to, the default is just
```
Listen 80
```

If you know for a fact that you can specify the IP do you mind sharing with me what it does/what the benefit is?

---

### Post by ingeva on 2008-08-20
> **MJN said:**
> So, if Apache isn't running on port 80 what is?
 
Find out with **sudo lsof -i :80** and post the results.
 
Incidentally, as you are using name-based virtual hosting you only need the one Listen 127.0.0.1:80 directive (all hosts should then be configured <Virtualhost 127.0.0.1:80> to match).
 

No output from the lsof command, so I guess no one is using port 80.

I haven't tried using the same IP for all domains, but I could try that.
In that case, what should be in the hosts file?

---

### Post by Ximbiot on 2008-08-20
> **Potatoj316 said:**
> If you know for a fact that you can specify the IP do you mind sharing with me what it does/what the benefit is?

Listen *without* an IP specified listens on all available network interfaces.  Listen *with* an IP specified binds only to the specified IP addresses.  For example, if you wanted a test server that could only be accessed locally, you could specify:

```
Listen 127.0.0.1:80
```

Then only browsers running on the local machine would be able to access the server.

Similarly, if you had a web server running on your router, you could make the server available on the LAN and not the WAN.

---

### Post by ingeva on 2008-08-20
> **Ximbiot said:**
> The [Apache Virtual Hosts documentation]("http://httpd.apache.org/docs/2.0/vhosts/") has some [examples]("http://httpd.apache.org/docs/2.0/vhosts/examples.html") I've found useful in the past.

I have used that documentation and examples as starting points,
but especially the documentation is incredibly hard to put into practice,
and the error messages are more or less cryptic.

I think apache must be the worst program I have ever worked with.
So far I've tried and retried for a couple of weeks, and the closest I've
been was to get "It works" regardless of what site I tried to open.

---

### Post by ingeva on 2008-08-20
> **Ximbiot said:**
> 

```
Listen 127.0.0.1:80
```Then only browsers running on the local machine would be able to access the server.


Right now it would be OK to only access it from this computer, but I plan
to set up an older computer as a file and web server, only to be access from
the LAN.

---

### Post by MJN on 2008-08-20
If you're struggling it is probably a sign that you are trying to run before you can walk.
 
Stick to getting a single site up first and once you're happy with that then move on to adding an additional host. Trying to get ten sites working when you can't do one is surely asking for trouble.
 
Mathew

---

### Post by Ximbiot on 2008-08-20
> **ingeva said:**
> No output from the lsof command, so I guess no one is using port 80.

I think the "no listening sockets available" error may have to do with the fact that you can't listen on an IP unless it is actually bound to an address.  So, unlike connection via a client, listening on IPs like 127.0.0.2 is only going to work if you have explicitly bound that IP to the loopback interface.

> **ingeva said:**
> I haven't tried using the same IP for all domains, but I could try that.
In that case, what should be in the hosts file?

You can alias all the IPs to 127.0.0.1.  Only the first will come up in a reverse-lookup, but I don't think this should affect you.  /etc/hosts:

```
127.0.0.1 intertrafico anotherhost yetanother yya
```

...and so on.

---

### Post by Ximbiot on 2008-08-20
> **ingeva said:**
> Right now it would be OK to only access it from this computer, but I plan
to set up an older computer as a file and web server, only to be access from
the LAN.

Then `Listen 80' should be what you want, to ask Apache to listen on all available interfaces.

---

### Post by Ximbiot on 2008-08-20
> **ingeva said:**
> the closest I've
been was to get "It works" regardless of what site I tried to open.

Do as Matthew suggests.  If you can get an "It works" message, then first start by putting the data you want to serve in the location "It works" says it is serving.  Once you can see *that*, *then* try changing the location to where you really want to serve the data from.  Once you have *that* working, *then* try adding additional virtual servers at new locations.

---

### Post by mbeach on 2008-08-20
I believe by default /etc/apache2/ports.conf is included after httpd.conf, so perhaps make sure nothing in ports.conf is overwriting what you've placed in httpd.conf.

---

### Post by mbeach on 2008-08-20
also, if I understand what you are trying to do - ie test sites internally, I think your httpd.conf file should be empty, ports.conf should have one line "Listen 80", your virtual host files should contain something like:
```

      1 NameVirtualHost *
      2 <VirtualHost *>
      3     ServerName com.someInternalDomain1
```
Then as Ximbiot said each machines host's file that you are testing from should have something like:
```
10.10.10.1 intertrafico com.someInternalDomain1 yetanother yya
```
assuming 10.10.10.1 is the webserver.

if you are going to test from the webserver itself, then you would probably want to change the host file on the webserver as well to be as Ximbiot suggested.

---

### Post by ingeva on 2008-08-20
> **Ximbiot said:**
> Do as Matthew suggests.  If you can get an "It works" message, then first start by putting the data you want to serve in the location "It works" says it is serving.  Once you can see *that*, *then* try changing the location to where you really want to serve the data from.  Once you have *that* working, *then* try adding additional virtual servers at new locations.

That's what I did.

---

### Post by ingeva on 2008-08-20
> **mbeach said:**
> also, if I understand what you are trying to do - ie test sites internally, I think your httpd.conf file should be empty, ports.conf should have one line "Listen 80", your virtual host files should contain something like:
```

      1 NameVirtualHost *
      2 <VirtualHost *>
      3     ServerName com.someInternalDomain1
```Then as Ximbiot said each machines host's file that you are testing from should have something like:
```
10.10.10.1 intertrafico com.someInternalDomain1 yetanother yya
```assuming 10.10.10.1 is the webserver.

if you are going to test from the webserver itself, then you would probably want to change the host file on the webserver as well to be as Ximbiot suggested.

Looks sensible. I'll try that.
It looks like the IP-address of the server computer is not guaranteed. The router sets up the addresses, and this router doesn't seem to accept a fixed setup like binding an IP address to a MAC address. However, right now it has the IP defined in the hosts file, and if that's sufficient I might make it work.
I won't be able to test this until tomorrow (It's late here now).

---

### Post by ingeva on 2008-08-20
> **mbeach said:**
> also, if I understand what you are trying to do - ie test sites internally, I think your httpd.conf file should be empty, ports.conf should have one line "Listen 80", your virtual host files should contain something like:

Well, with all this messing around it eventually turned out that "listen 80" was in BOTH the ports.conf and the httpd.conf file. I haven't even touched the first one because I would do as few modifications as possible.

Apache must be a strange program, that doesn't accept such duplicates, and prints error messages that give no clue to what's wrong.

I haven't tested any more yet. That will have to wait until tomorrow morning.

---

### Post by MJN on 2008-08-20
> **ingeva said:**
> Well, with all this messing around it eventually turned out that "listen 80" was in BOTH the ports.conf and the httpd.conf file. I haven't even touched the first one because I would do as few modifications as possible.This is why you shouldn't 'fight' the modular configuration approach because to do so ends up breaking things. On this note, leave httpd.conf empty - you shouldn't be using it at all (have another read of /etc/apache2/README)

> Apache must be a strange program, that doesn't accept such duplicates, and prints error messages that give no clue to what's wrong.It is strange, and for this reason I don't think it will really catch on... ;)

> I haven't tested any more yet. That will have to wait until tomorrow morning.Good to hear it - you'll be thankful it's all been so painful as I'm sure you'll find you've learnt far more than if it had 'just worked' the first time around!

Mathew

---

### Post by ingeva on 2008-08-21
> **MJN said:**
> This is why you shouldn't 'fight' the modular configuration approach because to do so ends up breaking things.
...
Good to hear it - you'll be thankful it's all been so painful as I'm sure you'll find you've learnt far more than if it had 'just worked' the first time around!


Fighting the modular approach is the last thing I would do, but because of this error everything else I did was in vain. The program didn't even come so far as to read the virtualhosts files.
I've learn something allright -- what a particular program apache is -- and the documentation doesn't really tell you how to do things.

It's almost solved now. Apache even reads the correct index files. However, they are all php, and even if I have installed php, apache won't use it.

Here are my install instructions:
```
#php5 and apache2
apt-get install libapache2-mod-php5 php5-common php5
apt-get install libmysqlclient15off mysql-common
apt-get install apache2 apache2.2-common apache2-mpm-prefork apache2-utils apache2-doc
```Did I forget something?

And I would like to ask an additional question: Except rebooting, what can I do to have the hosts-file reread?

---

### Post by ingeva on 2008-08-21
I see that the thread has been moved. That's OK. I was wondering if I should choose the server platform even if I'm using a desktop.

Anyway, thanks to everyone for helping.
However, there's one outstanding question, and I'll be going away for a few days so I hope there will be an answer here by then. :)

---

### Post by MJN on 2008-08-21
> **ingeva said:**
> And I would like to ask an additional question: Except rebooting, what can I do to have the hosts-file reread?There's no need - just save any edits and they will be available immediately. You may find some applications have their own internal cache so restarting them would be all that's required.
 
Mathew

---

### Post by windependence on 2008-08-21
Your box should at least have an internal static IP within your network. when you say the router assigns an addressm this means that your box is set up to pull IPs via DHCP. You don't want to do that in this case.

-Tim

---

### Post by ingeva on 2008-08-23
> **windependence said:**
> Your box should at least have an internal static IP within your network. when you say the router assigns an addressm this means that your box is set up to pull IPs via DHCP. You don't want to do that in this case.

-Tim

I thought so. I'm not sure how I can use static addreses on this box, but I'll check it out. As long at the address can be allocated according to the MAC address and not the physical port, it should be OK.

---

### Post by windependence on 2008-08-23
You don't need to worry about the MAC address if you set it static in the machine. Here's how you do it.

If you want to configure Static IP address you need to edit the /etc/network/interfaces and you need to enter the following lines replace eth0 with your network interface card

```
sudo nano /etc/network/interfaces
```

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
```

Of course you have to replace all the network parameters with your own.

After entering all the details you need to restart networking services using the following command

```
sudo /etc/init.d/networking restart
```

Then set up your DNS like so:

```
sudo nano /etc/resolv.conf
```

enter the following details

```
search example.com

nameserver 192.168.3.2
nameserver 208.67.222.222
nameserver 208.67.220.220
```

You can use these OpenDNS servers or replace them with the ones from your ISP. Either one should work fine.

-Tim

---

### Post by Iowan on 2008-08-23
> **ingeva said:**
> ... As long at the address can be allocated according to the MAC address and not the physical port, it should be OK.
I'm guilty of not reading the entire thread, but the DHCP server should be able to issue a "static lease" based on MAC address - or you can configure a static address on the server (outside the DHCP range, but within the subnet).

---

### Post by ingeva on 2008-08-24
> **windependence said:**
> You don't need to worry about the MAC address if you set it static in the machine. Here's how you do it.


Thanks! Here's what I did:

```
auto wlan0
iface wlan0 inet static
address 10.10.10.3
gateway 10.10.10.1
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255

```As you see, I'm using a wireless interface on the current machine.
After restarting and re-applying the parameters with the Network Manager some more lines were added automatically, and everything works fine.

---

### Post by ingeva on 2008-08-24
> **ingeva said:**
> Thanks! Here's what I did:


Next time I logged in I got problems with the Gnome session daemon.

Reset back to the original and everything was fine.
So this was not the best solution. However, defining the IP for the computer in the hosts file seems to ensure the correct IP every time, even when using dhcp.

---

