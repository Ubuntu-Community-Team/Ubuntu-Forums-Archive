---
title: "Network Error (tcp_error) apache2 hosting"
date: 2008-05-26
forum: Server Platforms
---

### Post by JameoPotato on 2008-05-26
Hi,
I thought my domain was fully up and running finally but I have ran into another problem.
I can fully access my website from a computer on my server's network but not any other. I get this error message trying to open my domain from a proxy server (Tested the proxy and it is working):
```

    Network Error (tcp_error)

    A communication error occurred: "Operation timed out"
    The Web Server may be down, too busy, or experiencing other problems preventing it from responding to requests. You may wish to try again at a later time.

    For assistance, contact your network support team.


```Firefox


If it helps you diagnose the problem my domain is [www.jameopotato.com](www.jameopotato.com) . See the error for yourself. 

I ran a DNS check and my site has been up for over 2 days now and about 90% of DNS servers have it recognized so i'm sure that isn't the problem. 

I am suspicious of it being either my DHCP IP address or my router (D-LINK Wireless G).

My IP is Dynamic, but I have it set static on my router (LAN) and unless my router is rebooted it won't change (WAN).
My router is set to forward TCP port 80 through the firewall to my servers IP... so thats not the problem.

Any suggestions would be greatly appreciated, thank you

---

### Post by spiderbatdad on 2008-05-26
Assuming public ip is correct with DNS and local ip is correct with ip forwarded by router, check SeverName in httpd.conf. Make sure it is [www.jameopoato.com](www.jameopoato.com)

---

### Post by JameoPotato on 2008-05-26
It works perfectly fine if I browse to it from my laptop on the same network as the server.
I get my homepage and everything. 
I ran a DNS check and it is being forwarded to my Public IP correctly.

And it is NOT like I get a "server not found error". I get the specific "Network error (tcp_error)" which I have never seen before.

---

### Post by spiderbatdad on 2008-05-26
Router should be set to forward both, tcp/udp.
My browser times-out trying to load your site.

---

### Post by JameoPotato on 2008-05-26
My router is forwarding both TCP/UDP port 80 to 192.168.0.103 and my server is set static to 192.169.0.103.

When i run ifconfig i get something saying :
Link encap:Ethernet
(lists ethernet setting)
THEN
there is a second section:
Link encap:Local loopback
(lists more settings)
This line kinda makes me suspicious, "UP LOOPBACK RUNNING"

Should that second part be there? Is the server maybe replying only to local machines and not public ones. How do I disable Local Loopback?

---

### Post by spiderbatdad on 2008-05-26
local loopback is necessary for system processes. I'm not sure what your mean when you say,"My router is forwarding both TCP/UDP port 80 to 192.168.0.103 and my server is set static to 192.169.0.103."
Your server is run on the same ip as your primary ethernet connection. If ifconfig shows your inet address as 192.168.0.103 for eth0, then that is the address that should be forwarded. Your DNS provider should be set up with your public ip address. [www.whatismyip.com](www.whatismyip.com)

---

### Post by JameoPotato on 2008-05-26
Yes, yes, that is all set up correctly. I have made it that far.
[www.jameopotato.com](www.jameopotato.com) OR jameopotato.com both are set on DNS servers with a A record to 207.216.210.44 (my public ip). When I browse to jameopotato.com on my laptop I go right to my site and can see my homepage.
I thought I had it running perfectly, but when I tried to access it at work it didn't work. It times out. 
Do notice however that browsers successfully "connect to the server" but waits on a response. So DNS is CHECK.

Somewhere between my IP and my server there is a problem which pretty much narrows down to my router. 

I put my servers LAN IP (192.168.0.103) in the DMZ and that also gave no luck. 

My servers LAN IP is: 192.168.0.103 (STATIC) and public IP is 207.216.210.44 (DHCP) 
I have asked my ISP for a static Ip and i'm waiting to here from them but I should still be able to get my site working with a dynamic ip as long as it is not Constantly changing. 

another clue, i checked my routers log and recovered this:
"Xmas port scan attack from WAN (ip:203.158.221.226) detected."
203.158.221.226 is the IP of the proxy server I was using to test my site with... 
This leads me to believe that maybe my router's firewall is not accepting connections. 
Unfortunately I cannot connect my internet directly into my server or else I would update my IP address offsetting the DNS and then I would have no way to check if it was working from another computer (cause router would be unplugged).

Bout ready to go buy a Hosting certified router or something...

---

### Post by spiderbatdad on 2008-05-26
what is the 192.169 that you refer to? You say your server is set to static 192.169.0.103

---

### Post by JameoPotato on 2008-05-26
did I say 169? I meant 192.168.0.103

That is my Static LAN ip address under the router that all my "Port Forwarding rules" are set to. Example, Forward Port 80 TCP/UDP to IP: 192.168.0.103 (my server)

---

### Post by JameoPotato on 2008-05-26
And in case the local IP was the problem I just tried setting my LAN IP to DHCP. I was assigned 192.168.0.133. I then set my port forwarding to 192.168.0.133 instead of 192.168.0.103...
And still nothing changed. 
It still works from the local machine but not from the proxy or an outside source.

---

### Post by windependence on 2008-05-26
You have a DNS problem.

```
twincactus@Mako:~$ ping [http://www.jameopoato.com](http://www.jameopoato.com)
ping: unknown host [http://www.jameopoato.com](http://www.jameopoato.com)

twincactus@Mako:~$ nslookup [http://www.jameopoato.com](http://www.jameopoato.com)
Server:         205.171.3.65
Address:        205.171.3.65#53

** server can't find [http://www.jameopoato.com.domain.actdsltmp:](http://www.jameopoato.com.domain.actdsltmp:) NXDOMAIN
```

Check to make sure your domain is pointed at the correct IP address. Are you running a dynamic IP redirection service like dyndns or no-ip?

-Tim

---

### Post by JameoPotato on 2008-05-26
No i'm not running a dynamic ip redirection, should I be?. I thought for sure it was running. It is possible that it is just your DNS server that isn't picking it up because I ran [http://www.squish.net/dnscheck/](http://www.squish.net/dnscheck/) and all DNS servers EXCEPT for the top one correctly were forwarded to my Dynamic ip address.

---

### Post by JameoPotato on 2008-05-26
> **windependence said:**
> You have a DNS problem.

```
twincactus@Mako:~$ ping [http://www.jameopoato.com](http://www.jameopoato.com)
ping: unknown host [http://www.jameopoato.com](http://www.jameopoato.com)

twincactus@Mako:~$ nslookup [http://www.jameopoato.com](http://www.jameopoato.com)
Server:         205.171.3.65
Address:        205.171.3.65#53

** server can't find [http://www.jameopoato.com.domain.actdsltmp:](http://www.jameopoato.com.domain.actdsltmp:) NXDOMAIN
```

Check to make sure your domain is pointed at the correct IP address. Are you running a dynamic IP redirection service like dyndns or no-ip?

-Tim

Actually... you pinged, [www.jameopoato.com](www.jameopoato.com) ... it should be jameopotato.com

---

### Post by windependence on 2008-05-26
> **JameoPotato said:**
> No i'm not running a dynamic ip redirection, should I be?. I thought for sure it was running. It is possible that it is just your DNS server that isn't picking it up because I ran [http://www.squish.net/dnscheck/](http://www.squish.net/dnscheck/) and all DNS servers EXCEPT for the top one correctly were forwarded to my Dynamic ip address.

Understand, it's not MY DNS servers, this is what is being resolved on the web. What is your outside IP right now?

-Tim

---

### Post by windependence on 2008-05-26
> **JameoPotato said:**
> Actually... you pinged, [www.jameopoato.com](www.jameopoato.com) ... it should be jameopotato.com

Yep, my bad. Still what are you seeing as your outside IP address?

-Tim

---

### Post by JameoPotato on 2008-05-26
Router says, "207.216.210.44"

---

### Post by JameoPotato on 2008-05-27
this is how I have set my router:
[IMG]http://www.planetbee.com/Clipboard01.bmp[/IMG]

---

### Post by windependence on 2008-05-27
Go to [www.canyouseeme.org](www.canyouseeme.org) and check to make sure your port 80 is open.

-Tim

---

### Post by JameoPotato on 2008-05-27
Nope its blocked and you know what I read what that site says and I think my ISP is blocking port 80 for me...

I'm positive I know how to set up my router and apache2 to the new port, but can you explain no-ip.com to me?

UPDATE:
actually after running that tool some more I can't find a single port that is open. All respond to either connection refused or timed out... this makes me think that there is a firewall somewhere else... does ubuntu come with a firewall???



Okay srry to update this again, but to be more specific, I get "Connection Timed OUt" on port 80, and connection refused on all other ports.

---

### Post by windependence on 2008-05-27
> **JameoPotato said:**
> Nope its blocked and you know what I read what that site says and I think my ISP is blocking port 80 for me...

I'm positive I know how to set up my router and apache2 to the new port, but can you explain no-ip.com to me?

UPDATE:
actually after running that tool some more I can't find a single port that is open. All respond to either connection refused or timed out... this makes me think that there is a firewall somewhere else... does ubuntu come with a firewall???

OK so with no-ip, they give you a domain name to use and you point your domain at that address. Then they forward it to your machine. You run a little app on your Linux machine that reports when the IP changes so you never lose your site. In your case you will want to redirect your port 80 traffic to another port like 8080 although they might be blocking that one as well, but try it and see. You will have to set Apache to listen on 8080 also. Keep in mind that there will be a fair amount of people who will not be able to see your site because some comapanies restrict access to redirected sites (they can tell).

-Tim

---

### Post by JameoPotato on 2008-05-27
Okay I will use that at a last resort but started checking random ports and what I realized was pretty much this:
port 80 and 21 (FTP and HTTP) both time out.
Port 22 Success
All others "Connection Refused"

I don't really know what to make of that... that seems more like a full firewall than just a couple ISP port blocks.

---

### Post by windependence on 2008-05-27
> **JameoPotato said:**
> Okay I will use that at a last resort but started checking random ports and what I realized was pretty much this:
port 80 and 21 (FTP and HTTP) both time out.
Port 22 Success
All others "Connection Refused"

I don't really know what to make of that... that seems more like a full firewall than just a couple ISP port blocks.

Trust me your ISP is blocking your ports. You can actually call them and ask, and they will tell you which ones. :)

-Tim

---

### Post by JameoPotato on 2008-05-27
Okay, well in that case I do have a backup plan. I have a separate house with a different ISP and I just emailed their customer service asking about web hosting under them. (If they provide static ip's and if they block ports). Depending on their response I will probably just move my serve to the new location. 

I like the other ISP better customer service wise anyway.

Thank you so much for your help though in finding out what the problem was. I think I can consider this SOLVED.

---

