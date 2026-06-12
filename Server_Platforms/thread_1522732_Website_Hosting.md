---
title: "Website Hosting"
date: 2010-07-02
forum: Server Platforms
---

### Post by crootsam on 2010-07-02
Im looking to start to make my own website, i want to host it from home and will probably use ubuntu to host. Im a novice to both ubuntu and website building and hosting. 
Ive done some research and i think (pls correct me if im wrong)you buy a domain name, register with the DNS, then configure firewalls etc. eventually ending up at the server its hosted on?
What software is good for website building and can Ubuntu host a website? and create one?

---

### Post by amauk on 2010-07-02
bear in mind that hosting a website is (depending on what you're serving, and the traffic you get) extremely bandwidth intensive

if you have 1mbps upstream
and 10 people connect, each person will only be able to download stuff at 100kbps
now, if 100 people connect...

For small stuff with a limited audience, self-hosting a site is fine
but for most things, you'll run out of bandwidth (and then people will get rejections) very quickly

---

### Post by Vegan on 2010-07-02
I get a lot of traffic on my site, but I have compression enabled so its a lot faster then otherwise.

---

### Post by amauk on 2010-07-02
while compression means you (generally) transfer less bits to & fro
it's dependant on the content being served
and it also increases CPU usage

but overall, I think compression is a good thing for webservers

---

### Post by teisho on 2010-07-02
Hosting a website from home is usually a bad idea, and not only because of bandwidth.

In order to connect to your website, visitors need a domain name and an "IP Address".  You can find out what your ip address is by going to sites like

[http://myip.is/](http://myip.is/)

And for a domain name, I would suggest

[https://www.nearlyfreespeech.net/](https://www.nearlyfreespeech.net/)

Once you have a domain name and an ip address, you can start running a server.  But there is a catch:

Your internet service provider ususally gives you a dynamic ip address, so whatever your ip address is, it will probably change on a regular basis.  Every time it changes, you domain name will point to the wrong place for your website.

There are services like dyndns to get around this limitation.

[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

So finally, once you've gone through all of this hassle, and learned to live with your limited bandwidth, there is still one more hurdle.  Most internet service providers have restrictions on you hosting servers in their terms and agreements when you signed up.  So when they notice you're using up lots of bandwidth and find that you're running a webserver, they might cancel your internet connection.

If you want to use Ubuntu to run a webserver, I would suggest not doing it from home.  If you can't afford several hundred dollars a month for a dedicated server, I would suggest a virtual private server (VPS).  You can run a website on Ubuntu for less than $10 a month in most cases.  Check out this list:

[http://xenlightenment.com/tier/128/month](http://xenlightenment.com/tier/128/month) (disclosure: I work for Xenlightenment)

The VPS host will give you an IP address that never changes, and you will have root access to an Ubuntu server with enormous amounts of bandwidth.

It's still a good idea to build and test your website at home, but once you're ready to put it on the internet, use a VPS.

---

### Post by dfreer on 2010-07-02
> **crootsam said:**
> Im looking to start to make my own website, i want to host it from home and will probably use ubuntu to host. Im a novice to both ubuntu and website building and hosting. 
Ive done some research and i think (pls correct me if im wrong)you buy a domain name, register with the DNS, then configure firewalls etc. eventually ending up at the server its hosted on?
What software is good for website building and can Ubuntu host a website? and create one?

I did this for a couple years, I believe there is a How-To guide somewhere on the forums but I'll give you some general ideas of how I ran it.

One important thing before you start, is to realize that hosting your own server is generally against the rules of your ISP and may result in termination of service. Furthermore, some ISP's will actually block incoming TCP port 80 (which is the standard port for webservers). 

First, you'll want to get a website going. You'll probably want to use the web server called Apache, it's the most common server out there besides Microsoft's IIS. Check out some basic guides on how to install Apache on your server, build a webpage, and make sure it works.

You will want to make sure your server has a static IP address on the LAN, that way you can open ports to the IP address and not worry about it changing on you. You normally would require a static IP address for your entire house/router as well, but since most ISP's won't do that for you we can use a service called Dynamic DNS to get around that.

Then, you will want to make sure you can see your server from the internet by opening a port in your firewall. Ubuntu server by default has no firewall but also has no ports open, once you install apache port 80 will be open and listening for web page requests so there should be nothing for you to configure there. 

Your home router will have a firewall though, so you will want to open TCP port 80 to the server's IP. Every router is different, so if you don't know how to forward the ports check out portforwarding.com as they have guides based on the most common router models.

You can then test to see if it's open a number of ways: use canyouseeme.org and it will check if it's open. You can grab your external IP address from whatismyipaddress.com and have a friend browse to [http://**YOURIPADDRESS](http://**YOURIPADDRESS)** and see if they can see it. Or if you have no friends you can use a free web proxy to view it yourself.

Finally, once you know your website is visible to the internet, you'll want to do a couple of things:
(1). Get some sort of domain name so that people can access your site via an easy to remember name instead of a bunch of numbers.
(2). Install a dynamic dns client so that every time your external IP address changes it will update a DNS server so that your website name always points to the correct IP address.

I find the best solution for both of these is dyndns.com. It offers a free client for updating your IP address, and you can either go the cheap route and get a free dynamic dns hostname like yoursite.dyndns.com or you can pay for Custom DNS solution and buy your own domain name like yoursite.com. I use both: my webserver had it's own domain name dfreer.org, and then my family's PC's use the free DNS so that I can VNC into them and not need the IP address to do so. It's like $15 a year for the domain name and $15 for the Custom DNS service.

EDIT: As to people saying that you will not have enough bandwidth, it's mostly true. Most ISP's offer plans that have huge download bandwidth but very little upload, almost all cable internet providers are like this, with rates like 5 mbps down/1mbps up if you are lucky. However, I have Verizon FiOS which has INSANE upload speeds, right now my plan is something like 20 mbps down/15 mbps up.

---

### Post by Intel91 on 2010-07-03
I'm actually working on getting my server setup right now, and I'm almost done. I use godaddy for my name registration. Just install Ubuntu Server, install lamp, install ftpd, you probably want to install ssh as well if you want remote access to it, wake-on-lan is a nice feature too when combine with pm-utils. Like before said, you will need to allow internet access to your server, unless it is directly connected to the modem (not router), easiest thing to do is allow DMZ on your local IP of the server, you can find guides for your specific router I'm sure, I personally use a Linksys with dd-wrt.

Anyways, name registration side of it: Just buy a domain name from godaddy (not affiliated, other than a customer), then go to [http://help.godaddy.com/article/422](http://help.godaddy.com/article/422) and follow the instructions for Domain masking, it will assign a domain name to your server's IP, so people can visit your website at [www.example.com]("http://www.example.com"), and see [www.example.com]("http://www.example.com"). Make sure it is Domain masking you select, otherwise they will go to [www.example.com]("http://www.example.com") and see youripaddress. Its very easy with godaddy, so thats all I can say, they aren't the cheapest though, still $10 flat is cheap enough.

But to be honest, unless you need more than web hosting alone, go with an actual web hosting companies for the reasons listed above. Even if you want to file serve, use a web server with ftp support (all of them, basically). Unless you are running a server that is a gaming server, voip server, VPN server, etc, go with a hosting company.

---

