---
title: "IPTables or another process to filter where web requests go"
date: 2009-03-13
forum: Server Platforms
---

### Post by twistedtwig on 2009-03-13
Hi all,

I am not sure if this is possible but I thought I would try and get some advice from people who understand this greater than me.

so let me explain my architecture a little first:

I am in the UK and have Broadband with Sky and they force users to use their custom Netgear modem router.  I can not get the username and password for the net so can not use my dlink modem to get an external IP.  

The sky modem has the relevant ports opened and all forwarded to ubuntu server.

so I have the sky modem, this goes directly into my ubuntu server with a static internal IP set.  my ubuntu server deals with the DNS and DHCP for the network.

From the ubuntu server it goes out into my network and internally I have a windows 2003 server, (so behind my firewall, as well as the netgear router firewall).

the ubuntu server is my main web host (has 3 sites on it).  I also have a couple of sites on my windows 2003 server.  At this moment I have used apache's proxypassreverse to be able to put out the site without putting them onto NON standard ports.  This works fine unless I want to use webservices or things like WCF.  Not sure if its proxypassreverse or windows server, but it all gets upset at this point and the address's get messed up and can not be routed to from the net, (seems to put the local IP into the request rather than the domain name).  The only way I found to get around this was to put the webservice on a separate virtual directory and use a non standard port for the webservice only.  This feels very hacky.

What I would like to do is to have IPTables / or some other application I could setup to filter the traffic.  It would look at the traffic and say stuff for domain X, Y and Z should go to Ubuntu server at local IP 1.1.1.1, and domain A, B and C should go to windows server with local IP 1.2.3.4.

I hope to get some newer hardware in the future and be able to put the windows server into a VM on the main Ubuntu server to reduce the amount of hardware lying around.  Don't know if this would make any difference with the IP address's / network adapters available.

Thanks for any and all advice, I just do not have enough knowledge / understanding of routing and the like to know how or if this is possible.

Jon Hawkins

---

### Post by BkkBonanza on 2009-03-13
I think you could use iptables but I'm not certain if it handles name based routing. I haven't used it for that. I have run across lots of people using nginx as a web server / proxy. It's a lot lower overhead/footprint than apache and pretty easy to setup too. I have Windows running under VirtualBox on Ubuntu and that works very well - also very easy to setup and consolidate your servers. You could have nginx or apache hosting some sites and proxy the remainder to the vm on the same machine (or to the lan too). It all sounds pretty doable to me.

You could also run a gateway like Untangle (or several others around) in a VM on your Ubuntu server and it would give you a nicer interface for managing many useful gateway tools. I'm just trying this out now to get a feel for it.

As an aside - I guess your'e doing this all from you home broadband as a learning exercise and it's great for that. But there are good reasons to use a data center hosted vps or server when you want to run commercial sites. You probably know this. Running a few servers at home will cost more in electricity than just renting 1 or 2 vps accounts at a London data center. I've been there and eventually figured it out. Fun to learn but in practical terms it's easier, cheaper and more reliable to keep your servers in a data center.

---

### Post by twistedtwig on 2009-03-13
Hi BkkBonaza,

I will look at both of those.  Thank you..

Your right the reason I have them at home is to play with the whole OS and see what I can do to learn different things.  I started on opensource stuff but my job used C# so I moved across to Windows programming as well to broaden my knowledge base. 

I am (very slowly) in the process of writing an application that will need to run a number of services that only a full VM slice would be able to do in a hosted environment.  As far as I know that would cost me best part of £100 p/m which is a fair bit more than the enlarged bills at home.  If I can get the site turning a small profit then hopefully it can pay for it self to be put out in a dedicated center for just the reasons you give.

Thanks again.

---

