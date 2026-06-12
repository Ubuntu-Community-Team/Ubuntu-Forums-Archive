---
title: "Hosting server with virgin media / DNS"
date: 2013-01-21
forum: Server Platforms
---

### Post by dooves on 2013-01-21
Hi,

I really quite new to hosting my own server and have usually used the virtual hosting.

I currently installed my own apache server with ubuntu and am trying to link the the website to my hosted domain name with 1 and 1.

I have read about changing the dns settings within the 1and1 control panel and get this to include the A ip address. the only problem is that the public ip address will be the same for all devices connected. the local 192.x.x.x address are fine and i can connect from another device on my network but unsure on how to access the server computer from outside the network. Ie what would the ip address be.

I have tried to change the static ip address within the virgin media super hub but that only researves for the local network so unsure how i can set this up.

any advise / help welcome

cheers

---

### Post by SeijiSensei on 2013-01-21
Point the A record for [www.yourdomain.name](www.yourdomain.name) to the external IP address of your router.  Use the router's software to forward its port 80 to port 80 on the web server.

Some potential problems:

1) Running a web server on a residential Internet connection may constitute a violation of the Terms of Service.

2) ISPs sometimes enforce that restriction by blocking inbound requests to port 80 on your router.

3) If you have a dynamic IP address that changes routinely, it's difficult to host a web server on that address.  You can fashion kludges with other DNS providers, but you're better off getting a static IP address if possible.

4) Sometimes ISPs charge substantial amounts for "business-class" service that include a static IP. You might be better off renting a virtual machine in the cloud.  I use [Linode]("http://www.linode.com/") as my VM provider.  Paying them $20/month was much cheaper than paying some $120/month to Verizon for a business class connection into my home.

---

### Post by chrisguk on 2013-01-22
I thin it may not have been clear regarding your server hosting configuration:

So the questions I have are:

1.  Are you hosting a dedicated server with an ISP which is located in a data center?

2.  Are you hosting the server at home or a small office?

If you are hosting the server as a dedicated server then the questions you have asked should be easy to resolve.  Firstly it would be easier to transfer the domain to the service provider of the dedicated server.

As SeijiSensei quite rightly pointed out, if this is a home connection I would strongly advise against it.  Not only will you be plagued with performance issues, it is against the terms of normal residential broadband rental.  Data centers are fully equipped with the necessary network infrastructure to handle multiple requests so that would be my option.

Im running 2 Servers at home with a hardware firewall.  My connection is 50Mbits and the servers are HP proliant.  I would never consider hosting from my home.

---

### Post by spynappels on 2013-01-23
If you do have a dynamic Public IP address, you could use a service like DynDNS to give you a "static" URL which will always point to your current Public IP. Most modems/routers have a facility to update DynDNS or similar services with a new IP when it receives it from the ISP. Then instead of pointing the DNS A record to an IP, you could point it to your DynDNS URL/domain name.

It's a bit kludgy, but it works, and you have the advantage that you can use the DynDNS domain name for SSHing to your internal server from outside too if you forward the appropriate ports.

While I would never host a site expecting any serious traffic in-home, for some small web apps etc which will only receive limited traffic, it is a perfectly acceptable solution, as long as it does not contravene your Broadband provider's T&Cs.

For production sites, I also use Linode, like SeijiSensei. Good service at low cost.

---

