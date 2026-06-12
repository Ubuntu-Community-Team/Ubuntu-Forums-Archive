---
title: "DNS server and webserver using bind9 same machine"
date: 2009-06-30
forum: Server Platforms
---

### Post by Lukas1 on 2009-06-30
Hi,

I am running jaunty server addition (x86) with gnome. I am trying to use this machine as both my dns server and my webserver. I registered a domain name (globalcapeesh.com) and the whois all looks right. I registered two nameservers and pointed it to my isp supplied static ip address. 

The two nameservers I set are ns1.globalcapeesh.com and ns2.globalcapeesh.com

I followed Sam Davis's tutorial on how to set up a chaching nameserver and then how to set up a master dns server using bind9 - [http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/](http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/) 

Here's where it gets funny:
If you go to [www.globalcapeesh.com]("http://www.globalcapeesh.com") it does not work but if you go to ns1.globalcapeesh.com it does work. 

I was wondering if someone has experience with a similar problem and what they did to fix it. My next thought was to reinstall bind but I would like to see if anyone else can offer better ideas first. Thank you!!

---

### Post by jhannah on 2009-06-30
When you register a name server, you are effectively adding the registered hostname and IP address you supply to the global name servers database (these are called glue records). Without this, there would be a catch 22 when trying to resolve ns#.yourdomain.com. As such, these will always resolve just fine- regardless of your DNS server setup provided the machine trying to resolve the domain is setup to query a server which will end up looking up the NS domain from a DNS root server.

To give you an example, here is what a dig trace looks like for your NS domain:
```

jhannah@noel:~$ dig +trace ns1.globalcapeesh.com

; <<>> DiG 9.6.1 <<>> +trace ns1.globalcapeesh.com
;; global options: +cmd
.            3600    IN    NS    FWDR-12.FWDR-0.FWDR-242.FWDR-71.
.            3600    IN    NS    FWDR-12.FWDR-0.FWDR-250.FWDR-71.
;; Received 192 bytes from 192.168.1.1#53(192.168.1.1) in 36 ms

ns1.globalcapeesh.com.    172738    IN    A    72.54.150.146
;; Received 55 bytes from 71.242.0.12#53(FWDR-12.FWDR-0.FWDR-242.FWDR-71) in 10 ms

```

If I run a similar trace against [www.globalcapeesh.com](www.globalcapeesh.com), I don't get a valid result:

```

jhannah@noel:~$ dig +trace www.globalcapeesh.com 

; <<>> DiG 9.6.1 <<>> +trace www.globalcapeesh.com
;; global options: +cmd
.            3600    IN    NS    FWDR-12.FWDR-0.FWDR-242.FWDR-71.
.            3600    IN    NS    FWDR-12.FWDR-0.FWDR-250.FWDR-71.
;; Received 192 bytes from 192.168.1.1#53(192.168.1.1) in 3 ms

com.            154673    IN    NS    G.GTLD-SERVERS.NET.
[...snip...]
com.            154673    IN    NS    F.GTLD-SERVERS.NET.
;; Received 455 bytes from 71.250.0.12#53(FWDR-12.FWDR-0.FWDR-250.FWDR-71) in 27 ms

globalcapeesh.com.    172800    IN    NS    ns1.globalcapeesh.com.
globalcapeesh.com.    172800    IN    NS    ns2.globalcapeesh.com.
;; Received 107 bytes from 192.35.51.30#53(F.GTLD-SERVERS.NET) in 89 ms

;; connection timed out; no servers could be reached

```

Even if I try to hit your IP address directly to resolve [www.globalcapeesh.com](www.globalcapeesh.com), it times out (for this, you would use: 'dig domain.com @nameserver'). Which makes me think that BIND is either not bound to the correct IP or not listenening. If it were misconfigured, I would expect to get a NXDOMAIN responce or something along those lines.

What does your bind config look like and what are the results of running this?

```
netstat -nap | grep ":53"
```

Hope that helps make sense of DNS somewhat.

---

### Post by Lukas1 on 2009-07-01
Thank you for posting, Joe. 

Here is that output:

bigdog@bigdog:~$ netstat -nap | grep ":53"
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 10.0.1.2:53             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::53                   :::*                    LISTEN      -               
udp        0      0 10.0.1.2:53             0.0.0.0:*                           -               
udp        0      0 127.0.0.1:53            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp6       0      0 :::53                   :::*                                -               


My DNS has The zones configured as should be, /zones/globalcapeesh.com.db and also the reverse.

Here is that.db file:

globalcapeesh.com. IN SOA ns1.globalcapeesh.com. admin.globalcapeesh.com. (

2007031001
28800
3600
604800
38400
)

globalcapeesh.com. IN NS ns1.globalcapeesh.com.
IN A 10.0.1.2
mail.globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.
globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.

www IN CNAME ns1
mail IN A 10.0.1.2
ns1 IN A 10.0.1.2


**  rev.1.0.10.in-addr.arpa  :  **

@ IN SOA ns1.globalcapeesh.com. admin.globalcapeesh.com. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS ns1.globalcapeesh.com.
2 IN PTR globalcapeesh.com.

---

### Post by Lukas1 on 2009-07-01
I mean thank you JON

---

### Post by gombadi on 2009-07-01
It looks like you have dns running on bigdog and it also looks like it is on a private network - 10.0.1.2

Is your router setup to forward udp port 53 to bigdog?

The other problem I see is -
> 
globalcapeesh.com. IN NS ns1.globalcapeesh.com.
IN A 10.0.1.2
mail.globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.
globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.

www IN CNAME ns1
mail IN A 10.0.1.2
ns1 IN A 10.0.1.2


If this is the public dns server for globalcapeesh.com and I ask for the ip address of mail.globalcapeesh.com will it return 10.0.1.2?

That is a private network ip address and I have no way of getting to it from my machine.

---

### Post by Lukas1 on 2009-07-01
I set up forwarding on udp and it looks like that was the problem!! Thank you!

---

### Post by windependence on 2009-07-02
You really don't need to run your own DNS at all to run a web site. It would probably be better just to use the DNS servers from your registrar than running your own DNS unless you just wanna know how to do it.

-Tim

---

### Post by Lukas1 on 2009-07-02
Well all the posts I read kind of pointed it out that way. Anyways this is how most websites do it as far as I know, so I'm glad I learned.

---

### Post by windependence on 2009-07-02
I know. For some reason here on the Ubuntu forums this has become an epidemic. In fact, most sites don't run their own DNS. I think all this came from the perfect server tutorial, which implies that you need to run DNS to run a web server. You really don't, and it's probably better not to, unless you need it for some reason like split DNS for mail or some other compelling reason.

-Tim

---

### Post by Lukas1 on 2009-07-21
OK, I' haven't had too much time to play with this lately, but here is where I'm at:

I got the website to appear on the network,  but it is not accessible from the outside. For example, if you were to go to [www.just-ping.com](www.just-ping.com) and try to ping globalcapeesh.com you would not get any response. However in the network if I type [www.globalcapeesh.com](www.globalcapeesh.com) in the browser, I do get the main web page hosted on my server. 

Does anyone know why this would be accessible locally on the network, but yet not from outside?

---

### Post by grantemsley on 2009-07-21
Because the 10.x.x.x addresses are local only - you can't use them on the internet.

Your website has to be on a public IP address, OR you have to have a router (which is on a public IP) forward port 80 to your internal webserver.

Also for DNS - try everydns.net - it's free and easy to setup DNS records at, and they have 6 servers in different locations so they won't go down.

---

### Post by Lukas1 on 2009-08-01
So then which records do I set with my public IP address?

[I]
globalcapeesh.com. IN SOA ns1.globalcapeesh.com. admin.globalcapeesh.com. (

2007031001
28800
3600
604800
38400
)

globalcapeesh.com. IN NS ns1.globalcapeesh.com.
IN A 72.54.150.146
mail.globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.
globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.

www IN CNAME ns1
mail IN A 72.54.150.146
ns1 IN A 72.54.150.146[/I]

I set all local IPs here to my static IP address. Is that how it is supposed to be? How long does it need top propogate or should it work right off the bat?

---

### Post by tobiness on 2009-08-01
Most routers have the ip 192.168.0.1 You Foward DNS To That Then That Sends It Out Through The Public Ip, Otherwise It Will Be Local Only Because You Are Not communicating with the public ip just local ones (192.168.0.0 to 192.168.255.255) Does That Make Any Sence To You? (Hope It Helped)

---

### Post by tobiness on 2009-08-01
i think it should work straight away providing you restart apache and bind (THINK)

---

### Post by Lukas1 on 2009-08-03
I tried that previous zones file and no dice. I will try to change the mail and ns pointers to the local server and let you know how it goes.

---

### Post by Lukas1 on 2009-08-05
I tried this last:

[I]globalcapeesh.com. IN SOA ns1.globalcapeesh.com. admin.globalcapeesh.com. (

2007031001
28800
3600
604800
38400
)

globalcapeesh.com. IN NS ns1.globalcapeesh.com.
IN A 72.54.150.146
mail.globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.
globalcapeesh.com. IN MX 10 mail.globalcapeesh.com.

www IN CNAME ns1
mail IN A 10.0.1.2
ns1 IN A 10.0.1.2[/I]

This setup works locally on the network, but does not work when I ping it. Any other ideas?

---

