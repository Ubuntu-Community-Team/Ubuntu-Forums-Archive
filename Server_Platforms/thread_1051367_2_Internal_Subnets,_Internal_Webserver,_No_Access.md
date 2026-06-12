---
title: "2 Internal Subnets, Internal Webserver, No Access"
date: 2009-01-26
forum: Server Platforms
---

### Post by quietas on 2009-01-26
Hey folks, I have an issue which I am not sure is Apache or my router though I think I have narrowed it down to something with the Ubuntu server. It's running 8.10 server and current updates.

I know the box works as I have Wordpress, GLPI, and OCS NG all running with their appropriate web interfaces.

The catch is when I access if from off of our local subnet. I have 4 VLANs managed by Cisco routers which our ISP handles. They say that the connection is not filtered or blocked and have tested port 80 to work.

192.168.13.0 - Main office, server here, my desk here
192.168.30.0 - Satellite office
192.168.40.0 - Satellite office
192.168.60.0 - Satellite office
192.168.70.0 - Satellite office

I have been testing through the .60 subnet as I have a Ubuntu 7.10 box over there I can SSH into. I can ping just fine, but nmap reports port 80 is closed|filtered. Lynx of course cannot connect and I can't telnet to port 80 as well. The server can get out just fine to our web as well as the separate LANs.

Let me know what I can help with.
[FONT="Courier New"]
> user@server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.13.201
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.13.12
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.13.10
        dns-search domain.com

> user@server:~$ cat /etc/hosts
127.0.0.1       localhost
192.168.13.201  server.domain.com        server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

> server.domain.com
> user@server:~$ cat /etc/resolv.conf
search domain.com
nnameserver 192.168.13.10

> user@server:~$ sudo netstat -pln --inet
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4148/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      4223/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      5450/apache2
tcp        0      0 192.168.13.201:53       0.0.0.0:*               LISTEN      4037/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      4037/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4058/sshd
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      4037/named
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      4223/smbd
udp        0      0 192.168.13.201:137      0.0.0.0:*                           4221/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           4221/nmbd
udp        0      0 192.168.13.201:138      0.0.0.0:*                           4221/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           4221/nmbd
udp        0      0 192.168.13.201:53       0.0.0.0:*                           4037/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           4037/named
udp        0      0 0.0.0.0:51400           0.0.0.0:*                           4037/named

> user@server:~$ cat /etc/apache2/ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

> user@server:~$ cat /etc/apache2/sites-enabled/000-default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
[/FONT]

---

### Post by Coreigh on 2009-01-26
You can access WordPress (not on port 80) that is on the same server that you can not access Apache, on port 80. You are working from inside the LAN but on separate VLANs, segments of the network. Is this correct?

Have you verified Apache is listening on port 80?
Are you able to access Apache from localhost, on the server?
Do you get an informative error or just server not found?
You said you can not telnet to port 80. You can't telnet or just connect fails? Connect fails indicates that the port is open.

I Hope these suggestions help.

EDIT: I assume you tried to conntect HTTP direct to the IP address and are not relying on DNS name resolution. i.e. [http://192.168.13.201/index.html](http://192.168.13.201/index.html)

SECOND EDIT: Do the apache logs offer any info? denied or failed connections?

---

### Post by quietas on 2009-01-26
I can access everything perfectly on port 80. Wordpress and Apache seem to function, but only on the local LAN.

I was attempting to telnet to port 80 from the remote system on the second subnet and it would no connect. I have tried both the full IP as well as the DNS name (which resolves).

---

### Post by capscrew on 2009-01-26
> **quietas said:**
> Hey folks, I have an issue which I am not sure is Apache or my router though I think I have narrowed it down to something with the Ubuntu server. It's running 8.10 server and current updates.

I know the box works as I have Wordpress, GLPI, and OCS NG all running with their appropriate web interfaces.

The catch is when I access if from off of our local subnet. I have 4 VLANs managed by Cisco routers which our ISP handles. They say that the connection is not filtered or blocked and have tested port 80 to work.

192.168.13.0 - Main office, server here, my desk here
192.168.30.0 - Satellite office
192.168.40.0 - Satellite office
192.168.60.0 - Satellite office
192.168.70.0 - Satellite office

I have been testing through the .60 subnet as I have a Ubuntu 7.10 box over there I can SSH into. I can ping just fine, but nmap reports port 80 is closed|filtered. Lynx of course cannot connect and I can't telnet to port 80 as well. The server can get out just fine to our web as well as the separate LANs.


sure is Apache or my router though I think I have narrowed it down to something with the Ubuntu server. It's running 8.10 server and current updates.

I know the box works as I have Wordpress, GLPI, and OCS NG all running with their appropriate web interfaces.

The catch is when I access if from off of our local subnet. I have 4 VLANs managed by Cisco routers which our ISP handles. They say that the connection is not filtered or blocked and have tested port 80 to work.

192.168.13.0 - Main office, server here, my desk here
192.168.30.0 - Satellite office
192.168.40.0 - Satellite office
192.168.60.0 - Satellite office
192.168.70.0 - Satellite office

I have been testing through the .60 subnet as I have a Ubuntu 7.10 box over there I can SSH into. I can ping just fine, but nmap reports port 80 is closed|filtered. Lynx of course cannot connect and I can't telnet to port 80 as well. The server can get out just fine to our web as well as the separate LANs.

[/QUOTE]
down to something with the Ubuntu server. It's running 8.10 server and current updates.

I know the box works as I have Wordpress, GLPI, and OCS NG all running with their appropriate web interfaces.

The catch is when I access if from off of our local subnet. I have 4 VLANs managed by Cisco routers which our ISP handles. They say that the connection is not filtered or blocked and have tested port 80 to work.

[/QUOTE]
I have read your entire post.  I have some questions that might shed light.  In some places you intimate that the network is 192.168.0.0/16 and other places it looks like you have 4 192.168.x.0/24 networks.  The use of VLAN's is typically used in one large network to separate areas logically rather than physically.

Usually ISP's do not manage internal private addressing schemes (192.168.etc).  Can you explain your setup a little better?

Some of your config files seem wrong.  See my comments in red.

```
 user@server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.13.201
netmask 255.255.255.0   [COLOR="Red"]<-- Is this really a /24 network?[/COLOR]
network 192.168.0.0     [COLOR="Red"]<--this means it is a /16 network[/COLOR]
[COLOR="Red"]Two things are inconsistent here.  The first is 
that you have described the the same network as both /16 and /24. 
It is either one or the other. 

The second thing is;  you do not need the line "network 192.168.0.0" 
[/COLOR]
broadcast 192.168.0.255  [COLOR="Red"]<-- this is the broadcast address for a /24 network.
If you are using a /16 network this should be 192.168.255.255[/COLOR] 
gateway 192.168.13.12    
# dns-* options are implemented by the resolvconf package, if installed 
[COLOR="Red"]This should not be here.  See [[COLOR="Black"]**http://en.wikipedia.org/wiki/Resolvconf**[/COLOR]]("http://en.wikipedia.org/wiki/Resolvconf")[/COLOR]
dns-nameservers 192.168.13.10
dns-search domain.com

```

```
 user@server:~$ cat /etc/resolv.conf
search domain.com
nnameserver 192.168.13.10[ [COLOR="Red"]<--Typo here (nameserver)[/COLOR]
```

I think you have a 192.168.0.0/16 network.  That would make the most sense as your DNS server uses a private address (resolving private side names  and caching only?)  

If this is correct, then set the netmask to 255.255.0.0  and the b'cast address to 192.168.255.255 in the /etc/network/interfaces file.  You should also remove all the incorrect lines in the file. Then correct the typo in the /etc/resolv.conf file.

---

### Post by Coreigh on 2009-01-27
Capscrew,
 Can you point me to a good VLAN tutorial or howto? I have need te segment my network with the hopes of minimizing broadcast traffic. When I google for VLAN I get lots of descriptions and definitions but no examples of how to implement VLANs.

---

### Post by quietas on 2009-01-27
The original admin here set up each network on it's on subnet with it's own dhcp server physically at each location. The incoming network feed is set up with a T1 with a Cisco router which is managed by the ISP. This feeds back to the main branch as well as ties to the other locations per the network diagram. Each router has an interal IP which corresponds to the subnet for that location, as well as the external IP on the internet.

I wonder at this point if it is my Apache or more likely my firewall/gateway now. Via Lynx I can access webservers between the outlying locations (really HP printers internal gui), but not outlying to the main branch.

It's a weird setup I inherited with little to no documentation and the routing between locations I do not have direct access. Firewall yes, routers no.

---

### Post by quietas on 2009-01-27
The typo in resolf.conf was a typo when I pasted, that works. I see the error with the /16 and fixed that portion. That fixed it perfectly. Odd that I could function locally, but not off the local network. I'll have to refresh my knowledge on subnetting again.

Thanks Capscrew.

---

### Post by capscrew on 2009-01-27
> **quietas said:**
> The typo in resolf.conf was a typo when I pasted, that works. I see the error with the /16 and fixed that portion. That fixed it perfectly. Odd that I could function locally, but not off the local network. I'll have to refresh my knowledge on subnetting again.

Thanks Capscrew.

You are welcome.  I have found a Howto on VLANS that has theory and a practical example for Coreigh.  maybe it will help you.

Coreigh,

This is a Howto for Dell equipment, but the basic howto applies to all.  You will have to get the specifics from the mfr. of your switches.

See: [**http://www.dell.com/downloads/global/products/pwcnt/en/app_note_38.pdf**]("http://www.dell.com/downloads/global/products/pwcnt/en/app_note_38.pdf")

---

