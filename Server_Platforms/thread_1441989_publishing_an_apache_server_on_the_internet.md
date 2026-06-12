---
title: "publishing an apache server on the internet"
date: 2010-03-29
forum: Server Platforms
---

### Post by maraja on 2010-03-29
Hi,

I have an LAMP Ubuntu server running perfectly when accessed from the local network.

Recently I switched to a new ISP to get a static IP (12.34.567.890) and I am now willing to publish that server over the internet.

I added a rule in the router setup redirecting port 80 to the server internal IP (192.168.3.33 - configured as static).

After having tested with the public IP from another location ([http://12.34.567.890](http://12.34.567.890)) and verified that the server responds correctly, I bought a domain name ([www.example.info](www.example.info)) and setup both the @ and www records (record type A) pointing to the public IP I got from my ISP provider (12.34.567.890).

Now, if I try to ping the domain, I get a response pointing to the proper IP:
```

$ ping www.example.info
$ PING www.example.info (12.34.567.890) 56(84) bytes of data
```

So I guess the DNS setup is fine.

When I try to load the site from Firefox, after a long wait all I get is:
```

The connection has timed out
The server at www.example.info is taking too long to respond.
```

I have been searched for solutions all day long with no positive results.

Not sure if I am missing one or more settings as my knowledge is not that deep in this area.

Is there anyone willing to give me some clues?

Any further info you may need please do not hesitate to ask.

Thanks a lot in advance for your time

---

### Post by terazen on 2010-03-29
After trying to get to the site from a public ip you can check your logfiles to see if your apache server is receiving the requests and if it had an error with one of them.
/var/log/apache2/access.log
/var/log/apache2/error.log

---

### Post by maraja on 2010-03-29
thanks, no entries both in the access and the error logs :(

---

### Post by lisati on 2010-03-29
Check out the "Shields up" website: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Take a look at what it says for port 80.

(edit: it seems to be on a "go slow" for me at the moment)

---

### Post by volkswagner on 2010-03-29
How long ago did you set the DNS record?  Have you waited long enough for it to propagate?

Does the server still allow access to apache2 via the external ip address?

If you open a terminal and run

```
host yourdoman.info
```

What do you get?

---

### Post by maraja on 2010-03-29
> **lisati said:**
> Check out the "Shields up" website: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Take a look at what it says for port 80.

(edit: it seems to be on a "go slow" for me at the moment)

sorry but I cannot find any clue on that site

---

### Post by maraja on 2010-03-29
> **volkswagner said:**
> How long ago did you set the DNS record?  Have you waited long enough for it to propagate?

6 hours now


> Does the server still allow access to apache2 via the external ip address?

how do I set apache2 to allow access via the external ip? I guess this may be the issue....

> If you open a terminal and run

```
host yourdoman.info
```

What do you get?

host [www.example.info](www.example.info)
[www.example.info](www.example.info) has address 12.34.567.890

---

### Post by chrisinspace on 2010-03-29
> **maraja said:**
> 6 hours now

That's probably not long enough.  Public DNS records can take 24 to 48 hours to fully propagate.  Can you reach your site just using the IP address?

---

### Post by maraja on 2010-03-29
> **chrisinspace said:**
> That's probably not long enough.  Public DNS records can take 24 to 48 hours to fully propagate.  Can you reach your site just using the IP address?

yes, well I will wait till tomorrow then and will let you know. Strange that ping and host both return the correct ip address, I guess they both rely on DNS.

thanks

---

### Post by terazen on 2010-03-29
When you did the ping test from "another location" I was under the impression that meant DNS worked.

Do you get an entry in the access log when you access the server by ip address from the other location?

---

### Post by maraja on 2010-03-29
> **terazen said:**
> When you did the ping test from "another location" I was under the impression that meant DNS worked.

Do you get an entry in the access log when you access the server by ip address from the other location?

yes, I get an entry in the access log when using the ip address

---

### Post by cdenley on 2010-03-29
> **maraja said:**
> yes, I get an entry in the access log when using the ip address

Which IP address? LAN or WAN? Did you try it from the other location, or from the same LAN? Some routers will not do port forwarding for requests originating from your LAN.

Do this from inside AND outside your LAN.
```

nc -z -v -w 5 mydomain.com 80

```

---

### Post by maraja on 2010-03-29
> **cdenley said:**
> Which IP address? LAN or WAN? Did you try it from the other location, or from the same LAN? Some routers will not do port forwarding for requests originating from your LAN.

I can access the site from a different location using its external ip (12.34.567.890). Port forwarding is fine, at least from outside the LAN.


> 
Do this from inside AND outside your LAN.
```

nc -z -v -w 5 mydomain.com 80

```

from inside the lan (in a terminal session I started using the external ip, i.e. ssh root@12.34.567.890) I get:
```

nc -z -v -w 5 www.example.info 80
DNS fwd/rev mismatch: www.example.info != dslc-012-034-567-890.pools.arcor-ip.net
www.example.info [12.34.567.890] 80 (www) : Connection timed out

```

from outside the lan, actually my house, I get the same result:
```

nc -z -v -w 5 www.example.info 80
DNS fwd/rev mismatch: www.example.info != dslc-012-034-567-890.pools.arcor-ip.net
www.example.info [12.34.567.890] 80 (www) : Connection timed out

```

---

### Post by volkswagner on 2010-03-29
> **maraja said:**
> 6 hours now




how do I set apache2 to allow access via the external ip? I guess this may be the issue....



host [www.example.info](www.example.info)
[www.example.info](www.example.info) has address 12.34.567.890

To verify your server is allowing access to apache2 via your external ip, enter [http://12.34.567.890](http://12.34.567.890) in a browser not on the server lan.

If the above host command response is your actual isp provided address, I would say DNS is working and propagated.


Verify your server can access the internet by running the following from your server

```
host google.com
```

If your server is accessing the internet fine, I would verify you dont have a hardware or software firewall blocking port 80.

You may want to post your apache2 config files.

---

### Post by cdenley on 2010-03-29
DNS isn't the issue. Assuming this command run from your LAN says "open"...
```

nc -z -v -w 5 192.168.3.33 80

```
...then your server isn't the issue. Either your router isn't port forwarding, or your ISP is blocking port 80 (and your router doesn't port forward LAN traffic).

EDIT: Actually, re-reading your post, something is inconsistent. You said you can access the site remotely by connecting to its IP, yet when you attempt to establish a connection on port 80 using the command I gave you, it fails even though it is connecting to the same IP. Can you access the site from home at all?

---

### Post by maraja on 2010-03-29
> **volkswagner said:**
> To verify your server is allowing access to apache2 via your external ip, enter [http://12.34.567.890](http://12.34.567.890) in a browser not on the server lan.

If the above host command response is your actual isp provided address, I would say DNS is working and propagated.

hmmm, if I try a traceroute it always hang after 13 hops with no more replies.

However, when I use the public server ip address from my house, I can see the home page.


> host google.com

this is what I get:
```
host google.com
google.com has address 74.125.43.147
google.com has address 74.125.43.104
google.com has address 74.125.43.103
google.com has address 74.125.43.106
google.com has address 74.125.43.105
google.com has address 74.125.43.99
google.com mail is handled by 200 google.com.s9a2.psmtp.com.
google.com mail is handled by 100 google.com.s9a1.psmtp.com.
google.com mail is handled by 400 google.com.s9b2.psmtp.com.
google.com mail is handled by 300 google.com.s9b1.psmtp.com.

```


> If your server is accessing the internet fine, I would verify you dont have a hardware or software firewall blocking port 80.

in such case I guess I should not be able to reach the server even when using its public IP, am I wrong?

Anyways, for sure there is no hw firewall, is there any clue about how to find out if there is a software firewall? Sorry but I still have many things to learn about servers... 

> You may want to post your apache2 config files.

I can do that tomorrow, actually is late evening for me and its time for some rest :)

---

### Post by cdenley on 2010-03-29
> **maraja said:**
> 
However, when I use the public server ip address from my house, I can see the home page.


This output you posted seems to indicate this is not the case.
```

nc -z -v -w 5 www.example.info 80
DNS fwd/rev mismatch: www.example.info != dslc-012-034-567-890.pools.arcor-ip.net
www.example.info [**12.34.567.890**] 80 (www) : **Connection timed out**

```
You failed to establish a connection on port 80 to your public server IP from your house. If you can't connect on port 80, you can't see your home page.
```

nc -z -v -w 5 12.34.567.890 80

```

---

### Post by maraja on 2010-03-29
> **cdenley said:**
> DNS isn't the issue. Assuming this command run from your LAN says "open"...
```

nc -z -v -w 5 192.168.3.33 80

```
...then your server isn't the issue. Either your router isn't port forwarding, or your ISP is blocking port 80 (and your router doesn't port forward LAN traffic).

:o But I can reach the server with its public IP, so I do not think the ISP is blocking port 80 otherwise I should not be able to see the home page anyways, am I wrong?

I set the router to forward the external IP (12.34.567.890 on port 80) toward the internal IP (192.168.3.33 again on port 80).

If port 80 is blocked I shouldn't be able to see the home page when trying to access in both cases ([http://12.34.567.890](http://12.34.567.890) and [http://www.example.info](http://www.example.info)), wrong?

---

### Post by cdenley on 2010-03-29
> **maraja said:**
> :o But I can reach the server with its public IP, so I do not think the ISP is blocking port 80 otherwise I should not be able to see the home page anyways, am I wrong?

I set the router to forward the external IP (12.34.567.890 on port 80) toward the internal IP (192.168.3.33 again on port 80).

If port 80 is blocked I shouldn't be able to see the home page when trying to access in both cases ([http://12.34.567.890](http://12.34.567.890) and [http://www.example.info](http://www.example.info)), wrong?

As I said, something is inconsistent. The output you posted clearly indicates a failure to connect to your web server from home.

---

### Post by maraja on 2010-03-29
> **cdenley said:**
> 
You failed to establish a connection on port 80 to your public server IP from your house. If you can't connect on port 80, you can't see your home page.
```

nc -z -v -w 5 12.34.567.890 80

```

I can grant you I can see the home page from my house by using: [http://12.34.567.890](http://12.34.567.890)

However I also tried the following:
nc -z -v -w 5 12.34.567.890 80
dslc-012-034-567-890.**pools.arcor-ip.net** [12.34.567.890] 80 (www) : Connection timed out

And when I try a traceroute it hangs at hop 13:
```

Hop	Hostname	IP	Time 1	Time 2
1	maraja-xps1330.local	192.168.1.105	0.143ms	
1	192.168.1.1	192.168.1.1	2.015ms	
1	192.168.1.1	192.168.1.1	1.490ms	
2	192.168.100.1	192.168.100.1	69.915ms	
3	host1-63-static.50-88-b.business.telecomitalia.it	88.50.63.1	70.204ms	
4	r-co37-vl2.opb.interbusiness.it	217.141.107.132	69.273ms	
5	172.17.4.89	172.17.4.89	73.322ms	
6	172.17.6.89	172.17.6.89	71.759ms	
7	mil26-ibs-204.mil.seabone.net	93.186.128.81	71.096ms	
8	telia-2-fra34.fra.seabone.net	89.221.34.166	104.717ms	
9	telia-2-fra34.fra.seabone.net	89.221.34.166	104.947ms	
10	ffm-bb1-link.telia.net	80.91.247.166	127.538ms	
11	ffm-b7-link.telia.net	80.91.251.52	93.826ms	
12	**arcor-ic-120246-ffm-b6.c.telia.net**	213.248.84.146	108.898ms	
13	145.254.10.78	145.254.10.78	118.130ms	
14	no	reply	*	
15	no	reply	*	
16	no	reply	*	
17	no	reply	*	
18	no	reply	*	
19	no	reply	*	
20	no	reply	*	
21	no	reply	*	
22	no	reply	*	
23	no	reply	*	
24	no	reply	*	
25	no	reply	*	
26	no	reply	*	
27	no	reply	*	
28	no	reply	*	
29	no	reply	*	
30	no	reply	*	
31	no	reply	*	

```

maybe a problem with **archor**?

---

### Post by cdenley on 2010-03-29
You can try removing the timeout.
```

nc -z -v 12.34.567.890 80

```
Does it take a long time to connect? If your browser can connect, then that command should as well, absolutely, 100% of the time, except maybe if you're using a proxy.

---

### Post by maraja on 2010-03-29
SOLVED!

sorry to have wasted your time buddies, but when closing the ssh connection I have noticed the IP address I set in the DNS records had one wrong number...

If it happen that anyone of you visits the area surrounding  [Como]("http://maps.google.it/maps?f=q&source=s_q&hl=en&geocode=&q=como&sll=41.442726,12.392578&sspn=18.691915,39.506836&ie=UTF8&hq=&hnear=Como,+Lombardy&t=h&z=13") in the future be sure to get in touch as I owe you a bottle of nice Italian wine!

Thanks a lot for your kind support, I love Ubuntu and this concept where everyone is helping each other, a radical change compared to 'closed' operating systems.

---

