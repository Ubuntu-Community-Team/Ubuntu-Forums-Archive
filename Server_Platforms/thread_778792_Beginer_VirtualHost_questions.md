---
title: "Beginer VirtualHost questions"
date: 2008-05-02
forum: Server Platforms
---

### Post by RWells on 2008-05-02
I am an absolute beginner, I just learned to spell compuder yesterday.
I am trying to set up a server strictly for the purpose of learning about running a server and developing and testing websites.


I want to use a virtual host to allow another person access for website dev/testing.

What  I have so far is 
1 ip, cable modem, with normal ports blocked by isp
Ubuntu 8.04 server with lamp and gui ( I know I know)
I have managed to get 2 virtual hosts working
"http://site1"
"http://site2"

Now for my questions
Assuming I don't want to register  domain names, can I access these two sites from the web?

Assuming I do want to register 2 domain names,
how do point these to 2 different sites with 1 ip?
Say I use godaddy or one of the dynamic dns services, what do actually need to change, a record, cname ?
And what do I need to tell it, 127.0.0.1, site1 or what?


Rusty

---

### Post by ghostknife on 2008-05-03
> **RWells said:**
> 
Assuming I don't want to register  domain names, can I access these two sites from the web?
No, if you don't register domains you won't be able to access the hosts from the web. Dynamic DNS hostnames should be sufficient though. They usually give you a domain like **your-chosen-name.dyndns.info**

You WILL be able to access the site via your IP address though, but only one of them as you won't have a name to distinguish between the 2 virtual hosts. Using IP you will get the default one of the two (usually the first one, or one specifically marked as a default virtual host).

> **RWells said:**
> Assuming I do want to register 2 domain names,
how do point these to 2 different sites with 1 ip?

When you register the domains you need to tell the registrar which DNS servers to use. Usually the company you register through provides this for you. Via the DNS you specify which server hosts these web sites. You do this by providing the IP address of the server. If it's a static IP you can give them your static IP address. If it's a dynamic IP you can setup a dynamic DNS host, and use a CNAME record on these DNS server to point to the dynamic DNS host.

> **RWells said:**
> Say I use godaddy or one of the dynamic dns services, what do actually need to change, a record, cname ?

See above. With a static IP, make an "A" record pointing to your IP. 
For a dynamic IP, make a CNAME to the dynamic DNS record. These A records would be made on the DNS server you use when registering a domain.

If you only use dynamic DNS, you can simply create two separate dynamic DNS host names for your one machine, and then use them directly inside your virtual host configuration. This would work in itself.

If you want nice names though, like [www.yourname.com](www.yourname.com), you need to register it and do the A/CNAME records on the DNS server as described above.

Confused? Feel free to ask. I remember what it feels like to get lost when you're new to these things, so there are no stupid questions, ever.

---

### Post by RWells on 2008-05-03
ghostknife, 
Thanks, I think you answered my questions.

The reason I asked is because of the isp blocking port 80.
I have two domain names registered and parked at go daddy.
When I use a 301 redirect to 00.000.000.000:8080, I only get the default site
However if I dont add the port number to the redirect url ,and type it in myself in the browser I get the host.

Same thing using DynDns.
Will creating A records for my ip fix this?

Rusty

---

### Post by ghostknife on 2008-05-04
Creating A records for your IP will make the people connect directly to your IP. If your ISP is blocking port 80 though, they will get nothing because they will try to connect to port 80.

If they type: [http://www.yourhost.com/](http://www.yourhost.com/) they will attempt to connect to port 80 of whatever the A record for [www.yourhost.com](www.yourhost.com) points to.

They will need to type: [http://www.yourhost.com:8080/](http://www.yourhost.com:8080/) to connect to your port 8080.

I recommend getting an ISP that doesn't block port 80. Or hosting [www.yourhost.com](www.yourhost.com) somewhere else, pointing to the A record to that host's IP, and storing a file that redirects to your DynDNS host port 8080.

---

