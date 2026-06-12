---
title: "Ubuntu Server 8.04 Problems"
date: 2008-05-12
forum: Server Platforms
---

### Post by CsmcDem on 2008-05-12
Yesterday I decided to (finally) install Ubuntu Server on one of my old computers. The computer is perfectly capable of running it, as I used to use it as my main computer, and frequently updated it. So yesterday I installed Ubuntu Server 8.04. I followed several guides that I found off of the internet, in order to configure certain options, but it's pretty much the default installation for the web server part of the server. The problem that keeps arising is that I can access the server, in my case my ip @ "24.187.53.132", anywhere in the network, however, when you go out of the network, you cannot access the server.

How can I fix this error?

Thank You in Advanced.

---

### Post by wirelessmonkey on 2008-05-12
Well, if your sever can see other machines on the network, and they can see it, then there is either a firewall blocking outside requests or a routing issue.

---

### Post by CsmcDem on 2008-05-13
Ohh. Thank you. I just read somewhere that my ISP doesn't allow web server hosting, unless you upgrade the package.

Thanks anyways

---

### Post by hyper_ch on 2008-05-13
forget about your ISP... you can host a server anyway (however depending on the usage they might block your inet account) but I see no reason why you should not be able to host a private server...

Well, I assume you are behind a router/modem with your local network, right?

if so, then

(1) give your server a static IP in your lan

(2) router port 80 (and more if you want to use other services than http) from the router to your server('s static IP)

(3) go to [http://www.no-ip.com](http://www.no-ip.com) and sign up for an account

(4) create a subdomain there (e.g. csmcdem.sytes.net or csmcdem.no-ip.com)... there are a couple available for free

(5) check your router, if no-ip is supported (or maybe another dyndns service, if so, use another one)

(6) if it is supported on your router, enter details there

(7) if it's not supported, install the package "noip2"
```

sudo apt-get install noip2

```

(8) during installation you should be asked for yur no-ip.com login details and dynmaic domain... enter those details

(9) it will then update at regular intervals your current IP from your ISP in their database. This means the domain csmcdem.sytes.net or csmcdem.no-ip.com (or whatever you chose) will be routed to your dynamic IP address and hence you can use your computer as webserver.

---

### Post by Thirtysixway on 2008-05-13
Your ISP must be blocking port 80. I believe there are ways to run your server on a different port, but use a no-ip dynamic dns name on port 80, which would let users still access the site.

---

### Post by hyper_ch on 2008-05-14
> **Thirtysixway said:**
> Your ISP must be blocking port 80.
What makes you think so? I just think he doesn't forward port 80 from the router to his server in the lan.

---

### Post by windependence on 2008-05-14
> **hyper_ch said:**
> What makes you think so? I just think he doesn't forward port 80 from the router to his server in the lan.

Either one of you could be correct. He can check this by going to [www.canyouseeme.org](www.canyouseeme.org) and checking the port. It's true, some ISPs do block common server ports like 80 and 25. 

Also, if he has a static IP there is no need for a no-ip account. My ISP only charges me $5 for my static IP.

-Tim

---

### Post by hyper_ch on 2008-05-14
if port 80 is blocked, you can't surf the web ;)

And because he says his ISP says you can't run servers I think he has no static ip... but that's just my assumption - I might be wrong on that.

---

### Post by dmizer on 2008-05-14
also ... even if your provider does prevent inbound port 80, you don't have to run your server on port 80.

---

### Post by windependence on 2008-05-14
> **dmizer said:**
> also ... even if your provider does prevent inbound port 80, you don't have to run your server on port 80.

For sure, but then you would need a redirect like no-ip. I ran mine that way for a while, but many people could not acces the site from work because their networks did not allow a redirect to be browsed to. It's just a pain in the @ss. There are plenty of ISPs that will give you a static IP and not block your ports.

-Tim

---

