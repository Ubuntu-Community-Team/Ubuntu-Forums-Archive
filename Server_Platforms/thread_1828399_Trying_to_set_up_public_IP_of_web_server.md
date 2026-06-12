---
title: "Trying to set up public IP of web server"
date: 2011-08-18
forum: Server Platforms
---

### Post by Zonglars on 2011-08-18
We have a spare computer and decided to turn it into a web server that we could use to access files away from home (and of course as a test server for web development).

I've installed Ubuntu Server 11.04, installed the LAMP stuff along with OpenSSH and Shorewall, and can log into it from my macbook via HTTP, SFTP and SSH. The problem is, I'm only able to access it currently via the IP address 192.168.1.4, which I know is limited to the computers on the network. We're using a NetGear router, and I've logged into it to setup the WAN settings, making that IP address the default DMZ server, and checked "Respond to Ping on Internet Port". After that I'm totally lost as to how I find the public IP. I installed lynx and browsed to whatismyip.com and it gave me the address of the router (216 something or other). When I visit it on my macbook, it takes me back to the router login.

What settings am I missing? Also, while I'm at it, is there any additional work required to allow a domain to be pointed to this server when I make it public?

Any help would be appreciated.

---

### Post by Dangertux on 2011-08-18
This is completely normal. This happens with most SOHO routers because of the way they route. 

There is a term that is running around that is semi official called NAT Loop Back. You might want to look into it.

In short though basically what is happening is this. 

You have your public interface (WAN) [216.xxx.xxx.xxx] then you have your internal interface (LAN)[192.168.0.xxx] because of the way the server for your router listens 0.0.0.0:* (if you were looking at netstat). It's listening on ALL interfaces, so if you get a request from the internal network to (WAN) it's going to route it to the INTERNAL server (because it's more logical per the router's default routing tables)

Try accessing it from an external system (phone, computer elsewhere, proxy) and you will find it will probably work just fine.

If you want a workaround add an entry that looks something like this to your /etc/hosts file

192.168.0.5           mydomain.com

where 192.168.0.5 is the internal IP of the server and mydomain.com is your domain name.

---

### Post by wojox on 2011-08-18
Just set up Port Forwarding on your router for 192.168.1.4

HTTP 80
HTTPS 443

---

### Post by Zonglars on 2011-08-19
> **Dangertux said:**
> This is completely normal. This happens with most SOHO routers because of the way they route. 

There is a term that is running around that is semi official called NAT Loop Back. You might want to look into it.

In short though basically what is happening is this. 

You have your public interface (WAN) [216.xxx.xxx.xxx] then you have your internal interface (LAN)[192.168.0.xxx] because of the way the server for your router listens 0.0.0.0:* (if you were looking at netstat). It's listening on ALL interfaces, so if you get a request from the internal network to (WAN) it's going to route it to the INTERNAL server (because it's more logical per the router's default routing tables)

Try accessing it from an external system (phone, computer elsewhere, proxy) and you will find it will probably work just fine.

If you want a workaround add an entry that looks something like this to your /etc/hosts file

192.168.0.5           mydomain.com

where 192.168.0.5 is the internal IP of the server and mydomain.com is your domain name.

You're right, it works fine accessing through my android. Now to google into tying it to one of my domain names. Thanks!

---

### Post by Zonglars on 2011-08-19
Sorry, I've got most of it working, and edited the hosts file on my macbook so it'll connect to the LAN address when I visit the domain. However, what about when I'm not on the LAN and want to connect? Is there a way to program a fallback; if it can't connect to the 192 ip it should go for the 216? Or should I have 2 separate subdomains? like a home.mydomain.com and a [www.mydomain.com?](www.mydomain.com?) I know how I can do the latter, but I'm wondering if there's a way to build a check right into the system so it's easier for family to access it the same way wether on the network or not.

---

### Post by e79 on 2011-08-19
Just adding my 0.02$.

The easiest way to achieve what you want would be to set up a [DNS server for your local network]("https://help.ubuntu.com/community/BIND9ServerHowto"). So when asking for yourdomain.com your request would be forwarded to the internal IP address of your server, and when being out of your home the other DNS servers on the web would route you to your external IP address (and then your router would forward the request to your server).Obviously this would imply that you have an external DNS server resolving your domain name to your external IP address.

Hope this helps

---

### Post by Zonglars on 2011-08-19
> **e79 said:**
> Just adding my 0.02$.

The easiest way to achieve what you want would be to set up a [DNS server for your local network]("https://help.ubuntu.com/community/BIND9ServerHowto"). So when asking for yourdomain.com your request would be forwarded to the internal IP address of your server, and when being out of your home the other DNS servers on the web would route you to your external IP address (and then your router would forward the request to your server).Obviously this would imply that you have an external DNS server resolving your domain name to your external IP address.

Hope this helps
Okay, I think I'm following you; I set up a DNS for the computers on the network to go through, which will redirect the requests for the server's website to the local IP address, in essence acting as if all the computers had the hosts file edited to go to that IP address rather than the public one.

I'm gonna dig through that article and see if I better understand it. Thanks!

---

### Post by e79 on 2011-08-19
You got it :popcorn: 

Setting up Bind9 is a pretty straightforward and simple process, once it done, effectively point all your local machines to use this DNS server and voila !

Don't hesitate if you have more questions !

Cheers

---

### Post by Zonglars on 2011-08-19
> **e79 said:**
> You got it :popcorn: 

Setting up Bind9 is a pretty straightforward and simple process, once it done, effectively point all your local machines to use this DNS server and voila !

Don't hesitate if you have more questions !

Cheers

Well, it's set up, and I've found the name servers the router uses. So which configuration should I use? I get the feeling a primary DNS would be what I need, but I'm not sure.

---

### Post by e79 on 2011-08-19
The way I would do it is :

- Create a Primary forward DNS zone responsible for yourdomain.com on your Bind9 DNS server
- Add the IP address of your router as a 'forwarder' for your Bind9 installation (when your internal DNS service cannot resolve a domain name, it will forward the query to your router) 
- Have all your local machine use this internal Bind9 DNS server as their primary
- Have your router use the external DNS for forwarded queries.

The communications from 'outside' your LAN are already handled by public DNS server anyway, which should point to your external IP address (216...).

If it can help, let me provide you with some configuration file examples :

**named.conf.local  file (to declare your master zones) :**
```

zone "yourdomain.com" {
        type master;
        file "/etc/bind/db.yourdomain.com";
        forwarders {8.8.8.8;};
        allow-transfer{"none";};
};

```**db.yourdomain.com  file (the actual zone file) :**
```

; yourdomain.com
$TTL    604800
@       IN      SOA     ns1.yourdomain.com. root.yourdomain.com. (
                       14022011 ; Serial
                           604800 ; Refresh
                             86400 ; Retry
                          2419200 ; Expire
                            604800); Negative Cache TTL
;
@      IN      NS      ns1
         IN      MX     10 mail
         IN      A       192.168.22.7
ns1    IN      A       192.168.22.7
mail   IN      A       192.168.22.6
www  IN      A       192.168.22.5

```(sorry if this one looks messy, I was not able to align everything properly once posted).

---

### Post by Zonglars on 2011-08-19
> **e79 said:**
> The way I would do it is :

- Create a Primary forward DNS zone responsible for yourdomain.com on your Bind9 DNS server
- Add the IP address of your router as a 'forwarder' for your Bind9 installation (when your internal DNS service cannot resolve a domain name, it will forward the query to your router) 
- Have all your local machine use this internal Bind9 DNS server as their primary
- Have your router use the external DNS for forwarded queries.

The communications from 'outside' your LAN are already handled by public DNS server anyway, which should point to your external IP address (216...).

If it can help, let me provide you with some configuration file examples :

**named.conf.local  file (to declare your master zones) :**
```

zone "yourdomain.com" {
        type master;
        file "/etc/bind/db.yourdomain.com";
        forwarders {8.8.8.8;};
        allow-transfer{"none";};
};

```**db.yourdomain.com  file (the actual zone file) :**
```

; yourdomain.com
$TTL    604800
@       IN      SOA     ns1.yourdomain.com. root.yourdomain.com. (
                       14022011 ; Serial
                           604800 ; Refresh
                             86400 ; Retry
                          2419200 ; Expire
                            604800); Negative Cache TTL
;
@      IN      NS      ns1
         IN      MX     10 mail
         IN      A       192.168.22.7
ns1    IN      A       192.168.22.7
mail   IN      A       192.168.22.6
www  IN      A       192.168.22.5

```(sorry if this one looks messy, I was not able to align everything properly once posted).

Okay, so 192.168.22.x is the LAN IP of the server, correct? I've set those to 192.168.1.4 (the local IP of the server) I didn't bother with the mail settings, since I'm not using this domain for mail.

However, I'm a bit confused about how I can have this intercept the computers on the network, if I need to add them or if it can dynamically redirect any computer connected.

---

### Post by e79 on 2011-08-19
Yes the LAN ip of your server should be 192.168.1.4 in your case; simply replace the appropriate values.

In order for your other computers to use this DNS server, simply configure it manually in your network cards using the network manager (as shown on the screenshot - again, change values according to yours).

It would also be a good idea to create Host Record for all your computers as well and have them all look/search (and be part of) for 'yourdomain.com'. This way, when trying to access one of these machine (for whatever reasons), you could simply type the Hostname instead of the IP address. This is how I usually set my LANs.

So lets say you have 3 machine in your LAN (server included); you could then set up your zone file like :

```

; yourdomain.com
$TTL    604800
@       IN      SOA     ns1.yourdomain.com. root.yourdomain.com. (
            14022011 ; Serial
                        604800 ; Refresh
                        86400 ; Retry
                        2419200 ; Expire
                        604800); Negative Cache TTL
;
@      IN      NS      ns1
       IN      A       192.168.1.4
ns1    IN      A       192.168.1.4
www    IN      A       192.168.1.4
pc1    IN    A    192.168.1.10
pc2    IN    A    192.168.1.11

```

---

### Post by e79 on 2011-08-19
unwanted duplicate post

---

### Post by Zonglars on 2011-08-19
> **e79 said:**
> Yes the LAN ip of your server should be 192.168.1.4 in your case; simply replace the appropriate values.

In order for your other computers to use this DNS server, simply configure it manually in your network cards using the network manager (as shown on the screenshot - again, change values according to yours).

It would also be a good idea to create Host Record for all your computers as well and have them all look/search (and be part of) for 'yourdomain.com'. This way, when trying to access one of these machine (for whatever reasons), you could simply type the Hostname instead of the IP address. This is how I usually set my LANs.

So lets say you have 3 machine in your LAN (server included); you could then set up your zone file like :

```

; yourdomain.com
$TTL    604800
@       IN      SOA     ns1.yourdomain.com. root.yourdomain.com. (
            14022011 ; Serial
                        604800 ; Refresh
                        86400 ; Retry
                        2419200 ; Expire
                        604800); Negative Cache TTL
;
@      IN      NS      ns1
       IN      A       192.168.1.4
ns1    IN      A       192.168.1.4
www    IN      A       192.168.1.4
pc1    IN    A    192.168.1.10
pc2    IN    A    192.168.1.11

```

Ah, okay, good thing I figured out how to set up reserved IP addresses for the computers. I'll try this out and see what happens. Thanks!

---

### Post by jramshu on 2011-08-19
You may want to consider, if you haven't already, setting the server with a static ip address. That way if you loose power to the router it doesn't assign it a different address.

---

### Post by e79 on 2011-08-19
> **Zonglars said:**
> Ah, okay, good thing I figured out how to set up reserved IP addresses for the computers. I'll try this out and see what happens. Thanks!

My pleasure !  Tell us how it goes :D

---

### Post by e79 on 2011-08-19
> **jramshu said:**
> You may want to consider, if you haven't already, setting the server with a static ip address. That way if you loose power to the router it doesn't assign it a different address.

That was obviously implied ;)

---

### Post by jramshu on 2011-08-19
> **e79 said:**
> That was obviously implied ;)

My bad.;)

---

### Post by Zonglars on 2011-08-19
> **e79 said:**
> That was obviously implied ;)

And I think I've taken care of that. I've added address reservations in the router configuration for the server and all the computers in the house. However, I just finished running a needed update on the router, and noticed the public IP has changed. I'm not sure how or if it's possible to set a static IP for the router itself. Plus, now I can't seem to access the public IP; it just hangs. If I specify the port number I set for remote management of the router, it's fine, but it can't seem to resolve like it use to, on both my macbook and my android.

Obviously the router's working otherwise I couldn't post this. Odd...

---

### Post by e79 on 2011-08-19
If I understood correctly, you simply do not have an External Static IP but rather a Dynamic one, that can change at anytime.

What I would suggest is to use a registrar (free or not) for your domain name, that is offering 'Dynamic DNS' service, so whenever your external IP would change, the records at the DNS level would be updated as well (public ones). So this way typing 'www.yourdomain.com' would always forward to your IP address whatever it might be.

Here are examples of companies offering Dynamic Dns services :

[http://freedns.afraid.org/](http://freedns.afraid.org/)

[http://www.no-ip.com/services/managed_dns/plus_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/plus_dynamic_dns.html)

---

### Post by Zonglars on 2011-08-19
> **e79 said:**
> If I understood correctly, you simply do not have an External Static IP but rather a Dynamic one, that can change at anytime.

What I would suggest is to use a registrar (free or not) for your domain name, that is offering 'Dynamic DNS' service, so whenever your external IP would change, the records at the DNS level would be updated as well (public ones). So this way typing 'www.yourdomain.com' would always forward to your IP address whatever it might be.

Here are examples of companies offering Dynamic Dns services :

[http://freedns.afraid.org/](http://freedns.afraid.org/)

[http://www.no-ip.com/services/managed_dns/plus_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/plus_dynamic_dns.html)

Had a feeling that was the case. And the router does have a setup for connecting to a DDNS service. However, the damn thing will only let me use DynDNS (well, 3322 and oray as well, but I don't feel like learning chinese). Still, 30/yr is fairly cheap all things considered. I'll look into what's involved in setting that up and see if it helps.

Ooh, wait, they've got a free version. That should do the trick.

Thanks.

---

### Post by e79 on 2011-08-19
> However, the damn thing will only let me use DynDNS (well, 3322 and oray as well, but I don't feel like learning chinese).Well yeah, basic commercial routers are somewhat restrictive....that's why I'm using a home built firewall (damn old pc + [PFsense]("http://www.pfsense.org/index.php")) ;) It is SO more flexible.

Bonne chance dans tes aventures !

---

### Post by Zonglars on 2011-08-20
> **e79 said:**
> Well yeah, basic commercial routers are somewhat restrictive....that's why I'm using a home built firewall (damn old pc + [PFsense]("http://www.pfsense.org/index.php")) ;) It is SO more flexible.

Bonne chance dans tes aventures !

Still baffled as to why the public IP worked before but didn't after upgrading the firmware. However, I decided to give the port forwarding a shot (easily manageable in the router manager) and it seemed to work without a hitch; no worrying about the public vs. local IP. I didn't want to go with it originally because I wanted to rely on the server's firewall, not the routers, but hell I just updated the damn thing so it should be fine.

It'll do, this things honestly just going to be a dressed up file sharing server for accessing stuff outside the house and easily sending stuff to friends.

Merci beaucoup!

---

### Post by e79 on 2011-08-20
> **Zonglars said:**
> Still baffled as to why the public IP worked before but didn't after upgrading the firmware. However, I decided to give the port forwarding a shot (easily manageable in the router manager) and it seemed to work without a hitch; no worrying about the public vs. local IP. I didn't want to go with it originally because I wanted to rely on the server's firewall, not the routers, but hell I just updated the damn thing so it should be fine.

It'll do, this things honestly just going to be a dressed up file sharing server for accessing stuff outside the house and easily sending stuff to friends.

Merci beaucoup!

Of course port forwarding is a requirement here if you want to reach your server from outside (if not, what good for a firewall would be ;) ).

But again, to reach it from outside you would need to know either your IP address at that time or the domain name, which doesn't change. And considering you do seem to have a Dynamic IP, it is more likely that it will change again so without a service like Dynamic DNS, you would have problem accessing your files from outside once it happens, unless someone at your home can check the router or whatismyip.org.

In any way you seem resourceful so I'm sure your project will be a success !

Cheers

e79

---

### Post by Zonglars on 2011-08-20
> **e79 said:**
> Of course port forwarding is a requirement here if you want to reach your server from outside (if not, what good for a firewall would be ;) ).

But again, to reach it from outside you would need to know either your IP address at that time or the domain name, which doesn't change. And considering you do seem to have a Dynamic IP, it is more likely that it will change again so without a service like Dynamic DNS, you would have problem accessing your files from outside once it happens, unless someone at your home can check the router or whatismyip.org.

In any way you seem resourceful so I'm sure your project will be a success !

Cheers

e79

Thanks. I've got it set up with DynDNS so that should do the trick, otherwise I could look into seeing about making a cron job that checks what it's public IP is, compares it to the database, and notifies me if it's changed so I can edit the A record. But I'm hoping the DDNS setup I did with the router will more or less take care of that.

Wait and see I guess.

---

### Post by e79 on 2011-08-20
Yeah if set up properly and working, nothing to worry and no need to create such script...though I must admit it still could be handy and a nice little side project :P

> Thanks.

Again, my pleasure and if you have more issues or questions, don't hesitate as the community is here for that !

---

