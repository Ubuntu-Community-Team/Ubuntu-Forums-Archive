---
title: "*nix noob, setting up php dev/test server, almost got it"
date: 2010-08-25
forum: Server Platforms
---

### Post by raccer on 2010-08-25
**Goal:** A dev/test server piped to the interwebs via dyndns.org & accessible via my existing domain name.

**Setup:**
I have Lucid with the lamp stack up & running, ethernet to my netgear wgr614, then comcast cable residential (thus the dyndns)

At one point I was able to connect to Apache via local machines, but not external machine/networks, so I kept changing settings and then I broke that, & Apache went dark. I have my domain name pointed at dyndns correctly & my router has the dyndns update utility up & running, and tcp 8080 is fwd'ed to my server ip. 
I'm 99% sure my issues are in the server settings... 

The files listed below I have modified, If it's not here I haven't touched it (I think :D) & the settings are default...

/etc/network/interfaces
```

#loopback network interface
auto lo
iface lo inet loopback

#primarynetwork interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

/etc/resolv.conf
```

nameserver 68.87.76.182
nameserver 68.87.78.134

```

/etc/apache2/httpd.conf
```

ServerName www.mydomain.com

```

etc/apache2/ports.conf
```

NameVirtualHost *:8080
Listen 8080
...(remainder omitted & unchanged)

```

/etc/apache2/sites-available/default
```

<VirtualHost *:8080>
...(remainder omitted & unchanged)

```

---

### Post by BkkBonanza on 2010-08-26
When you try both your public IP and domain name what response/messages exactly do you get? Also what happens when you use the local IP?
I'm afraid "going dark" just doesn't give enough detail.

---

### Post by raccer on 2010-08-26
Thanks for the reply Bkk,

I remember writing the post thinking "I'm going to put every detail in here so there's no way they would need any more info...;)"

Requests from external machines/networks have always timed out (regardless of domain name vs. IP), when I had it working I could load the "It Works!" page from my desktop on the private LAN (using the local IP). I think I can get back to that state if I tinker a little more...

---

### Post by raccer on 2010-08-26
OK,
Just found out apache wasn't starting/running because of a port conflict (err msg follows)

"('98')Address already in use: make_sock: could not bind to address 0.0.0.0:8080 
no listening sockets available, shutting down
Unable to open logs"

Is there a way to list what is using different ports?

---

### Post by raccer on 2010-08-26
Just found out about netstat, so here is the output
netstat -an | egrep 'Proto|Listen'
```

Proto Recv-Q Send-Q  Local Address   Foreign Address  State
tcp        0      0  127.0.0.1:3306        0.0.0.0:*  LISTEN
tcp        0      0    0.0.0.0:8080        0.0.0.0:*  LISTEN
Proto RefCnt  Flags    Type     State      I-Node Path
unix  2       [ ACC ]  STREAM   LISTENING  2705   @/com/ubuntu/upstart
unix  2       [ ACC ]  STREAM   LISTENING  4042   /var/run/mysqld/mysqld.sock

```

---

### Post by Ryan Dwyer on 2010-08-26
Make Apache listen on port 80, then forward external 8080 to internal 80.

---

### Post by raccer on 2010-08-26
Hi Ryan,
Thanks for the reply, 

Did you mean fwd from my router? It's a little different as my router only gives an option to open up a specific port (or range of ports) under the forwarding section, it does not have options/settings for external/internal ports...

here is a picture of the fwd'ing tab in my router:
[http://portforward.com/english/routers/port_forwarding/Netgear/WGR614v7/Apache.htm]("http://portforward.com/english/routers/port_forwarding/Netgear/WGR614v7/Apache.htm")

---

### Post by raccer on 2010-08-26
WooHoo!

I changed apache back to 80, my fwd'ing back to 80, and now it works!?

This was how I had it setup yesterday, when it wasn't responding to external http requests (timing out)?

I wonder whats different between then & now???

```

Querying my domain name [my ip]...

[begin response]

HTTP/1.1 200 OK
Date: Thu, 26 Aug 2010 22:07:16 GMT
Server: Apache/2.2.14 (Ubuntu)
Last-Modified: Wed, 25 Aug 2010 18:58:44 GMT
ETag: "2094f-b1-48eaa78879516"
Accept-Ranges: bytes
Content-Length: 177
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
[end response]

```

---

### Post by BkkBonanza on 2010-08-26
That's a bit limited. *Note to self, don't buy a Netgear Router.

Try using **sudo netstat -lntp** 
This will show which process is currently using port 8080. You'll need to resolve that conflict. There's no reason why 8080 isn't a good a port to use, particularly if you have no choice but two services can't listen on the same one.

---

