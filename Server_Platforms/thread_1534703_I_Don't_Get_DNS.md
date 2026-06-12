---
title: "I Don't Get DNS"
date: 2010-07-19
forum: Server Platforms
---

### Post by Carleas on 2010-07-19
As will become clear, I'm new at this.  I apologize in advance.

So, I'm migrating a site from one VPS to another, and I'm having trouble understanding what I need to do with DNS.  I haven't even gotten to the nitty-gritty of it: I don't understand it at a very high level.  My host sent me this email explaining what I need to do, and I don't even know what questions to ask.
> Your registrar has MyHost's
nameservers listed for your domain name.

All DNS-related info for mysite.com and everything inside
that zone is defined in your zone file which is currently on your
VPS "myserver1" and is being rsynced to [our] servers.

I'm suggesting that if you don't want to spend any of your migration
time setting up a DNS server then you may wish to just make the
changes in that file, since that is the method that is currently
working.

I've come up with two possible interpretations of this situation, and perhaps neither is correct.
[LIST=1]
[*]I need to set my new VPS to be its own nameserver, and have my registrar point mysite.com to my VPS.
[*]I need to set up a DNS server to somehow interact with MyHost's nameservers (something about a zone file).
[/LIST]
Do either/both of these sound plausible?  I thought DNS made a server into a nameserver, is that not right?  I would ask my host, but I've exhausted his patients for me not knowing what the hell I'm talking about.

---

### Post by CharlesA on 2010-07-19
DNS only deal with converting domain names to IP addresses.

Did the IP address of the server change? If it did, you would probably have to contact whoever you registered the domain with and tell them to update DNS to point to the new IP address.

I don't know what exactly they were talking about changing data in a zone, but I suppose that would apply if you are running a DNS server on the VPS.

From what I understand, normally the company hosting the VPS would update their DNS name servers with the new IP address and you wouldn't really need to do anything. I could be wrong since I've not run a VPS before.

---

### Post by S.R on 2010-07-20
Don't you have to go to your admin panel to configure your zone file?

---

### Post by ov3rcl0ck on 2010-07-20
probably just have to reconfigure what Nameserver's you're using. You'll just have to modify your DNS records to point at your new nameserver/s.

---

### Post by Carleas on 2010-07-21
I got some more information, but I still need help decoding it.  My question:> To clarify, this is what I understand you to be saying:
-At the end of the migration process, my registrar will use my new server as the primary DNS, and your servers as secondaries.
-Along the way, I can use the MyHost nameservers while I'm setting up my own DNS server.
And my host's response:
> No, that wasn't what I was saying. :(

Clearly you're going to have to change the content of your zone file at some point during this migration since the IP addresses of your services are going to change. The way you currently control your zone content is through a file on "server1" which MyHost rsyncs from you.

This method of getting your zone content to MyHost is deprecated. I would prefer if you set up a nameserver on your new VPS for
MyHost's nameservers to do transfers from.

Separately, you have old nameservers set with your registrar and in
your zone file. They work, but should be updated.

The [change] that I'm talking about is
setting up a nameserver instead of BitFolk rsyncing your zone file.
I don't understand this, because I don't really understand DNS.  Why would I need to set up a nameserver just to transfer data to a nameserver?  What's the difference between that and rsyncing?

What I think I understand is the part about MyHost getting new namerservers, that makes sense (**CharlesA** was right here).  And editing the zone file kind of makes sense (I'm found it at /etc/bind/zones/mysite.com.db).  It seems that, to change from one server to the next, I edit the old zone file, it gets loaded to the nameserver, and the nameserver directs traffic to the new server.

Then I think I need to make my new VPS a nameserver to somehow get the same information to the old nameserver, but I don't understand how or why.

**S.R**, I don't have an admin panel.  I could probably install one, but I haven't looked into it.

**ov3rcl0ck**, don't I also have to update that information with my registrar?

---

### Post by tomh0665 on 2010-07-21
> **Carleas said:**
> 

So, I'm migrating a site from one VPS to another, and I'm having trouble understanding what I need to do with DNS.  I haven't even gotten to the nitty-gritty of it: I don't understand it at a very high level.  My host sent me this email explaining what I need to do, and I don't even know what questions to ask.

I've come up with two possible interpretations of this situation, and perhaps neither is correct.
[LIST=1]
[*]I need to set my new VPS to be its own nameserver, and have my registrar point mysite.com to my VPS.
[*]I need to set up a DNS server to somehow interact with MyHost's nameservers (something about a zone file).
[/LIST]
Do either/both of these sound plausible?  I thought DNS made a server into a nameserver, is that not right?  I would ask my host, but I've exhausted his patients for me not knowing what the hell I'm talking about.

I'll give you an example of a hosting move that I've just done.

A friend bought a domain through Network Solutions two years and asked for my help. I logged in to NetSol with his credentials and created an A record (the basic DNS record that associates "domain.com" with "1.2.3.4") pointing at the ip address that the hosting service that he had chosen had given him and an MX record (the Mail eXchange record that sets the mail server for a domain) pointing at Gmail.

He has decided to move to a new hosting service so I've again logged on to his NetSol account and changed his A record to point at his new hosting service's assigned ip address.

So, what you have to do is log in to whatever service is controlling your DNS settings and change the A record (and any other, as needed) to point to your new VPS.

If you can't remember what your authoritative DNS servers are, run "dig @8.8.8.8 your.domain.com -t ns" to find out.

"8.8.8.8" is google's primary public DNS server. If you prefer, you can replace it by one of your ISP's DNS servers or another public one like OpenDNS (primary 208.67.222.222).

---

### Post by Carleas on 2010-07-23
Thanks **tomh0665**, I appreciate your help.

What do I need to do if I'm going to be shutting down my old server shortly after I make the move?  What do I need to do on my new server so that the changes I make on my old server stay true after it's shut down?  Or will they persist unchanged until I set up a new method on my new VPS?

As I understand it, I currently control the zone file for my DNS servers, and it is rsynced to them every 15 minutes.  After the move, I'll need to make a DNS server on my VPS, but it seems like the sole purpose of that server would be to do essentially the same thing the rsyncing is doing now.  Is that something that happens in DNS?  One nameserver telling another nameserver about its domain names?

---

