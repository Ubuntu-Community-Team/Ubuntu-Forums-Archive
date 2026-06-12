---
title: "Web server, behind wireless router"
date: 2007-03-17
forum: Server Platforms
---

### Post by maniacmusician on 2007-03-17
I've got my apache mostly set up; I have various port-based VirtualHosts. I thought that if I forwarded those ports from my router to my computer, and navigated to [homeipaddress]:[portnumber], I'd arrive at the site I was hosting. 

I tried that; forwarded port 82 to my computer (which on my home network is 192.168.2.5). Then I entered [homeip]:[82] into a browser, but I just get a page not found. 

suggestions?

warning: I absolutely don't know what I'm doing. I haven't tried this before so I'm just screwing around and seeing what happens.

---

### Post by Nikron on 2007-03-17
What's your ports.conf look like then?  That may be the problem..

---

### Post by maniacmusician on 2007-03-17
> **Nikron said:**
> What's your ports.conf look like then?  That may be the problem..
Good point. I checked it, and all it had was "Listen 80." I changed it to be:

```

Listen 80
Listen 81
Listen 82

```
and restarted apache. Still gives me "page not found". 

I don't need any special service for this right? It should just come up?

---

### Post by maniacmusician on 2007-03-18
bump

---

### Post by Nikron on 2007-03-18
> **maniacmusician said:**
> bump

You'll get more help if you post the virtual host files, and maybe the httpd.conf file..

---

### Post by maniacmusician on 2007-03-18
> **Nikron said:**
> You'll get more help if you post the virtual host files, and maybe the httpd.conf file..
Here they are. The default file, vhost1, and vhost2. 

httpd.conf was empty.

---

### Post by Mr. C. on 2007-03-18
You are using your WAN IP to connect to your LAN services ?

No good - you must user your LAN IPs to connect to your LAN services.

Run ```
netstat -ln
``` to see if ports 80...82 have a listener.

MrC

---

### Post by maniacmusician on 2007-03-18
Here's the relative part (I think it's saying that those ports are listening):
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8010            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1550            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN
tcp6       0      0 :::79                   :::*                    LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::81                   :::*                    LISTEN
tcp6       0      0 :::82                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
udp        0      0 0.0.0.0:32768           0.0.0.0:*
udp        0      0 0.0.0.0:32934           0.0.0.0:*
udp        0      0 0.0.0.0:8010            0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*

```

As for what you said; How can I access my LAN IPs from a remote computer? I thought that forwarding the ports through the router would be the only way.

Another thing; I'm not actually testing from a remote computer. I'm inside my LAN but trying to access through the WAN. Simply because I don't have access to a remote computer until tomorrow. But I figured that this should work anyways since entering my WAN in a browser brings me to my router's config page and if I put a :82 after it, it should forward that to my machine.

---

### Post by Nikron on 2007-03-18
That might not work.  I changing my apache2 ports similarly and forwarding them, and computers from inside the LAN could still not access the server thru the LAN.  However, from outside of the WAN they did indeed work.

---

### Post by Mr. C. on 2007-03-18
Good, there are listeners.

Your understanding of port forwarding is basically correct.  It is important to understand that a port forward is typically based on a WAN IP/port -> LAN IP/port *from the WAN interface*. It does not imply that the forward will work from the LAN using the WAN IP.

In order to use your WAN IP from the LAN, your router must support this transparency.  If it does not, you must use your LAN IPs while you are within your LAN.  If yours supports this, and port forwarding at the same time, then there's no problem.

Check your access logs to see if your connections are being made, and check your router's logs.

MrC

---

