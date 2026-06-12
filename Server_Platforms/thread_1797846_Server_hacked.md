---
title: "Server hacked?"
date: 2011-07-05
forum: Server Platforms
---

### Post by garfonzo on 2011-07-05
Hey folks:

I have a web server for a business running in my garage. There is a second web server in another geographical location running the exact website as a backup. Should the main server go down, I have DNS failover protection so that traffic is automatically routed to the second server. 

Last night the main server went down for about an hour. I don't know why yet, but in my investigating, I was looking at the access.log for the server. I found an entry which comes from a strange source. When I tried to do some domain name lookup, I received no results. 

So, I tried simply entering the domain name in a web browser. To my, shock, **my website showed up!** Then I realised that the domain name is the address of my backup server's IP address, followed by some other stuff. 

For example, if my backup web server's IP is: 123.456.789.123
This odd domain is: 123-456-789-123-astatic416-dsl.ucc-net.ca

I can go to the site, browse through as per normal. I am using the DNS Made Easy service and wondering if this is simply a cached version of the site, server by DNS Made easy and somehow this is related to the main server going down? I'm also wondering if someone has copied my site and is hosting it themselves. 

I'm kind of worried since there is a link on my site for people to pay invoices. This link, however, does take them to a different website which handles that transaction securely (I don't process any credits cards).

Any thoughts?

---

### Post by e79 on 2011-07-05
`123-456-789-123-astatic416-dsl.ucc-net.ca` is simply the FQDN of the modem at your remote location (where the backup server is). What you saw in your logs are attempts to get from your remote location to your main location (garage I assume). Are both server replicating things, like is the backup server is synching with your main server maybe ?

> I'm also wondering if someone has copied my site and is hosting it themselves

well unless your ISP DNS are being hacked, I would`t worry too much about that because if they are safe typing  [www.yourdomainname.com](www.yourdomainname.com) should always froward the queries to your own IP addresses (main or backup).

my $0.02

Hope this help.

---

### Post by Lloyd_mcse on 2011-07-05
> **garfonzo said:**
> Hey folks:


For example, if my backup web server's IP is: 123.456.789.123
This odd domain is: 123-456-789-123-astatic416-dsl.ucc-net.ca


Looks like the PTR of your IP, my static ADSL IP addresses reolve to something similar.

Handy site for checking thigs like this is [http://www.mxtoolbox.com/](http://www.mxtoolbox.com/)

---

### Post by garfonzo on 2011-07-05
> **e79 said:**
> `123-456-789-123-astatic416-dsl.ucc-net.ca` is simply the FQDN of the modem at your remote location (where the backup server is). What you saw in your logs are attempts to get from your remote location to your main location (garage I assume). Are both server replicating things, like is the backup server is synching with your main server maybe ?



Thanks for the reply. When I type [www.mydomain.com](www.mydomain.com), I do in fact see the corresponding request at the server, so that is good. The two machines are not syncing with each other. I do that manually since changes are few and far between. I suppose somehow the two machines are in fact "talking" to each other? Seems odd.

---

### Post by garfonzo on 2011-07-05
> **Lloyd_mcse said:**
> Looks like the PTR of your IP, my static ADSL IP addresses reolve to something similar.

Handy site for checking thigs like this is [http://www.mxtoolbox.com/](http://www.mxtoolbox.com/)

Sweet, thanks for the link. A new bookmark is formed. :-)

---

### Post by e79 on 2011-07-05
> **garfonzo said:**
> I do that manually since changes are few and far between. 
Is it possible to track back the last change you did and check if the date and time concur with what you have in your logs ?

> I suppose somehow the two machines are in fact "talking" to each other? Seems odd.
Unless there is some form of cluster or direct replication that we are not aware of, I do not see how they could.

---

