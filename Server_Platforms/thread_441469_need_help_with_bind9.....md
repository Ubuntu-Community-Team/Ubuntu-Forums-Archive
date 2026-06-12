---
title: "need help with bind9...."
date: 2007-05-12
forum: Server Platforms
---

### Post by hockey97 on 2007-05-12
HI I don't fully know how to config bind 9  using webmin to make my own domain name.
I want to know if how do you get a domain name is their any way where I could convert my ip adress to a domain name and broadcast the domain name on the internet?? so when someone types in my domain name in the browser it will search the internet for my server that's has that domain name attach to it where my dsn server would reply and then proccess it to my server.

my router has 4 inputs where it say's dns1 and then dns2 all the way to 4 the input can only be an ip adress I don't know the whole system.

Like how the domain names are visiable to the network or internet.

If I need to buy a domain from an ISP ect then I would rather be my own ISP.

is their way around dealing with the ISP for a domain name?  and can all isp handle domain name
services??

Thanks for your time.

---

### Post by craigp84 on 2007-05-12
Hi Hockey,

> I don't fully know how to config bind 9 using webmin to make my own domain name.

DNS is one of those things that, if you make an **** of it, it gets pretty painful quickly.

If you're going to do your own DNS, take some time out to read up on DNS upfront. There's good documentation comes with bind, but if you prefer books, "DNS and BIND" from O'Reilly is pretty much the definitive text, and worth a read anyway.

Unfortunately there's not many shortcuts with DNS (that don't end up biting you in the long run).

> is their any way where I could convert my ip adress to a domain name

Yes, that's called reverse DNS. You'd most probably set this up during your configuration.

> broadcast the domain name

With DNS you don't so much broadcast, as hang up a sign that others can choose to come read. It's not someone shouting over a megaphone, its more like someone holding up a wee sign.

> so when someone types in my domain name in the browser it will search the internet

It doesn't search the internet, rather it looks up the database you configure to see what the current IP is. This only makes sense if you have a static IP for your server. Otherwise you'd look to something like dyndns.org to sort you out.

> my router has 4 inputs where it say's dns1 and then dns2 all the way to 4 the input can only be an ip adress

Yes, this is the other side of DNS - the resolver. So you can think of DNS as having two parts (actually there's quite a few parts) - a server part, which contains the database that can translate your domain name to an IP address, or sometimes your IP address to a domain name - and there's the client bit.

The client part is the bit that speaks to the server and asks "Hey, i'm looking for [www.mysite.com](www.mysite.com), do you know what IP that's on?".

Those boxes allow you to configure the resolver (the client bit) in the router. These tell the router that when it needs to resolve a domain to an IP, it should speak to these servers.

> If I need to buy a domain from an ISP ect then I would rather be my own ISP.

Hmmm. This is one bit of pain that's really better to give to someone else to look after normally. Save your hair, pay someone else to do your DNS - some registrars will chuck in free DNS hosting when you buy a domain from them.

Hosting your own DNS can sometimes hammer your bandwidth, and that just slows down your internet browsing for no good reason! :-)

> is their way around dealing with the ISP for a domain name? and can all isp handle domain name
services??

Yeah there is, but as above, you probably don't want to do that. Let the professionals with their big servers and plentiful bandwidth handle that.

Hope this helps,

Craig

---

