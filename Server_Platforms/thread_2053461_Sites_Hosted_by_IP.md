---
title: "Sites Hosted by IP"
date: 2012-09-05
forum: Server Platforms
---

### Post by the1joker on 2012-09-05
Hello,
 
I'm not sure if this belongs here but Ive been trying to figure out a script to find the sites hosted by a certain IP-address, i think it should be possible, but i can't seem to find a way to do this... anyone with any experience in this??
 
it would be just like [http://sameip.org](http://sameip.org) 
 
this can be in a bash or PHP or whatever is the best way to do this.
 
Thanks in advance!
 
Tobias

---

### Post by SeijiSensei on 2012-09-05
You mean you want to find all the sites on a server using name-based virtual hosting that share the same IP address?  I don't think that is possible at all.  Reverse DNS will only tell you the hostname associated with the IP address, but there could be hundreds of sites using that address.  Name-based hosting just matches the server name specified in a URL against a list of server definitions and returns the matching content.  You'd have to know at least the domain names of the sites you want to list.

And, frankly, as someone who hosts name-based sites I wouldn't want you to be able to do this either.  Why, for instance, should I give you a list of my clients?

---

### Post by sanderj on 2012-09-05
You could do it this way:

find as much URLs / FQDNs as you can.
Use "host <FQDN>" to find out the IP address
Create a database of all FQDN's pointing to the same IP address

---

### Post by SeijiSensei on 2012-09-05
Well, sure, but how you even know where to begin?  If you had an existing list of URLs and wanted to know whether they shared a common server, your method would work.  Otherwise you are just shooting in the dark.

---

### Post by sanderj on 2012-09-05
> **SeijiSensei said:**
> Well, sure, but how you even know where to begin?  If you had an existing list of URLs and wanted to know whether they shared a common server, your method would work.  Otherwise you are just shooting in the dark.

Just begin, and you can cover all (and thus it's not shooting in the dark). 

According to [http://www.whois.sc/internet-statistics/](http://www.whois.sc/internet-statistics/) and [http://www.daniweb.com/web-development/web-design-html-and-css/news/380974/how-many-internet-domain-names-are-there#](http://www.daniweb.com/web-development/web-design-html-and-css/news/380974/how-many-internet-domain-names-are-there#) there seem to be about 250.000.000 domains. If the script / robot can handle 100 domains per second, it will take 250.000.000/100 seconds to create the whole database. That's less than a month (29 days to be precise: (250 000 000 / 100) / (3600 * 24) = 28,9351852). So that sounds feasible to me (assuming the OP really wants to have this information).

From that moment on the OP will have a very unique and valuable database.

---

### Post by the1joker on 2012-09-05
@ [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") 

It is possible, like on the example site i posted, i want exactly that.

@ SanderJ 

i have tried that too, but there is something you are overlooking, how do you get the FQDNs if you don't know what they are, i randomly can genereate them, but by my calculation if i randomly create webaddresses, with all existing extensions, it would take my server about 300 years to scour the internet and then ping all those if they actually resolve to a address.

Therefor i want to use IP's, they are limited and therefore can be much easier put into a loop and then put all sites hosted on that IP into the database.

---

### Post by lisati on 2012-09-05
I'm not sure why you would want to do this. If the websites are on a webserver that you're responsible for, wouldn't it be quicker and eaiser to look in the configuration files, e.g. apache's "sites available"??????

---

### Post by sanderj on 2012-09-05
> **the1joker said:**
> 
@ SanderJ 

i have tried that too, but there is something you are overlooking, how do you get the FQDNs if you don't know what they are, i randomly can genereate them, but by my calculation if i randomly create webaddresses, with all existing extensions, it would take my server about 300 years to scour the internet and then ping all those if they actually resolve to a address.

Therefor i want to use IP's, they are limited and therefore can be much easier put into a loop and then put all sites hosted on that IP into the database.

I've written and used such a robot/script to find IPv6 enabled websites. I used Google to find FQDN's: just feed Google one or two random words, and request 100 (or 1000) search results from Google. So ... that's a way to find FQDNs. And you're probably only interested in domains, which is a subset of FQDNs, so that's easier.

Please be aware that there are more IPv4 address (about 4 billion) than domains (250 million).


But anyway: I have the feeling that you're looking for an easy way to go from IP address to hosted domains. And that does not exist.

---

### Post by Cheesemill on 2012-09-05
> **sanderj said:**
> Just begin, and you can cover all (and thus it's not shooting in the dark). 

According to [http://www.whois.sc/internet-statistics/](http://www.whois.sc/internet-statistics/) and [http://www.daniweb.com/web-development/web-design-html-and-css/news/380974/how-many-internet-domain-names-are-there#](http://www.daniweb.com/web-development/web-design-html-and-css/news/380974/how-many-internet-domain-names-are-there#) there seem to be about 250.000.000 domains. If the script / robot can handle 100 domains per second, it will take 250.000.000/100 seconds to create the whole database. That's less than a month (29 days to be precise: (250 000 000 / 100) / (3600 * 24) = 28,9351852). So that sounds feasible to me (assuming the OP really wants to have this information).

From that moment on the OP will have a very unique and valuable database.

Your maths doesn't look very convincing to me, you're making some massive assumptions here.

For a start, you don't actually have a list of valid domain names to parse. Because of this you would have to iterate through all possible domain names to find out which existed and which didn't.

Some quick 'back of a beer mat' calculations of mine follow...

There are 37 valid characters in a domain name (a-z, 0-9, -).
Domain names (not including the TLD suffix) can be anything up to 36 characters.
There are currently around 280 TLD's.

This gives you roughly 37^36 x 280 = 8 x 10^58 possible domain names.

Even if you could resolve 100 domains per second (which is doubtfull), then you are still looking at around 2.5 x 10^49 years to process all of the available domains (which is millions of times larger than the age of the universe).

Even if you could attempt this then your list would be massively out of date before you even made a dent into this number because of old domains that weren't renewed as well as new domains that are being registered. Also I haven't accounted for domains that are using a dynamic IP or even started thinking about sub-domains.

---

### Post by sanderj on 2012-09-05
> **Cheesemill said:**
> Your maths doesn't look very convincing to me, you're making some massive assumptions here.

For a start, you don't actually have a list of valid domain names to parse. Because of this you would have to iterate through all possible domain names to find out which existed and which didn't.



I have the idea you didn't read my post I posted 30 minutes before your post.

---

### Post by Cheesemill on 2012-09-05
> **sanderj said:**
> I have the idea you didn't read my post I posted 30 minutes before your post.
Nope.

I clicked on reply before going to have my tea, then posted after I'd eaten :)

---

### Post by SeijiSensei on 2012-09-05
> **Cheesemill said:**
> There are 37 valid characters in a domain name (a-z, 0-9, -).
Domain names (not including the TLD suffix) can be anything up to 36 characters.
There are currently around 280 TLD's.

Actually ICANN increased the length of domain names to 255 characters so the search space is exponentially larger than your estimates.  ICANN also adopted the "internationalized" domain name system to accomodate non-Western sites that use characters like Chinese or Japanese.

[http://en.wikipedia.org/wiki/Domain_name](http://en.wikipedia.org/wiki/Domain_name)
[http://en.wikipedia.org/wiki/Internationalized_domain_name](http://en.wikipedia.org/wiki/Internationalized_domain_name)

The notion that you could set up a computer in your house or office to recurse through all possible domain names before you die is absurd.

You could spider the web and accumulate a list of active server names by following links as Google and other engines do.  Good luck with that without an army of machines at your disposal.

On top of all that you have the problem of sites that don't use hostnames like "www.domain.name".  A domain could have a enormous number of sites of the form "something.domain.name" or "somethingelse.something.domain.name", etc.

> **sanderj said:**
> But anyway: I have the feeling that you're looking for an easy way to go from IP address to hosted domains. And that does not exist.

My point exactly.

I'm still waiting for someone to explain why you would want to do this.

---

### Post by the1joker on 2012-09-05
Okay but from this i assume no one knows how they do this at the example site i gave... 

[http://sameip.org/](http://sameip.org/)

Since i come to the same massive calculations if i would have to resolve all addresses, and im sure that that site uses some forward and/or reverse scripts since they can find domains that i have running on my site, but that aren't resolved globally through the DNS of my registrar....

Why i want to do this, if it helps, is simply to be able to find existing domains within certain TLD's not for registration purposes but simply for the content they will offer.

It mostly seems interesting to me since obviously this is something very uncommen and prolly tricky to do, but i'm sure it's possible and i am always looking to figure out new stuff!

---

### Post by fang0654 on 2012-09-05
I just tried out that site, and it got 31 out of 74 sites I had hosted on one of my servers.

My guess would be that somewhere in Google's search results (or another web crawler) IP information is accessible and is being parsed.

---

### Post by Cheesemill on 2012-09-06
> **the1joker said:**
> Okay but from this i assume no one knows how they do this at the example site i gave... 

[http://sameip.org/](http://sameip.org/)

This site doesn't work properly.

I just tried with the IP of one of my web servers and it only gave me 2 out of around 50 domains as a result.

---

### Post by koenn on 2012-09-06
> **fang0654 said:**
> I just tried out that site, and it got 31 out of 74 sites I had hosted on one of my servers.

My guess would be that somewhere in Google's search results (or another web crawler) IP information is accessible and is being parsed.

> **Cheesemill said:**
> This site doesn't work properly.

It still works remarkably well, in light of what SeijiSensei said.

I was wondering if something like this could be achieved by extensive DNS querying, possibly  working back from an IP to a domain to name servers ... etc.

On the other hand, if the people that run that sameip site have access to, say, a web proxy or a cache-and-forward DNS server that is used by a pretty random but reasonable large sample of internet users (an ISP maybe, or a DNS provider, ...), they'd have the opportunity to build a pretty large, but incomplete, database of site FQDNs and their ip addresses, wouldn't they ?

---

### Post by Cheesemill on 2012-09-06
The best way that I can think of to get such a database would be to get a zone transfer from all of the root nameservers, I can't see you persuading ICANN to let you do this though :)

Even then this wouldn't give you access to all of the subdomains for a particular domain.

---

### Post by SeijiSensei on 2012-09-07
> **Cheesemill said:**
> The best way that I can think of to get such a database would be to get a zone transfer from all of the root nameservers, I can't see you persuading ICANN to let you do this though :)

Even then this wouldn't give you access to all of the subdomains for a particular domain.

Back in 1994 when I decided to go into the Internet business, I browsed around to see what domain names were in use.  At the time you could download a complete list of registered domains in the global domains like .com and .net from Network Solutions.  As I recall there were fewer than a hundred thousand entries on that list.  Hard to imagine nowadays.

> **koenn said:**
> if the people that run that sameip site have access to, say, a web proxy or a cache-and-forward DNS server that is used by a pretty random but reasonable large sample of internet users (an ISP maybe, or a DNS provider, ...), they'd have the opportunity to build a pretty large, but incomplete, database of site FQDNs and their ip addresses, wouldn't they ?

Sure.  So would logging all the requests made to a widely-used DNS server like Google's.  I always presumed that was a reason they offered a public DNS server in the first place.  Big ISPs like the telcos could build large databases from queries as well.  So could a service like [Alexa]("http://www.alexa.com/").  They even make their [list of the top 1,000,000 sites]("http://s3.amazonaws.com/alexa-static/top-1m.csv.zip") available free.

---

