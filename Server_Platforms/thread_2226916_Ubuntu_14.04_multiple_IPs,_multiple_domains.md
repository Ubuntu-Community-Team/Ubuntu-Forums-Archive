---
title: "Ubuntu 14.04 multiple IPs, multiple domains"
date: 2014-05-29
forum: Server Platforms
---

### Post by dan109 on 2014-05-29
Hi there. Pretty new to the linux environment, so let me just tell you what I'm trying to do in Ubuntu 14.04:

The company I work for has a linux web server that I just installed on a  server rack that we rent. We have a block of 30 ips that we can use, a  couple of which I've already moved to this new linux server.

For simplicity's sake, let's say the IPs I've attached to this server are 1.1.1.57, 1.1.1.59 and 1.1.1.44

I'm trying to get .44 to come up as its own website and not having a lot  of luck. Right now I connect with SSH through the .57 address and it  works fine.

My problem is (was) when I tried to connect to .44, it would just  redirect to either the .57 address or the .57 folder (not sure which).  Anyway I further screwed something up, so now .44 isn't even working.  The .57 address still works fine for SSH and the default website.

I'm having a lot of trouble finding help or manuals on what I need  exactly (multiple IPs and multiple host names). Can anyone take a look  at my files and point out any glaringly stupid mistakes I might have  made:

/etc/apache2/sites/available/000-default.conf
```

<VirtualHost 1.1.1.57>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

/etc/apache2/sites/available/my-other-site.conf
```

<VirtualHost 1.1.1.44>
        ServerName my-other-site.com 
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/my-other-site/public_html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

/etc/hosts
```

127.0.0.1       localhost
127.0.1.1       TheNameOfMyServer
1.1.1.44         www.my-other-site.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

/etc/hostname
```

TheNameOfMyServer

```

/etc/network/interfaces
```

# The loopback network interface - do not adjust
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 1.1.1.57
netmask 255.255.255.224
gateway 1.1.1.33
dns-nameservers 8.8.8.8 8.8.4.4

# second ip address - unused
auto eth0:1
iface eth0:1 inet static
address 1.1.1.59
netmask 255.255.255.224

# my-other-site.com
auto eth0:2
iface eth0:2 inet static
address 1.1.1.44
netmask 255.255.255.224

```


I'd like to thank anyone that takes a look at this and provides feedback!

---

### Post by dan109 on 2014-05-29
Just an update... I rebooted the server and now I can't SSH into it. Woops. Let me know if anyone has any ideas what I'm screwing up. Thanks

---

### Post by TheFu on 2014-05-29
web servers don't usually need to be on differnent IP addresses.  Use name-based virtual servers inside the web-server config.  I've seen 300+ different domains hosted on a single IP.

The only reason to both with other IPs is 
* to connect to different subnets (backup LAN, administration LAN)
* to add redundant primary network connections for clustering
* to support IP-based SSL connections - i.e. HTTPS that listen on port 443.

For port 80 connections, it just isn't necessary.

Routing becomes non-trivial when multiple network devices are on the same subnet.  Connections will come in on 1 IP, but leave on the default interface which has the route back to the origination. I suppose you could split up the internet into 3 different areas and manually modify the routing with 1/3rd going to different parts of the world ... but why?

Who provided the netmasks? ARE you positive those are correct for each IP?
1.1.1.32/27 is the network ... so all the IPs are in the same subnet.  Each will need a gateway specified, probably .33.

Oh - and hostnames/DNS names are case-insensitive. Mixing case just messes with scripts - though it shouldn't be any problem.

We stopped using apache a few years ago, so I don't feel comfortable recommending any settings there. Sorry.

---

