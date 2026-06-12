---
title: "Apache2 port change problem"
date: 2009-07-14
forum: Server Platforms
---

### Post by canishk on 2009-07-14
Hi,

I have installed apache2 with php5 in my ubuntu 9.04 server and I tried to change the default port for security in apache2/ports.conf

I have listened the port using netstat -tulpn and I got

```
netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:8010            0.0.0.0:*               LISTEN      6708/apache2    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      6708/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      32679/sshd      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      6708/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      32679/sshd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           32638/dhclient3 

```

when I checked with iptables i got the following output.
using iptables -vnL

```
iptables -vnL
Chain INPUT (policy ACCEPT 1144 packets, 504K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 352 packets, 57836 bytes)
 pkts bytes target     prot opt in     out     source               destination  
```

I don't know what exact it means. Please help me asap

Thanks,

Anish

---

### Post by Wim Sturkenboom on 2009-07-14
What problems are you having (would be nice to know, I think).

The iptables output indicates that you have the firewall configured to allow anything.

What are you trying to achieve with changing ports? Security, but what? No access from the outside world? Wouldn't it be easier in that case to change the listen address (possibly to 127.0.0.1)?

---

### Post by Wim Sturkenboom on 2009-07-14
Duplicate of above

---

### Post by giggins on 2009-07-14
Figured I'd ask, after you changed the /etc/apache2/ports.conf file, did you restart apache2? You do that by running:

```
sudo /etc/init.d/apache2 restart
```Also, as suggested by the previous replies, you can change the listening address to localhost, if your intention is to prevent external users from accessing the site. This is done in the ports.conf file:

```
Listen 127.0.0.1:80
```

---

### Post by canishk on 2009-07-15
> **Wim Sturkenboom said:**
> What problems are you having (would be nice to know, I think).

The iptables output indicates that you have the firewall configured to allow anything.

What are you trying to achieve with changing ports? Security, but what? No access from the outside world? Wouldn't it be easier in that case to change the listen address (possibly to 127.0.0.1)?

MY PROBLEM IS:
The problem is I can't access the port using a browser. As it is a server system, I have to check it from a desktop client in my lan, but didn't show up.

Thanks for your reply

---

### Post by canishk on 2009-07-15
> **giggins said:**
> Figured I'd ask, after you changed the /etc/apache2/ports.conf file, did you restart apache2? You do that by running:

```
sudo /etc/init.d/apache2 restart
```Also, as suggested by the previous replies, you can change the listening address to localhost, if your intention is to prevent external users from accessing the site. This is done in the ports.conf file:

```
Listen 127.0.0.1:80
```

Sure I did the restart thing. As I don't want it to access with the localhost. I want to access with in the lan, so can i put something like this ?? 
```

Listen <MYIP>:<MYPORT>
```

---

### Post by Wim Sturkenboom on 2009-07-15
So you use *[http://my.domain:myport](http://my.domain:myport)* in the browser? Or you have something that will translate port *80* to *myport*?

Maybe something in your network that blocks *myport* (e.g. the client PC but might be something else).

Not sure if I can help you further.

---

### Post by canishk on 2009-07-15
> **Wim Sturkenboom said:**
> So you use *[http://my.domain:myport](http://my.domain:myport)* in the browser? Or you have something that will translate port *80* to *myport*?

Maybe something in your network that blocks *myport* (e.g. the client PC but might be something else).

Not sure if I can help you further.

exactly I want it like [my.domain:myport](my.domain:myport). I don't know what blocks me. I tried with all systems connected with my network. That include both linux and windows machines, but the result was negative.

I am really sorry to hear you say like that.

anyway thanks for your kind reply.

---

### Post by Wim Sturkenboom on 2009-07-15
One thing that I can still think of is the files *hosts.allow* and *hosts.deny*. The latter usually contains a line to block all traffic and the former will then be used to allow specific traffic.

---

### Post by giggins on 2009-07-15
Changing the ports.conf file can restrict what port and/or IP apache2 listens on, but that doesn't sound like what you're trying to do. That said, keep it like this:

```
Listen 80
```

Then try connecting to it locally using w3m:

```
w3m localhost:80
```

Does your page show up? (Just an FYI, use 'q' to quit w3m.) If it does show up, then the server is working properly and its likely some kind of firewall issue. In that case, you should be able to check from a remote machine and watch the syslog for Kernel messages about dropped packets:

```
sudo tail -f /var/log/syslog
```

If you still have no luck on determining where the problem is, maybe check if there are any other devices acting as a firewall (or using ACLs) between you and the Ubuntu server.

---

### Post by canishk on 2009-07-16
> **giggins said:**
> Changing the ports.conf file can restrict what port and/or IP apache2 listens on, but that doesn't sound like what you're trying to do. That said, keep it like this:

```
Listen 80
```

Then try connecting to it locally using w3m:

```
w3m localhost:80
```

Does your page show up? (Just an FYI, use 'q' to quit w3m.) If it does show up, then the server is working properly and its likely some kind of firewall issue. In that case, you should be able to check from a remote machine and watch the syslog for Kernel messages about dropped packets:

```
sudo tail -f /var/log/syslog
```

If you still have no luck on determining where the problem is, maybe check if there are any other devices acting as a firewall (or using ACLs) between you and the Ubuntu server.

Hey,

I am getting the port 80 in my apache. When I put Listen to port 80, I can access my web through out the network.I don't think there is some firewall between, means externally but anyway i have to check that.

Thank you for your reply.

---

### Post by windependence on 2009-07-16
You will not be able to access your site by domain name on your local network because most likely your router does not support NAT reflection. Google it. If you can access the site by IP address, then it's working. You can also try using *localhost:port_number* to access it OR you can add an entry in the hosts file on the computer you are trying to access it from (the client).

-Tim

---

### Post by canishk on 2009-07-17
> **windependence said:**
> You will not be able to access your site by domain name on your local network because most likely your router does not support NAT reflection. Google it. If you can access the site by IP address, then it's working. You can also try using *localhost:port_number* to access it OR you can add an entry in the hosts file on the computer you are trying to access it from (the client).

-Tim

The thing is I am getting the site by ip.address, but not getting when I tried with ip.address:myport

---

### Post by windependence on 2009-07-17
OK so Apache is still listening on 80 then?

Can you post your config file?

You could also try a traceroute from the client and tell me where it stops.

I usually don't much with the ports.conf file. Why don't you just change the listen directive to listen only on 8010?

-Tim

---

### Post by canishk on 2009-07-20
> **windependence said:**
> OK so Apache is still listening on 80 then?

Can you post your config file?

You could also try a traceroute from the client and tell me where it stops.

I usually don't much with the ports.conf file. Why don't you just change the listen directive to listen only on 8010?

-Tim

hey,

this is my ports.conf file

```
NameVirtualHost *:80
Listen 80
Listen 8010
<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

I can't traceroute the ip with the port 8010.

---

### Post by giggins on 2009-07-20
You also need to name the additional VirtualHost:

```
NameVirtualHost *:8010
```After that, you need to make sure that you are using the now declared VirtualHost in a config file. Check in /etc/apache2/sites-available/ for a site using your Listen port:

```
grep -E '<VirtualHost [*0-9.]+:8081' /etc/apache2/sites-available/*
```If any lines are returned, then you have something setup to use that VirtualHost. If not, then you need to create another site in your config. The easiest way to do this is to copy the existing one and edit it slightly:

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/default8081
sudo vim /etc/apache2/sites-available/default8081
```Change the line that says this:
```
<VirtualHost *:80>
```to this:
```
<VirtualHost *:8081>
```Then save that config file (using ':wq'), and then enable the site:

```
sudo a2ensite default8081
sudo /etc/init.d/apache2 reload
```Now you should have a site enabled, listening on all interfaces on TCP port 8081. If you're using ufw, you need to allow access to that port.

---

### Post by canishk on 2009-07-21
Hey Giggins,

High Five !!!!!!

Its like a Dream which converted from a nightmare !!!!

Thanks Buddy. Thank you for your wonderful help.

---

### Post by giggins on 2009-07-21
no problem. glad we got the issue resolved!

---

