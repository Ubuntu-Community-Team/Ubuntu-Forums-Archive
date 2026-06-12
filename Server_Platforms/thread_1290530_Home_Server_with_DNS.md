---
title: "Home Server with DNS"
date: 2009-10-13
forum: Server Platforms
---

### Post by master_script_maker on 2009-10-13
Hi everyone. I want to setup a web, ftp, and dns server at my home. I was wondering how to set this up all on one machine, and if I setup a dns server, would I still have to buy a domain name from somewhere. Edit: I will probably be using ubuntu 9.04
Thanks,
Alex

---

### Post by bab1 on 2009-10-13
> **master_script_maker said:**
> Hi everyone. I want to setup a web, ftp, and dns server at my home. I was wondering how to set this up all on one machine, and if I setup a dns server, would I still have to buy a domain name from somewhere. Edit: I will probably be using ubuntu 9.04
Thanks,
Alex

Are you intending the web server to be visible by the public?  If so I would use the DNS services the DNS registrar (i.e. GoDaddy).  

If you are hosting the web server at an IP address supplied by your ISP for home use there are a couple of things to note.  

First you will have to see if TCP/IP port 80 is available.  Sometimes it is blocked by the ISP.  I would also check your usage terms (agreement) with the ISP.  Some do not allow servers unless you have a business plan.

Secondly, if the IP address to the MODEM is served by DHCP (not a static address), you will have to look into dynamic DNS services.

In any case, setting up your own DNS sever for public use is not needed or recommended.

---

### Post by master_script_maker on 2009-10-13
I have a static ip from my provider along with a business plan, and they allow ports 80, 21, 25 ect. I do want the server to be visible to the public, and I would very much like to use my own dns to register a domain for free.

---

### Post by bab1 on 2009-10-13
> **master_script_maker said:**
> I have a static ip from my provider along with a business plan, and they allow ports 80, 21, 25 ect. I do want the server to be visible to the public, and I would very much like to use my own dns to register a domain for free.

There is no free domain name registration that you will end up *"owning"*.  See [_here_]("http://www.google.com/search?q=free+domain+name+dns&btnG=Go!"). You may be able to get a free subdomain name from them though. 

You should at least register your name through [_ICANN_]("http://www.google.com/search?hl=en&q=ICANN+register&aq=f&oq=&aqi=g1"). I would use an accredited registrar.  You can't just pick a name and use it.

Running your own public facing DNS server can have serious security ramifications.  Unless you have a large business with sites and DNS names changing regularly it just isn't worth it.  But if you must then look at [_BIND9_]("http://www.bind9.net/").

In answer to your original question -- Yes you can do it all on one host (machine).  Should you put all the services on one host another question.

Apache, FTP and BIND are all available in the Ubuntu repos.

How to do it is a little more complicated.  Each service (server) is well documented on the internet.  I would install the Ubuntu "server edition" and select all the services you want.  This will install [_LAMP_]("http://en.wikipedia.org/wiki/LAMP_(software_bundle)").  I believe you can also install BIND at that time.

---

### Post by windependence on 2009-10-13
Agree wholeheartedly with bab1. With Domains being about $8 a year, what is the issue? running your own DNS is both painful and unnecessary. You simply point your registar's DNS at your server. Just because you run your own DNS doesn't mean you have any more "ownership" of your domain, and their DNS servers are probably faster to propogate anyway, along with being backed up and on redundant power. For you, it's just one more single point of failure you have to deal with.

-Tim

---

### Post by doas777 on 2009-10-13
> **windependence said:**
> Agree wholeheartedly with bab1. With Domains being about $8 a year, what is the issue? running your own DNS is both painful and unnecessary. You simply point your registar's DNS at your server. Just because you run your own DNS doesn't mean you have any more "ownership" of your domain, and their DNS servers are probably faster to propogate anyway, along with being backed up and on redundant power. For you, it's just one more single point of failure you have to deal with.

-Tim

not to mention that unless an upstream server is configured to get a zone update from you, your name would never be propagated to the public.

---

### Post by louislepperd on 2009-10-14
Actually I want to set up a similar situation to the one above,
and I want to do it because My registrar tries to charge people for them to host dns for you.
So far the only thing Ive had to pay for to set up a website is the domain name. I want to keep it like that.
so.....
How do I:
1:set up a dns server
2:Make louisnz.net point to my ip address

I have all the ports fowarded
I have a Static ip address
I have installed bind9
I have configured the named.conf files and some of the others
I have a reasonable knowledge of how to do things in linux 
but...
So far I have been unable to get this to work :-(

It could be because of that upstream server thing that was mentioned earlyer in the topic.
I have some contacts in my isp(its a local one)
So I may be able to get them to put somthing in their upstream server(if they have one)


Where should I go from here?

Thanks
Louis

---

### Post by louislepperd on 2009-10-14
Oh and I want to get a dns server running for kicks too.(is this an expression that people from other countrys will get?)
(the most important reason)

---

### Post by BkkBonanza on 2009-10-14
There are many free DNS servers on the web. Check out zoneedit.com and dnssolutions.com for starters. There are more. Doing it for kicks, ok. But don't do it because you seriously think there's a reason that makes sense other than learning. 

Running your own DNS server doesn't give you free names. 

And the person above about zone updates is wrong. You will register your DNS server with your registrar anyway which will cause any name requests to upstream zones to resolve correctly to your DNS server. 

I've run DNS servers because I wanted geo-directed control of certain domains - a feature not commonly available for free, but other than education it's a pointless waste of your server resources and a weak spot for failure of your hosted domains. Most decent DNS providers have 4-5 redundant servers and much easier domain controls. And they almost always don't charge for it. If they charged me I would move my domain - which doesn't cost anything if you plan to keep the name another year anyway.

---

### Post by BkkBonanza on 2009-10-14
@louislepperd,

You need to go to your domain registrar and set your name to use your DNS server instead of there's. They will require that you have two seperate IP addresses for redundancy. Once done, they update the global root servers so that any public requests for your name get sent to your IP. If your DNS server IP is down then your name fails to resolve.

Before doing that your need to use tools like dig to check that your DNS server is providing valid and correct dns records. dig is in the package dnsutils in ubuntu repo. It allows setting which specific server IP to query for the testing unlike most other general DNS requests, thus bypassing normal DNS query routing. You can use it locally to test a local DNS server. One thing to note is that if testing locally then often your router may not route your public IP requests back to your local server. For that you can use web-based tools out on the net to check your DNS server. Make sure your DNS server gives good replies before updating your domain registrar.

Regarding zone transfers - the only zone transfers you need to worry about are the ones between your own (two or more) DNS servers. Any other server out there that allowed you to do a zone transfer would be enabling a severe security breach. Likewise your DNS servers can only accept zone transfers from your own servers. Allowing others would enable  name table posioning - a very severe form of attack supporting fraudulent sites/phishing.

---

### Post by windependence on 2009-10-14
> **louislepperd said:**
> Actually I want to set up a similar situation to the one above,
and I want to do it because My registrar tries to charge people for them to host dns for you.
So far the only thing Ive had to pay for to set up a website is the domain name. I want to keep it like that.
so.....
How do I:
1:set up a dns server
2:Make louisnz.net point to my ip address

I have all the ports fowarded
I have a Static ip address
I have installed bind9
I have configured the named.conf files and some of the others
I have a reasonable knowledge of how to do things in linux 
but...
So far I have been unable to get this to work :-(

It could be because of that upstream server thing that was mentioned earlyer in the topic.
I have some contacts in my isp(its a local one)
So I may be able to get them to put somthing in their upstream server(if they have one)


Where should I go from here?

Thanks
Louis

What country are you in? In the states, I use Godaddy and I get the domain for $8 a year complete with a full DNS control panel. Just transfer to someone who gives you that capability. You can still set up your own DNS for your local zone and learn without messing up the web in the process. :-)

-Tim

---

### Post by doas777 on 2009-10-14
> **BkkBonaza said:**
> 
And the person above about zone updates is wrong. You will register your DNS server with your registrar anyway which will cause any name requests to upstream zones to resolve correctly to your DNS server. 


sorry for the confusion.
in the example cited, the op was not using a registrar. we were pointing out that without a registrar, a DNS server would be useless. the registrar either has to point to your dns server and propagate that to other upstream servers, or they need to get a zone transfer from you to propagate. otherwise, you have a server that no one knows about, just sitting there doing nothing, since no one knows how to contact it, or even that it is there.
without an upstream registrar, nothing happens. thats all I was saying.

---

