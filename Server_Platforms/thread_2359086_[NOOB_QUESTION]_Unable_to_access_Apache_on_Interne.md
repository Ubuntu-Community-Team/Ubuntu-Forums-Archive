---
title: "[NOOB QUESTION] Unable to access Apache on Internet"
date: 2017-04-20
forum: Server Platforms
---

### Post by buenorcd on 2017-04-20
Hi guys!

First i would like to apologize in case that question has been already solved by someone else, i've tried to search and couldn't find anything that actually helped me.

I'm using Ubuntu Server 17.04

The problem is:

I'm able to acess my webserver through my LAN, within the LAN everything works fine, but when someone tries to access "http://foxp2.ddns.net" or my Internet IP address wich currently is:

```
189.69.210.93 it says "conection timed out / could not estabilish connection
```

 
The server's LAN IP is 192.168.15.25, i set it up as _static_ and since my router is DHCP (MitraStar GPT-2541GNAC-N1) I created a DNS redirection from No-Ip.

```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static
address         192.168.15.25
network         192.168.15.0
netmask         255.255.255.0
broadcast       192.168.15.0
gateway         192.168.15.1
# This is an autoconfigured IPv6 interface
iface enp2s0 inet6 auto

```

[IMG]http://imageshack.com/a/img924/2484/HnhFNa.jpg[/IMG]

Then i setup the NAT:
[IMG]https://imageshack.com/i/poJs8qAIj[/IMG]

And Firewall:
[IMG]https://imageshack.com/i/pox4PHepj[/IMG]


But still no success.

These are the configs i set up for the Apache:

/etc/apache2/sites-available/000-default.conf
```

<VirtualHost *:8080>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


```

/etc/apache2/ports.conf
```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 8080

<IfModule ssl_module>
        Listen 4443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 4443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```


I simply just don't know what else to do, i'm trying to solve this by my own for two weeks reading and trying to understand the whole process but still no success, i'll be very glad if you guys can help me so i can understand whats really happening, thanks in advance and sorry for my English.

---

### Post by darkod on 2017-04-20
In /etc/network/interfaces your broadcast value is wrong. Especially if you don't understand what the values mean, I always recommend not using network and broadcast. Earlier it was necessary but now they are calculated automatically from the address / netmask combination. So not using network and broadcast reduces the possibility of error.

Remove them and restart the networking service or the server.

So, on the LAN you can open it as 192.168.15.25:8080? I see you set up apache for port 8080. It works internally on that port in a browser?

If it does, then the issue is with port forwarding on your router, or the ISP is blocking port 80 like many ISPs do to prevent people running web servers at home.

---

### Post by buenorcd on 2017-04-20
Hi Darko, first thank you for the reply

I setup the interfaces like so:
```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static
address         192.168.15.25
netmask         255.255.255.0
gateway         192.168.15.1
# This is an autoconfigured IPv6 interface
iface enp2s0 inet6 auto

```

Yes, in my LAN i can open it as 192.168.15.25:8080, and i changed the port to 8080 because the ISP was blocking port 80.

But i also didn't find a way to make sure if the ISP was really blocking the port 80, i just assumed that it was because when i changed the default listen port to 90 (did it as a test) and checked in [http://canyouseeme.org/](http://canyouseeme.org/) it was showing that the port (90) was open, and when set as 80 it was filtered.

What i just don't get is like, now i set up the listen port to 8080, and i'm currently not using any kind of iptables rules or ufw, but whenever i check the port status it says:
 
"[COLOR=red]**Error:**[/COLOR] I could **not** see your service on **189.69.210.93** on port (**8080**)
Reason: Connection timed out"

---

### Post by darkod on 2017-04-20
But in such case you do not have the port forwarding set up correctly to use 8080 external. In your NAT port forwarding you use external port 80 to internal 8080. You need to use ext 8080 to int 8080.

Also in your firewall rules in Open Ports you set 80 instead of 8080.

And in the external URL you would have to add :8080 at the end because without specifying a port it uses 80 by default.

---

### Post by buenorcd on 2017-04-20
I'm starting to get it now, i was assuming that just because it was a TCP request it must came from the port 80, that's why i set the forwarding like ext 80 -> int 80 (it was wrong anyway ](*,))

Now i changed the NAT to ext 8080 -> int 8080

Now when i type in the browser the internal server IP "192.168.15.25" It says "Unable to connect"
And when i type "192.168.15.25:8080" It opens the Apache index, wich should be correct way since the 80 isn't the default anymore.

And using the DNS
When i type "http://foxp2.ddns.net" it sends me to my router.
And when i type "http://foxp2.ddns.net:8080" i can see the Apache index.

That should be correct, right?

Man i'm so happy i'm starting to understand and amazed with how dumb was the things i was doing #-o
You're really helping me out, thanks!

---

### Post by darkod on 2017-04-20
Yeah, looks to be correct. You still have to test from outside your LAN, but so far it looks good. You can mark the thread as solved when you are happy how it works. You can do that in Thread Tools above the first post.

---

### Post by buenorcd on 2017-04-20
I'll mark it as solved Drako, thank you so much for the help man, it really made me understand some flaws, sorry for the wait to reply, i was busy doing some other stuff but i really don't know how to thank you. I'm very happy to make part of this community and i hope some day i can help other ppl as you helped me, thank you very much!

---

