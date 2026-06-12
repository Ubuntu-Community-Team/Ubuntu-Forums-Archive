---
title: "Running applications behind OpenSSh server"
date: 2014-11-14
forum: Server Platforms
---

### Post by shane30 on 2014-11-14
Hi all.

I'll confess I'm very new to using Linux so please bear with me when that becomes obvious.

I currently have a number of Linux servers running applications - a mixture of Ubuntu and CentOS.  These applications are generally webapps that are accessed by our staff via naked internet connections - we expose the service through our firewall, and staff connect using external IPs and port numbers, then log in with their own credentials.  A couple of examples are instances of Jenkins and Redmine that we host here in our office.

I've set up an OpenSSH server on an Ubuntu machine which is running and which I am able to use as a proxy using Putty, for my outbound internet connections.

What I want is to make it compulsory for anyone connecting to various applications/machines to connect via this SSH server, i.e have one dedicated entry point to our internal network so that nobody can connect simply using an IP address, but rather having to login first to the SSH server, and then be able to access these internally hosted apps.

Seems like it should be very do-able but I have been unable to find a plain language explanation for what I need to do.  I'm not looking for specific detail of what needs to be done on one machine or another, but rather what needs to be done in principle across the board.  If I know this, then I'm confident I will be able to figure out the detail.

Any advice would be greatly appreciated.

---

### Post by slickymaster on 2014-11-14
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Jonathan L on 2014-11-14
Hi Shane30

You might consider using OpenVPN to build a virtual private network: users' laptops connect and build an encrypted tunnel, either with passwords or certificates.  You expose only one port, and once set up is pretty much invisible to the users.

Any use?  Ask if you need more detail.

Kind regards,
Jonathan.

---

### Post by shane30 on 2014-11-14
Hi [COLOR=#000000]Jonathan,

Thanks for the reply.

We have considered OpenVPN and it is definitely an option, but we were thinking of trying an SSH tunnel as a quicker/easier hacky solution.  One concern for us is our staff that work on client sites (mainly large banks) and a concern that they probably won't be able to access another company's VPN from those sites.

I'm also pretty unclear on how this all looks in the end anyway - if someone logs into the VPN server, can they then browse as per normal within the internal network, say use a web browser to open apps etc?  

Anyway I appreciate the response and it's definitely another option I am looking at.[/COLOR]

---

### Post by TheFu on 2014-11-14
Jonathan is correct. OpenVPN is the better, more seemless solution to this issue.
Banks will not all ssh outbound from their networks either and ssh has much more overhead than openvpn over UDP.  Actually, I suspect neither will work, since banks should be smarter than to allow any external traffic that doesn't go though a proxy server with DPI that drops all unapproved traffic.

So - the only hope of using an encrypted tunnel from inside a client network (of any non-trivial sort) is to use openvpn with tcp going to port 443 on your interface.  UDP outbound traffic should be blocked by any real corporate network security team.  Outbound DNS should be blocked too - at least from client subnets and those subnets shouldn't ahve any route to the internet either.

BTW - openvpn works fine over cellular data networks and there is a redmine android app that works fairly well.

---

### Post by shane30 on 2014-11-14
Thanks, TheFu.  Sounds like that's going to be a much better way to go then.  I suspect you're right that we are going to struggle to get anything that will work from our customers' sites anyway, which is probably going to be a major sticking point.  Thanks both for the responses, I'll do some more experimenting.

---

### Post by Jonathan L on 2014-11-17
Hi Shane30

I quite agree with Fu about what's likely to be blocked in your clients' environments -- certainly lots of networks I've made would prevent these things -- and abusing well-known port numbers may well be the only thing that works.  Do nonetheless consider discussing your requirements with their security people, and review their terms and conditions: you might find yourself in breach of contract for circumventing their network policies (or even just trying to), and in some organisations that actually will get your contract terminated.

And also wanted to be clear that what you're suggesting is a good idea: adding a security machine in front of the application machines gives you all kinds of opportunities to see what's going on and make it more secure.  And that helps the clients.  Getting that a cross to client security teams is a very variable business though.  My experience of security specialists is that about 75% like to go strictly by rulebooks, 20% are flexible and pragmatic, maybe 5% see it as their job to help you do yours, but more securely.

Just to answer original question about what it looks like once done: the  laptops appear to have a new network interface, which has a route to  your application servers.  So you see additional things in the laptop's  routing table.  In fact, of course, as there's no hardware, the outgoing  packet is wrapped up, encrypted, and sent out of the existing  ethernet/wifi/whatever.

An alternative to consider if your applications are (or can be made to be) all web-based is putting a reverse proxy in front of them, which typically deals with the HTTPS connection and forwards it as plain HTTP to the application servers.  (For example [Nginx]("http://en.wikipedia.org/wiki/Nginx"))  If you went down this road deployment is trivial to the laptops, no client which allows web access could ever complain, and you'd be likely to achieve some organisational benefits because the tools can be more coordinated.  You'd have to look at your list of apps to get a feel for how practical this would be to achieve.

On the other end of this equation: if you're designing a corporate network, do remember to put in a "liberty LAN" for your clients and suppliers, so they can work in the way that suits them best.

Hope that's of some use.  Do let us know how you progress.

Kind regards,
Jonathan.

---

