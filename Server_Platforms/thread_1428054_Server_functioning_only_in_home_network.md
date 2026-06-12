---
title: "Server functioning only in home network"
date: 2010-03-12
forum: Server Platforms
---

### Post by eyehavenoi on 2010-03-12
I set up an old machine with Ubuntu 9.10 (Desktop Edition) but I am using it as a server.

I am using apache2 - from what I've gathered on my own, it seems I should be able to load my html and files into /var/www, then they should be accessible on-line through the ip address of that machine. The server is hooked up to my router through a wireless pci card.

I have been able to access my site from my laptop (also wireless) but I tried it from work today, and it timed out.

I'm guessing there might be complications since I have it set up through a router?

I'm have a domain name set up through DynDNS.com. There's a box on the site for "Your current IP address", and it gives a different IP than the ones I've been using.

I've been using 192.168.x.x
DynDNS recognizes 64.252.xxx.x

Very nebulous for me, I'm learning as I go.
Would appreciate some clarification.
Thank you

---

### Post by Ryan Dwyer on 2010-03-12
192.168.x.x is a private address and cannot be accessed from outside your network. The 64.252.x.x address is your external address and should be used to access your server (or just use the domain name).

Using the external address will only get as far as your router. You need to configure your router to forward port 80 to your server. Make sure your server's private address is static (ie. it won't change after a reboot).

---

### Post by eyehavenoi on 2010-03-12
> **Ryan Dwyer said:**
> 192.168.x.x is a private address and cannot be accessed from outside your network. The 64.252.x.x address is your external address and should be used to access your server (or just use the domain name).

Using the external address will only get as far as your router. You need to configure your router to forward port 80 to your server. Make sure your server's private address is static (ie. it won't change after a reboot).
Awesome, I'll look into this soon.

So I should link my domain name with the 64.252.x.x of my server, and the rest of the configuration will be done by editing my router settings?

---

### Post by spynappels on 2010-03-12
Yes, that is correct.

What make and model of a router do you have? If you can give that info, we may be able to help with the port forwarding too, but key for this is to have the server on a static LAN IP.

---

### Post by eyehavenoi on 2010-03-12
Motorola Netopia 3000, Model #3347-02

In researching this, I almost scrapped the project because I thought I needed a static IP. Then I remember coming across something that said I could still set up a server with a dynamic IP. Will I have to update the address every day or something along those lines?

It'd probably be more cost-efficient to buy some hosting space than to get a static IP from AT&T, right?

---

### Post by eyehavenoi on 2010-03-12
- (double)

---

### Post by Ryan Dwyer on 2010-03-12
Most routers have an option for DynDNS. You enter your DynDNS username/password into the router and it updates automatically. If your router doesn't have that option, you can install the ddclient package which does the same thing.

Follow the instructions on this page to set up port forwarding. It's not the same model router as what you have but it should be very similar: [http://portforward.com/english/routers/port_forwarding/Netopia/2247-02/Apache.htm](http://portforward.com/english/routers/port_forwarding/Netopia/2247-02/Apache.htm)

---

### Post by eyehavenoi on 2010-03-12
I edited my router options for default NAT server - I pointed it to the internal IP of my server (192.168.x.x), then changed my server IP on DynDNS to the 64.148.x.x address, and I can access my site from my laptop!

Was it really that simple or am I being fooled because I am still requesting the page from within my home network? Before changing the NAT settings from my router I had tried to access my server's 64.148.x.x address and it would not load - now it works fine. I'll have to try it from a friend's computer though.

As I said before I'm just running this from a home internet connection (my ISP is AT&T). Is my server address going to change?

---

### Post by FuturePilot on 2010-03-12
> **eyehavenoi said:**
> 
Was it really that simple or am I being fooled because I am still requesting the page from within my home network? 

No, it really was that simple. :)
Most likely though you're on a dynamic IP so occasionally it will get changed. You can set up something like ddclient on the server so that it will automatically update DynDNS with the new IP address when that happens. Most routers also have a built-in utility to do this.

---

### Post by eyehavenoi on 2010-03-13
I just a had a friend try my site and he got a "server not found" error.
The server IP is still the same. And I can still get the site to come up from my home network.

Do I have to allow permission for outside access or something along those lines?

---

### Post by zander1013 on 2010-03-13
> **eyehavenoi said:**
> I just a had a friend try my site and he got a "server not found" error.
The server IP is still the same. And I can still get the site to come up from my home network.

Do I have to allow permission for outside access or something along those lines?

hi,

i have mine setup with a port forward. if you can add a port forward to the firewall in you router it might work.

set "source ip"=all, "public port"=1234 (choose anything between 1024 and 65535), "private port"=80, "private ip"=ip of your server. the ip of my server is issued from dhcp. and it seems to work okay. it seems to keep that address continuously even when the lease is renewed or the machine is reboot. but i am trying to changes that to a static ip in my networks private static range.

then you should be able to reach you server with http://<externalip>:1234

the link where this was explained to me is here [http://ubuntuforums.org/showthread.php?t=1426199](http://ubuntuforums.org/showthread.php?t=1426199)

here is a working example where it is reaching my new wireless server [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) but my router/firewall has a static ip from my isp. it is an extra $5/month.

---

### Post by eyehavenoi on 2010-03-13
> **Ryan Dwyer said:**
> Most routers have an option for DynDNS. You enter your DynDNS username/password into the router and it updates automatically. If your router doesn't have that option, you can install the ddclient package which does the same thing.

Follow the instructions on this page to set up port forwarding. It's not the same model router as what you have but it should be very similar: [http://portforward.com/english/routers/port_forwarding/Netopia/2247-02/Apache.htm](http://portforward.com/english/routers/port_forwarding/Netopia/2247-02/Apache.htm)
I tried this guide, but was unable to make a port for 80, said it was already in use.



> **zander1013 said:**
> hi,

i have mine setup with a port forward. if you can add a port forward to the firewall in you router it might work.

set "source ip"=all, "public port"=1234 (choose anything between 1024 and 65535), "private port"=80, "private ip"=ip of your server. the ip of my server is issued from dhcp. and it seems to work okay. it seems to keep that address continuously even when the lease is renewed or the machine is reboot. but i am trying to changes that to a static ip in my networks private static range.

then you should be able to reach you server with http://<externalip>:1234

the link where this was explained to me is here [http://ubuntuforums.org/showthread.php?t=1426199](http://ubuntuforums.org/showthread.php?t=1426199)

here is a working example where it is reaching my new wireless server [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) but my router/firewall has a static ip from my isp. it is an extra $5/month.

I just attempted a [guide from the Motorola website]("http://www.netopia.com/support/hardware/technotes/CQG_025.html") that seemed to address exactly my situation, which I was surprised about. Seemed similar to what you described.

As I posted earlier, I was getting the site the site through my laptop hooked up to my local network when my friend could not. Hence I can't really test if I got all the settings worked out right. If someone could let me know if they can get to my site [illumetank.shacknet.nu]("http://illumetank.shacknet.nu") - that'd be awesome.

Appreciate all the input

---

### Post by Ryan Dwyer on 2010-03-13
It doesn't work. illumetank.shacknet.nu resolves to 64.148.0.90. Please go to [www.whatismyip.com](www.whatismyip.com) and confirm that is your IP address. If it is indeed your IP, then your router isn't port forwarding.

It might also be worth logging into your ISP's website and looking around for port settings. I know some ISPs require you to enable it in their interface.

---

### Post by eyehavenoi on 2010-03-13
My IP address got updated, I'm going to have to get ddclient. But for now, I think I got the port forwarding set up okay. I combined these two guides:

[http://www.netopia.com/support/hardware/technotes/CQG_025.html](http://www.netopia.com/support/hardware/technotes/CQG_025.html)
[http://portforward.com/english/routers/port_forwarding/Netopia/2247-02/Apache.htm](http://portforward.com/english/routers/port_forwarding/Netopia/2247-02/Apache.htm)

Changed my internal server to 8080, added pinholes for port 80 and 443 to my server's local ip.

Someone want to give it a shot again? [illumetank.shacknet.nu]("http://illumetank.shacknet.nu")

---

### Post by Ryan Dwyer on 2010-03-13
That works.

---

### Post by eyehavenoi on 2010-03-14
Really? Thank you very much, everyone!

---

### Post by Kiwi76 on 2010-03-15
It doesn't work for me. It times out.

Also, why are you using port 8080? You shouldn't have to bother with that. AT&T doesn't block port 80 (at least, it doesn't for me, but I'm also using U-Verse which essentially has a static IP address).

---

