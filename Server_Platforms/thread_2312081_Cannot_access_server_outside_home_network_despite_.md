---
title: "Cannot access server outside home network despite having opened ports 80 and 22"
date: 2016-02-01
forum: Server Platforms
---

### Post by kaarthik2 on 2016-02-01
Hi!
I recently setup my server using Ubuntu Server OS and I am successfully able to get to the apache 2 confirmation page within the home network using my internal ip (192.168...). But if I disconnect from my wifi and use my mobile internet and go to that ip (192.168...), I cannot access that page. I tried using my public ip (of the server) to access the page, but that didn't work from within the home server and outside the server. I am able to successfully use FTP within home network (haven't tested outside home). I use shorewall firewall and the ports are opened in that; if I stop shorewall and try to access the page (192.168...), I cannot get to that page even within the home network. I have configured my sever and router to use static ip (different address in both; can't use the one I used for my server for my router as it says that it is invalid) and allowed port 80 and 22 through my Linksys router. Still no luck. Changing the ip to static ip in the router yielded no different result.

Can you guys help me please!

Thank you in advance!

---

### Post by nerdtron on 2016-02-01
Did you configure port forwarding on the router? You should set port forwarding of port 80 and port 22 of the router's public IP to the local IP of the ubuntu server.

---

### Post by kaarthik2 on 2016-02-02
Thank you for the reply. But I don't have an option to enter an IP when allowing port, I am stuck with 192.168.1.(_) for the prefix whereas the public address does not start with that. So I am stuck with forwarding ports to my private IP instead of Public IP. Is there anything I can do?

---

### Post by Chris_McMillan on 2016-02-02
Use the private IP of the server.  Since it's on your home network it should be in the 192.168.1 subnet.  Just forward the ports for its host IP on the router.

---

### Post by kaarthik2 on 2016-02-02
That's exactly what I am doing. For some reason it is not allowing me to access outside the network, and its not just the server, I tried opening ports for my personal PC and I still couldn't access through the port.

---

### Post by nerdtron on 2016-02-02
It's not just a matter of open or closed ports on the firewall section of the router. You'll need to configured the Port forwarding on the router to forward the requests (from public IP) to be forwarded to the ubuntu server (with local IP).

Just for troubleshooting purposes, if your router has a DMZ setting then turn it on and configure to forward everything to the Ubuntu server. This may not be secure but at least you'll have an idea if the forwarding is really functioning correctly.

---

### Post by darkod on 2016-02-03
Lets go back little bit because you posted lots of confusing data...

1. When testing do not use all IPs that come to your mind (router public IP, router private, server private...). The rules are simple: When testing from inside your home network (connected to your router by cable or wifi), use the server private IP. Lets say it is 192.168.1.10. When testing from the internet (your mobile connected to mobile network, work, friends house...) use the router public IP. Note that the public IP can change if it's dynamic.

2. Open the router web interface and forward TCP ports 80 and 22 to 192.168.1.10 (your server private IP). Also check if you need to allow them in the router firewall separately because on some routers you need to do that. Only the forwarding is not enough if the router firewall is blocking those ports. Save the configuration.

3. You say you have shorewall firewall on the server. Why? It is on a private network not accessible from the internet. No one can reach it directly except the ports you forward on the router. And you don't want to block those ports anyway so I don't see a point having a firewall on your server on a private network. I would completely remove shorewall, or at least disable it while you are testing. That way you can know shorewall is not the issue (and it might be!). Even if you want to apply some sort of firewall protection better to use basic iptables than other programs that you might not be familiar with... But that can be discussed later.

4. Once the above is done, first do a test from the home network using your server private IP. Does it open the apache default page or your site (depending how you have it set)??? If that works it shows you the server configuration is OK.

5. Then test from the internet and check if it displays the apache page also.

Let us know how it went and if there were any issues...

---

### Post by kaarthik2 on 2016-02-03
Thank you for the detailed response! I did everything and I can access by apache page from my home network, but not from the outside (like using my phone's data). I did setup static IP address but that is affecting anything. I did try disabling all my firewalls, including my router's firewall (IPv6 and IPv4) but that also didn't affect any thing. This is so frustrating but fun :cry:

---

### Post by matt_symes on 2016-02-03
Hi

There's a useful, independent web tool to verify if your ports are open or not.

[http://canyouseeme.org/](http://canyouseeme.org/)

It'll eliminate your phone being the problem.

You may want to post a screen shot of the port forwarding page on your router so it can be checked.

You can redact any sensitive information from the screen shot before uploading it.

Kind regards

---

### Post by MAFoElffen on 2016-02-04
Or from reading your posts... A few questions:

What is the IP address of your Apache server?

Do you have your gateway forwarding port 80 and ports 22 to that address?

If you go to Google.com, if you type 
```

What is my IP address

```
Is that the publicly seen IP address that you've been trying to use?

Did you confirm that your ISP does not block incoming port 80 to their clients? (one way) Because some ISP's do... That is how they justify selling static, public IP addresses.

---

### Post by darkod on 2016-02-04
So, your apache is configured good because it does work locally.

Next I would do what Matt suggests in his post #9. Visit the canyouseeme.org page from your desktop connected to your home router and check if port 80 is visible. That will confirm if the internet provider is blocking port 80 or not. Also it should confirm if the firewall is blocking it or not...

After you get that result we can talk about options.

---

### Post by matt_symes on 2016-02-04
Hi

> **MAFoElffen said:**
> Did you confirm that your ISP does not block incoming port 80 to their clients? (one way) Because some ISP's do... That is how they justify selling static, public IP addresses.

This is definitely worth checking.

The link i posted above (canyouseeme.org) can be used to verify this if you are convinced port forwarding on your router has been configured correctly.

EDIT:

@darkod. 

I missed your post when i hit the 'reply to thread', and have just repeated what you said.

Kind regards

---

### Post by MAFoElffen on 2016-02-04
+!, or one we use here: [ShieldsUp!]("https://www.grc.com/x/ne.dll?rh1dkyd2")

This one is meant for vulnerability testing, which comes up with a reports of ports seen from the public side of your connection. It is sort of like doing an ss (replacement for netstat) on your connection from the perspective of being on the the outside, looking back in.

---

### Post by kaarthik2 on 2016-02-04
@darkod @MAoElffen @matt_symes It says that the port is still blocked... I used another website where I was able to enter the IP address and then check ports for that address, and that failed too... I am going to check my ISP. I noticed that people who are using my provider that their ports were blocked, so I am planning on using an unofficial port number and then access the link outside my home network

---

### Post by kaarthik2 on 2016-02-04
@MAFoElffen Thank you so much for bringing up the ISP. I didn't know that they would block ports. I will try using unofficial/unlisted ports and then try to access my server through that

---

### Post by kaarthik2 on 2016-02-04
@darkod It says that the port is not opened (both 80 and 22). :( looking on the ISP problem

---

### Post by matt_symes on 2016-02-04
Hi

> **kaarthik2 said:**
> @darkod It says that the port is not opened (both 80 and 22). :( looking on the ISP problem

Please post back if it is your ISP's policy to block these ports. I'd be interested to know.

There's no need to mention the ISP by name though.

Kind regards

---

### Post by darkod on 2016-02-04
OK then... If you still want to try it working without changing ISP, you have two options basically.

1. You can set apache virtual host to work on different port (for example 8080) but in such case you will always need to access your webserver putting the port in the URL, like http://<public IP>:8080

2. If your router supports it, you can leave apache on port 80 and use 8080 in the URL and your port forwarding needs to forward external port 8080 to internal 80. That way apache can stay on 80.

Basically if your ISP is blocking 80 you have to use another port in the URL, so you might as well change it in apache too. That way you don't depend whether your router supports changing ports when forwarding or not.

---

### Post by MAFoElffen on 2016-02-04
For reference, if an ISP does block ports, if an ISP says that they "*block certain ports per industry-standard best practices.*" That translates to that they block at least the following ports:
```

Port  Service
----   --------
25    SMTP
69    TFTP
80    HTTP
135   NetBios
137   NetBios
138   NetBios
139   NetBios
445   Windows File Sharing
1025  Network Blackjack
1434  
2745
3127 to 3198
4899  Ra Admin
5000  uPnP
6129

```
Port 65535 is the maximum definable port. But most say that if you are going to define a non-standard port, then to define it below 49151 ... As the range from 49152 up to 65535 are reserved for Ephemeral ports

Next, if an ISP says that they block all ports, what they mean is they block all incoming traffic initiated from outside their client's IP address, that are not initiated from the client, then bound into the Ephemeral range. (one way traffic for intiations). This is how interactive binding with normal interaction with the internet works. 

Example: Client is on PC #4 in a home & is browsing a website and the connected host updates it's content on that page (GET/POST action), gets back to PC#4 in that local network... through that single publicly seen IP address.

This is also how open-port utilities work to Dynamic DNS Services, Proxy Service Sites, Remote Desktop technical support apps, etc. Initiate a request that opens a port from the client side, which binds that port in the Ephemeral range from that client side... and leave it open to a proxy (tunneled between)... Make sense? Not saying I am telling anyone how to circumvent an ISP's limitations, policies, rules, or terms of service. I'm just explaining how that logically works, right?

---

### Post by matt_symes on 2016-02-04
Hi

Just a minor point.

> As the range from 49152 up to 65535 are reserved for Ephemeral ports

This is the suggested range by ICANN.

Linux uses a slightly different range by default.

```
matthew-xu-16-04:/home/matthew:1 % cat /proc/sys/net/ipv4/ip_local_port_range
32768   60999
matthew-xu-16-04:/home/matthew:1 %
```

These can be changed in Linux by editing sysctl.conf.

The theory is rock solid though.

Kind regards

---

### Post by kaarthik2 on 2016-02-04
@matt_symes @MAFoElffen @darkod It was the ISP! I called my service provider and asked them allow port 80 and 22 for that specific (server) IP address and they did it! Now I am able to access my server using its public IP outside my home network. I cannot thank you all enough for helping me with this! You all took your time to help me and I really don't know how to repay that kindness. If not for you all, I would have stuck with this problem for at least two more weeks. Thank you so much!

---

### Post by matt_symes on 2016-02-04
Hi

> **kaarthik2 said:**
> @matt_symes @MAFoElffen @darkod It was the ISP! I called my service provider and asked them allow port 80 and 22 for that specific (server) IP address and they did it! Now I am able to access my server using its public IP outside my home network. I cannot thank you all enough for helping me with this! You all took your time to help me and I really don't know how to repay that kindness. If not for you all, I would have stuck with this problem for at least two more weeks. Thank you so much!

Excellent :D I'm glad you got it fixed.

The easiest way to thank us is to mark this thread as SOLVED using the thread tools menu just above post #1.

It'll help others looking for a similar solution.

Kind regards

---

