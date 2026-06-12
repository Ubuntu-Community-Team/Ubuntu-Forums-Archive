---
title: "Authoritative Only Server"
date: 2009-01-28
forum: Server Platforms
---

### Post by Marmidon on 2009-01-28
Hi guys,
I'm trying to set up Bind so that I can host my own web site from home.
I'll be hosting it on my desktop which is connected to a router. The only other computer connected to the network is my wife's work laptop (and the odd person who stays and want's to get online).
The router dishes out the IP addresses on the internal network automatically (DHCP?) and the one assigned to my desktop appears to remain the same.
Now, I want all computers on the local network to use my ISP's DNS servers but for anyone externally (wanting to view my web site) to use my DNS server. I think this means that I will be a non-caching server or an authoritative only server? Is this right?
I've had a stab at setting up the zones using the various guides available but one thing keeps confusing me namely which IP addresses should I be putting in the zone files?
My ISP has assigned me an address of 82.16.184.xxx
My routers address is 192.168.2.1
My desktop is addressed 192.168.2.4
Subnet mask is 255.255.255.0
and then there's our old friend 127.0.0.1

I always think that if two people have the same router (Belkin) as me then their internal addresses will be the same as me and therefore the domain name for my web site can't be mapped to this. But then I think that if the IP address allocated from my ISP is mapped to the domain name how will my router know when to send the queries when they come in?

If you could clear any of this up for me I'd be eternally grateful.

P.s. I have done a whole lot more in terms of registering a domain name and countless hours of research so if you ask me something I do stand a chance of being able to give you an answer!

Thanks.

---

### Post by gombadi on 2009-01-28
> 
but for anyone externally (wanting to view my web site) to use my DNS server


When you setup a domain you have to set two DNS servers that will handle requests for that domain.

You adsl connection is one but what is the other?

> 
but one thing keeps confusing me namely which IP addresses should I be putting in the zone files


Your ISP's ip address as that is the only one that the rest of the world will be able to connect to. 127.0.0.1 and 192.168.x.x will not work for the rest of the world.

I take it the ip address from your ISP is static. If not then it will not work.

Have you considered using a dns company? It would make life a lot easier.
[http://www.dyndns.com/](http://www.dyndns.com/) or [http://www.easydns.com/](http://www.easydns.com/) for example.

---

### Post by windependence on 2009-01-28
You don't even need BIND to host your own site. Use the nameservers from your Domain Registrar (where you registered the domain). There should be an option in your domain control panel for DNS.

-Tim

---

### Post by Marmidon on 2009-01-28
Cheers for the replies guys.
Gombadi, when I registered the domain I changed the nameservers to ns1.mydomain.co.uk and ns2.mydomain.co.uk.
In the same control panel I've set @, ns1.mydomain.co.uk and www 'A' records to my external IP address (the one assigned my IPS).
As you can imagine, ns1 and ns2 both point to my external IP address and so I'm not really covering myself should the primary go down although I thought this wasn't a problem, just not conventional. I have set up an account with xname.org for my secondary server but I don't want to go into all that just yet, I'd sooner get sorted at my end first before going down that road (unless I have to).

My IP address is not 'static' as such but it is sticky and I'm informed it only changes when my mac address changes. To me that's static enough!!

Tim and gombadi - I'm aware of the hosting options offered by third parties but I'd really like to have total control and besides, I'm too far in with this to give it over to someone else. It's mad but between moments of uncontrolled sobbing and kicking the cat I quite like what I'm learning about bind and DNS!!!!

---

### Post by windependence on 2009-01-29
I am sure you misunderstood me. I am NOT saying anything about a hosting provider. This is done from your DOMAIN REGISTRAR'S control panel, you know, the people who you bought your domain from. They almost always have nameservers you can use to point your 'A' records at your server. Running your own authoritative name server is expensive (because you need two) and dangerous, because you can piss off a lot of people if you misconfigure a DNS server. It's certainly not necessary. I host quite a few domains for customers and all of them use Godaddy's nameservers. I see hundreds of these threads here but it's like pounding my head against the wall because of the "perfect server" tutorial telling everyone they need a DNS server to run a web site. They don't.

-Tim

---

### Post by hyper_ch on 2009-01-29
it is recommended to have two dns servers in different subnets. However it is not mandatory.

---

### Post by Marmidon on 2009-01-29
OK Tim, I dont want to be pissing people off with some ill configured DNS server so lets say I use the registrars nameservers. I'm assuming that I change the nameservers back from what I nominated them to the ones supplied by the registrar? Then what? Is it then a case of using something like Apache or are there certain aspects of Bind that still need to be implemented? 
Any advice or threads regarding this would be appreciated.

Cheers hyper_ch, at least something is as I thought!

---

### Post by spynappels on 2009-01-29
To host the site, you just need to install Apache, and maybe PHP and MySQL, depending on how complicated and interactive you want the site to be.

wrt your DNS, you need to point it to your "static" external IP, and enable port forwarding on your router to forward all port 80 traffic to the local IP assigned to your server. It would be better to assign the computer acting as your server a static local IP to avoid issues with changing local IPs.

---

