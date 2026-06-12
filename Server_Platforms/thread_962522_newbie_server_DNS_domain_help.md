---
title: "newbie server DNS domain help"
date: 2008-10-29
forum: Server Platforms
---

### Post by adept_king on 2008-10-29
I am confused about DNS and Bind.  I dont know if a Domain Name Server is a company out there like Godaddy.com

If I make a Domain Name Server myself, on my own computer, do I still need Godaddy or whatever those kind of companies are called?

I am totally confused over namehosts, hosts, domain, domain name servers, bind, all that stuff.

it all seems so redundant.  also, much of this stuff i am told i need to get a server to work isnt included on ubuntu server.

It is amazingly confusing trying to understand why i need to do this or that.  its so easy comparatively to sign onto a wireless network.

why is it so much harder to just walk up to the roadside on the world wide web and set up shop?  how can i get a unique ip for my computer, stuff like that.

I have been doing nothing but reading my eyes off about this stuff, and its nice to read about DARPA, but unless your link is simple and to the point, i could otherwise google for these phonebook sized manuals myself.  what i'm looking for is some kind of insight.

I am a mess.  Please help.

Thanks.

---

### Post by baudday on 2008-10-29
What are you trying to accomplish with your server?

---

### Post by adept_king on 2008-10-29
install a web server on that computer and configure router to
allow inbound traffic on the webservers port.

-problem is, i dont have a router of my own, i am using somebody elses wireless.

Then install a dns server on that computer and set up your computer to
serve dns queries for some domain. This will also require some router
support. ( you may have to buy one for this step, they are like $15 )

-serve queries? some domain?  router support?

Then install a email server and receive email destined for that domain.
Again, router support.

---

### Post by redmk2 on 2008-10-29
> I am confused about DNS and Bind. I dont know if a Domain Name Server is a company out there like Godaddy.com


DNS (Domain Name Services) is a protocol for maintaining a unique list of networks by their domain name ie; yahoo.com or arcade.com

BIND is a server process that interacts with the users request to resolve the domain name to an IP address of specific computer (host).  

> If I make a Domain Name Server myself, on my own computer, do I still need Godaddy or whatever those kind of companies are called?

Yes.  Godaddy is a registrar for the Internet Assigned Number Authority (IANA) See: [http://www.answers.com/topic/internet-assigned-numbers-authority]("http://www.answers.com/topic/internet-assigned-numbers-authority")
You can deal directly if you  like.  Godaddy is a broker, a go between of sorts.

This does not stop you from having a DNS server at all.  But you do need a registered IANNA name for the public internet.

> I am totally confused over namehosts, hosts, domain, domain name servers, bind, all that stuff.

it all seems so redundant. also, much of this stuff i am told i need to get a server to work isnt included on ubuntu server.

Everything has a name and a function.  The term hosts=hardware and a operating system (Ubuntu) -- a domain=your network -- bind=domain name server Note: a domain name server is NOT referred to as DNS.  DNS is a service not a server```
DNS=Domain Name Service
BIND DNS Server=A process on the computer listening for a request from a client
```

The Ubuntu "server" is the OS with some, but not all server apps pre-installed.  Not all users configure the installation the same way.  I have Ubuntu "server" OS installed for use as a file server.  I have no need to run BIND.  My DNS needs are provided by another host (computer).

> why is it so much harder to just walk up to the roadside on the world wide web and set up shop? how can i get a unique ip for my computer, stuff like that.

The underlying technology is complex.  You get the IP from your ISP and the name from Godaddy.  If you have a small network you do not need to even run a DNS server.  I believe Godaddy will provide DNS hosting or you can check with the your ISP.

---

### Post by cariboo on 2008-10-29
You're going to have pretty hard time using the ip address of someone elses router to serve web pages.

You also have to portforward from your computer to port 80 on the router. For what you are trying to do you don't need a dns server. I would suggest using something like noip.com or dyndns to setup things, this are free services, as your friends router probably gets an ip address via dhcp, so the ip address changes from time to time.

One other thing to test is to open port 80 on the router and then go to [canyouseeme]("http://www.canyouseeme.org/")
 to see if the isp is blocking port 80.

---

### Post by adept_king on 2008-10-30
thanks red, for clearing some things up for me.  i was confusing dns server with dns.  domain name service server... oKAY!


also, thanks cariboo.  the canyouseeme.org link is very telling.  yeah, i did the dyndns.org thing and got stuck after that.  i figure, if i can get hacked (say, if i give away my root password online,) it must be just as easy for people to see my apache page if i pray to the right voodoo gods.

my theory is that if i can get hacked, i can reverse hack myself and show a webpage from my apache2.

do i need bind to do that?  if so, or if not, how would one go about serving a webpage based on my computer itself, as a unique device on the net?  is there software that can talk to the "man" so to speak?  to talk to the great sorter of unique ip's in the sky?

---

