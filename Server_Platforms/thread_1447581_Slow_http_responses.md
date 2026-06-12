---
title: "Slow http responses"
date: 2010-04-05
forum: Server Platforms
---

### Post by mrdaze0 on 2010-04-05
Hi, I have a couple of servers running on a local network.  My ubuntu server has been giving me problems since having to change the IP address.  I get 15 to 20 seconds delay before the html page is returned for the request.  This happens with internal ip address being used, or if the url is used.  Ping of the url gives
[B]Pinging hs***ts.com [173.197.144.174] with 32 bytes of data:
Reply from 173.197.144.174: bytes=32 time<1ms TTL=64
Reply from 173.197.144.174: bytes=32 time<1ms TTL=64
Reply from 173.197.144.174: bytes=32 time<1ms TTL=64
Reply from 173.197.144.174: bytes=32 time<1ms TTL=64[/B]
Ping of the internal ip gives
[B]Pinging 192.168.1.112 with 32 bytes of data:
Reply from 192.168.1.112: bytes=32 time=3ms TTL=64
Reply from 192.168.1.112: bytes=32 time<1ms TTL=64
Reply from 192.168.1.112: bytes=32 time<1ms TTL=64
Reply from 192.168.1.112: bytes=32 time<1ms TTL=64[/B]

ISP was changed this morning so the external IP address changes and with the equipment installed by the ISP I had to change internal IP's to 192.168.1.* from 192.168.0.*

I am at a loss as to why the http response from the server is so slow when all other methods of connecting are fast.  SSH is almost instantaneous.  


Any ideas appreciated.

---

### Post by cdenley on 2010-04-05
Run this from a client and the server
```

time nc -z -v 192.168.1.112 80

```

---

### Post by mrdaze0 on 2010-04-05
> **cdenley said:**
> Run this from a client and the server
```

time nc -z -v 192.168.1.112 80

```
on the server the response was:
```

mdazey@www:~$ time nc -z -v 192.168.1.112 80
www.hs***ts.com [192.168.1.112] 80 (www) open

real    0m0.002s
user    0m0.000s
sys     0m0.000s

```

I do not have another system that will let me run that command but I have wireshark and I fired that up on one of the systems.  
Initial http message
Apr  5, 2010 15:48:18.612848000
Final http message
Apr  5, 2010 15:48:28.747943000
10 seconds to load a very simple webpage over the lan.

---

### Post by cdenley on 2010-04-05
> **mrdaze0 said:**
> 
I do not have another system that will let me run that command but I have wireshark and I fired that up on one of the systems.  
Initial http message
Apr  5, 2010 15:48:18.612848000
Final http message
Apr  5, 2010 15:48:28.747943000
10 seconds to load a very simple webpage over the lan.

What exactly was the request? Did it take 10 seconds to transfer the html content, or does that include any image or scripts included on that page? Do you experience the issue when accessing the site by IP?

---

### Post by mrdaze0 on 2010-04-05
The 10 seconds did include loading html content no scripts just pure html with a 1 image which is 18.5KB  
This happens when accessing by url, external ip, or internal ip of the server.

---

### Post by cdenley on 2010-04-05
> **mrdaze0 said:**
> The 10 seconds did include loading html content no scripts just pure html with a 1 image which is 18.5KB  
This happens when accessing by url, external ip, or internal ip of the server.

Any html content is going to be insignificant compared to the image, so I will focus on that, and I will assume it takes 10 seconds to download it.
```

time bash -c "echo -e \"HEAD /path/to/image.jpg HTTP/1.0\\n\"|nc 192.168.1.112 80"
time bash -c "echo -e \"GET /path/to/image.jpg HTTP/1.0\\n\"|nc 192.168.1.112 80">/dev/null

```

---

### Post by mrdaze0 on 2010-04-05
> **cdenley said:**
> Any html content is going to be insignificant compared to the image, so I will focus on that, and I will assume it takes 10 seconds to download it.
```

time bash -c "echo -e \"HEAD /path/to/image.jpg HTTP/1.0\\n\"|nc 192.168.1.112 80"
time bash -c "echo -e \"GET /path/to/image.jpg HTTP/1.0\\n\"|nc 192.168.1.112 80">/dev/null

```
It is taking more like 15 seconds.
on the server from lan ip
```
root@www:/# time bash -c "echo -e \"HEAD /images/HLogo.png HTTP/1.0\\n\"|nc 192.168.1.112 80"
HTTP/1.1 200 OK
Date: Mon, 05 Apr 2010 21:32:30 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Wed, 18 Nov 2009 03:57:28 GMT
ETag: "63a-49d2-4789d3dc17ee8"
Accept-Ranges: bytes
Content-Length: 18898
Connection: close
Content-Type: image/png


real    0m0.004s
user    0m0.000s
sys     0m0.000s
root@www:/# time bash -c "echo -e \"GET /images/HLogo.png  HTTP/1.0\\n\"|nc 192.168.1.112 80">/dev/null

real    0m0.004s
user    0m0.000s
sys     0m0.000s

```

on the server from the external IP:
```
root@www:/# time bash -c "echo -e \"HEAD /images/HLogo.png HTTP/1.0\\n\"|nc 173.197.144.174 80"
HTTP/1.1 200 OK
Date: Mon, 05 Apr 2010 21:41:12 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Wed, 18 Nov 2009 03:57:28 GMT
ETag: "63a-49d2-4789d3dc17ee8"
Accept-Ranges: bytes
Content-Length: 18898
Connection: close
Content-Type: image/png


real    0m15.018s
user    0m0.000s
sys     0m0.000s
root@www:/# time bash -c "echo -e \"GET /images/HLogo.png  HTTP/1.0\\n\"|nc 173.197.144.174 80">/dev/null

real    0m15.017s
user    0m0.000s
sys     0m0.000s


```

---

### Post by cdenley on 2010-04-05
I just noticed that you posted your public IP. It seems to work fine for me.
```

cdenley@cdenley:~$ time bash -c "echo -e \"GET /images/HLogo.png  HTTP/1.0\\n\"|nc 173.197.144.174 80">/dev/null

real	0m0.473s
user	0m0.000s
sys	0m0.010s

```
So it works fine from your LAN and my computer. When you tried that command from an "external IP", was that from within the same LAN as the server? If not have you tried accessing it from anywhere else?

---

### Post by Kiwi76 on 2010-04-06
It loads pretty quickly (a second or two) for me as well, so I think cdenley is on to something asking if this problem is only occurring when accessing it via your LAN, and thus I'm going to guess this is a feature of your router/gateway from your new ISP at work here (since that is when the problem showed up). It seems to truly be working fine.

Feel lucky. My router/modem/gateway (AT&T U-Verse) lacks NAT loopback completely, and it always returns a "Server Not Found" error. I overcame this by adjusting my Windows HOSTS file to redirect my domain name to my LAN IP address before the request even leaves my PC (as the router won't let it leave and come back using the external IP address or domain name), and it works flawlessly now using that workaround.

If your client you are accessing this from is Windows based, try that.

If it's GNU/Linux and/or Ubuntu, I'm sure there must be a similar way, though I don't know it.

---

