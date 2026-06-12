---
title: "Virtual hosting with single domain name"
date: 2012-02-21
forum: Server Platforms
---

### Post by time4e on 2012-02-21
Hello,
  I am currently running three virtual machines (virtual box) all three are running Ubuntnu server 10.04 each hosting different webpages with apache2 and I have one domain name registered. Lets say [www.example.com]("http://www.example.com"). I want to be able to access each webserver over http by using the name of the server for example [www.webserver1.example.com]("http://www.webserver1.example.com/") or [www.webserver2.example.com]("http://www.webserver2.example.com/"). What would be the best way to go about this.
   
  Thanks,
  -Tim

---

### Post by volkswagner on 2012-02-22
If I understand your question, you would like to run multiple web servers with one public ip address.

First you will want to get name based virtual hosting working with Apache2.  The sticky at the top of this forum has the how to listed under HTTP servers.  Pick one of your VM's to be the "main" apache server. 

Set up your DNS to point to your main server.  Get at least two virtual host's working. 

Once you get that working you will want to setup reverse proxy. This will allow your router to forward all web requests to main server, then main server will "forward" the request to external apache server when other subdomains are requested.

I created a simple how to for proxy.
ubuntuforums.org/showthread.php?t=1920715

---

### Post by idef1x on 2012-02-22
Why not put all 3 servers on one apache server and use virtual hosts?? If that is the only taskt the 3 servers are doing, it would save some resources too when combining them

---

### Post by HugoSerrano on 2012-02-22
Yep, you can use all three site in the same machine.

But there's some times when we need to have some different machines, for different reasons.

You need to configure VirtualHosts as a proxy for the others servers.


[http://httpd.apache.org/docs/2.0/vhosts/examples.html#proxy](http://httpd.apache.org/docs/2.0/vhosts/examples.html#proxy)

---

### Post by a2j on 2012-02-22
I have similar setup. Multiple VPS, multiple sites per VPS. Single IP, multiple (sub)domain names. Look into pound. [http://www.apsis.ch/pound]("http://www.apsis.ch/pound")

I have dedicated VPS that runs pound to handle all http requests.

---

### Post by time4e on 2012-02-25
Thank you all so much for your reply. This is something I am dabbling at  for work to see if we could provide VPS to some of our clients, which  is the main reason they would have to be separate vm instances.  volkswagner and HugoSerrano I will try out both of your recommendations and let everyone know how it works out. 

Thanks again everybody,
-Tim

---

### Post by SeijiSensei on 2012-02-25
> **time4e said:**
> Hello,
  I am currently running three virtual machines (virtual box) all three are running Ubuntnu server 10.04 each hosting different webpages with apache2 and I have one domain name registered. Lets say [www.example.com]("http://www.example.com"). I want to be able to access each webserver over http by using the name of the server for example [www.webserver1.example.com]("http://www.webserver1.example.com/") or [www.webserver2.example.com]("http://www.webserver2.example.com/"). What would be the best way to go about this.

If you have control over the DNS for example.com, and the servers have separate fixed IP addresses, you only need to change the DNS records for the domain:

```

@   IN SOA example.com. root.example.com. (
       [stuff]
       )

[more stuff]

www.webserver1     IN    A   ip.of.webserver.1
www.webserver2     IN    A   ip.of.webserver.2

```

If the webservers are configured to serve requests as [www.webserver1.example.com](www.webserver1.example.com) and [www.webserver2.example.com](www.webserver2.example.com), that should be all you need.

---

### Post by time4e on 2012-02-25
SeijiSensei,
I am using no-ip.com to manage my dns for the domain, do I need to configure the dns record on no-ip's control panel or can i edit it on the vm that i have the dns updater for no-ip?

---

### Post by SeijiSensei on 2012-02-25
I don't know.  I run my own DNS servers.  The entries have to be publicly visible however you configure it.  

I'd actually create an A record for server.example.com and a CNAME for [www.server.example.com](www.server.example.com).  In Apache, you can designate server.example.com as the ServerName and [www.server.example.com](www.server.example.com) as the ServerAlias.  Then you can advertise server.example.com, but still accept requests from people who think all web sites begin with "www".

---

### Post by time4e on 2012-03-06
All,
Thanks again for the replies, but I have been at this for a month now with no results. Again I have multiple webservers behind one domain name/ip address. My domain lookup is provided by no-ip.com, I have setup two Apache web servers server1 and server2. I would like my external users to be able to access there appropriate web server buy typing server1.example.com or server2.example.com in a web browser. Pound seems like it would be great if I was hosting mutiple websites on one webserver but this is not my case. I need some solution that would enable me to port forward 80 to a server and have that server redirect to the requested server or a better dns solution. any more ideas? Perhaps pound could do this? can't find any decent docs on it. Setting up cnames in my noip control panel works but only internally. Any ideas, tips, tricks for me? 

Thanks,
-Tim

---

### Post by volkswagner on 2012-03-06
From your post I can't tell if your issue is DNS or getting more than one web server on port 80.

Do you have two domains available from no-ip?  Are they both resolving to your home ip address?  If the answer to both the above are yes, then you should be able to use reverse proxy on the machine that has port 80 forwarded from your router.

It is confusing to me because you are using a subdomain scenario in your post.  I did not think no-ip had this feature.

---

### Post by idef1x on 2012-03-08
> **time4e said:**
> All,
Thanks again for the replies, but I have been at this for a month now with no results. Again I have multiple webservers behind one domain name/ip address. My domain lookup is provided by no-ip.com, I have setup two Apache web servers server1 and server2. I would like my external users to be able to access there appropriate web server buy typing server1.example.com or server2.example.com in a web browser. Pound seems like it would be great if I was hosting mutiple websites on one webserver but this is not my case. I need some solution that would enable me to port forward 80 to a server and have that server redirect to the requested server or a better dns solution. any more ideas? Perhaps pound could do this? can't find any decent docs on it. Setting up cnames in my noip control panel works but only internally. Any ideas, tips, tricks for me? 

Thanks,
-Tim

1) Setup your DNS to point server1.example.com and server2.example.com to the public ip address
2) setup an apache webserver or so where you will direct all webtraffic to (port 80)
3) configure this webserver to do reverse proxy for server1.example.com and server2.example.com (see apache documentation about reverse proxy)
4) configure your server1.example.com and server2.example.com on their machines

done.

NB: you can also use one of the server1.example.com or server2.example.com webservers to work as reversed proxy as described in point 2 and 3, but the above example might make it more clear how it is going to work...

---

### Post by time4e on 2012-03-10
I have decided that the using no-ip is just making this much harder than it hast to be. I have decided to setup my own dns server using webmin on freebsd 9. Hopfully I will be able to setup the VMs in the configuration I want. If anyone has any helpful links or advise that would be create, since this is my first DNS server. I will post back in a few days with my progress.

---

