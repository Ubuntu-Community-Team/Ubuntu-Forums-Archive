---
title: "Local Name Server For Local Sites"
date: 2007-03-10
forum: Server Platforms
---

### Post by kramerkeller on 2007-03-10
Hi, have a home server where I host some of my websites.  It all works fine, including virtual hosting from outside the network.

However, on my home network I can't resolve the address.  I have been trying to set up a local name server.  On my ubuntu machine I think it works because I can go to mysite.com in links and it there it is.  I am trying to access mysite.com through other local machines though.

I have a router pointing to my linux box and pointing to a wireless router.  I am fine with the idea of making by linux box into a router if that is easier, but my main goal is just to access mysite.com without typing an ip on the local network.

Please help.  Would it be a lot easier if my router was the ubuntu box?

---

### Post by thornomad on 2007-03-10
I think you could also tag the IP address to the website address in your /etc/hosts file (I think that is it) on your local machines.  But I am no expert.

---

### Post by Mr. C. on 2007-03-10
You have two options:

1) Add entries in /etc/hosts for all systems on each system
2) Configure a local DNS server to provide your private IPs to all clients, then configure your clients to use your own DNS server.

The first is easy, but you have to copy the files to all systems, and when guests connect to your network, they will not be able to access this systems by name (unless you update their hosts table too)

The second is not terribly difficult, but requires knowing a little about DNS and its zone files.  The benefit here is that you can configure your DHCP server on your router to handout your DNS server, so that when guests connect to your network, they have name-access to all machines.

MrC

---

### Post by kramerkeller on 2007-03-10
I would like to do option two.  I have a router, but I am not sure how to this part that you mentioned

> The benefit here is that you can configure your DHCP server on your router to handout your DNS server, so that when guests connect to your network, they have name-access to all machines.

Should I make my ubuntu box into a rounter adding a card and assigning IP's or is there a way for my box to communicate to my current router the DNS server?

My guess would be I would have to use my ubuntu box.

What would you suggest?

---

### Post by kramerkeller on 2007-03-10
One more note.  I noticed my linksys router will allow me to type in the name of two DNS servers.  I would like to use my ISP's name servers for outside address and my own DNS for local addresses, I guess I could point my router to my local machine for the DNS and maybe somehow use my box to dns for local and call the other name servers for all otehr requests.  Again though it sounds like it might be easier to make my box intou the router.

Let me know what you think.

---

### Post by Mr. C. on 2007-03-10
The only configuration change you will make to your router is to change the DNS server listed.  Everything else occurs on your server.

Make the distinction in your mind between DNS and a Router.  One translates names <-> IPs, the other forwards packets from one network to another.  They perform different functions completely.  For the task at hand, there are not routing issues or changes.

The way you describe how you want to do DNS is possible - you have to setup your DNS server to respond authoritatively for your Zones, and act as a forwarder for all other requests.   What is the reason why you desire this type of configuration?

The two IP address both should be to either the inside, or outside.  The second entry is a fallback position should the first DNS server not respond.  Don't think of this as a second DNS server that gets equally used.

It sounds like you are just starting to learn about DNS.  Have a review of week 8 and 9: DNS I and DNS II at : [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php) .  Also look at the labs, which are designed to walk someone through the process of configuring DNS.  They were written for another distribution, but the concepts are the same.

MrC

---

### Post by kramerkeller on 2007-03-10
Currently I am virtual hosting 3 sites.  I use zone edit for my name server and it send the appropriate cnames etc to my router.  My router in turn forwards http, ftp, and ssh requests to my linux box.

So I have an name server I am happy with and it works fine externally.  However, on my internal network I would like to set up a local name server to resolve addresses locally.  createcandor.com works externally, but not internally.

I know I wasn't very clear about anything I was saying in my last message becaseu I am new to this, but I have read up a bit.  Can I set up a local dns that only resolves names given locally to the static ip address my linux box is on?  I have read this is possible.  What I don't understand though is how to let all the local machines know to use the local dns server to resolve the names.  I can edit the host files, but then I have to do it on each machine and when I move my notebook it screws it up.

I think I have to somehow use DHCP to tell the local machines what they are using for the local names server.  I want them to access the local name server that has a list of local names to resolve to the linux box, but then for all other names like google.com etc, I would like them to of course use a real name server because I am not up for that.

I hope I make more sence and thank you for the help.

---

### Post by Mr. C. on 2007-03-11
Let's tackle the easiest part first, setting up the other system to use your internal DNS.

Two options: DHCP or static configuration.  You pick the method that is convenient for you.  Here's how you get the best of both worlds.  Some LAN systems require having a static IP (like a IP network printer, a file server).  Many of today's routers allow their DHCP server to assign static-leases to known MAC addresses; thus, you can get both DHCP assigned netmask, DNS servers, as well as dynamic IPs for guests and new systems.  So again, its DHCP or static configuration, or some combination of the two.

For an internal DNS server, let's make sure you understand a key point.  Only one name server is used, until either an answer is given, or a timeout occurs.  If there was a timeout (15 seconds), the next name server down the list in /etc/resolv.conf is tried.  And finally a third name server might be tried if the second one failed.   So, this should indicate that you need your name server to respond to ALL requests.

There are several simple configurations of a DNS server.  A caching only name server obtains its information in the usual fashion, maintains a cache of lookups for fast response, but has no zone files of its own.  In other words, it recursively resolves names and caches the data.

Another minimal configuration is a server that is authoritative for one or more zones, and for all other queries, the usual lookup methods occur.  It too keeps a cache of lookup data for rapid response, and *always* is authoritative for its zones (thus overriding similar names externally, allowing for your private IPs).  This is likely what you want

Other variants allow you to forward queries, see different views depending on IP address ranges, etc.  However, for your needs, there really is no reason to use anything more complex than configuring two zone files for your domain names, the reverse zone files, and a zone file for localhost.  With this, you get the addresses you want for internal lookups, and all other lookups will be done for you.

Spend some time reviewing week 8 and 9 "DNS I" and "DNS II" notes and lab work at:

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php) 

MrC

---

