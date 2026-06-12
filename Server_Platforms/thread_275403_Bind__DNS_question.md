---
title: "Bind / DNS question"
date: 2006-10-11
forum: Server Platforms
---

### Post by paul.maddox on 2006-10-11
Hi,

I have bind installed on a spare server here, what I want to do is make bind return a single IP address (say 10.8.1.1) no matter what the DNS query is.

So any lookup done, would always return that address.

Is this possible?

---

### Post by twistedtwig on 2006-10-11
I no clue how to do it but am curious to why you would want to.  I am new(ish) to bind / ddns extra and just trying to get as much of a feel for it as i can.

thx for sharing :)

Twiggy

---

### Post by paul.maddox on 2006-10-11
I have a little server that our sales guys take on the road with them to show off our LAMP based product.

[IMG]http://static.flickr.com/52/110539071_58abdd4abc.jpg[/IMG]

The server has a DHCP (dhcpd) and DNS (bind) server installed so that when you plug a cross-over cable from laptop to the mini server, it assigns their Windows laptop an IP address and if they browse to [http://www.example.com](http://www.example.com) then the DNS server redirects [www.example.com](www.example.com) to itself.

However, I want to configure it so that any web address the sales guys enter, it always loads up our demo site. 

What I need is a kind of default entry that bind will return if the address is not found in it's configuration.

---

### Post by twistedtwig on 2006-10-11
OH i see :) thanks and good luck

dont suppose you can use wild cards in bind.. or have forwarders in the firewall maybe that forward everything to that ip?

just guessing really.

Twiggy

---

