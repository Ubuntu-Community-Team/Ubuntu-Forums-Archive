---
title: "Setting up servers at multiple locations"
date: 2010-03-27
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2010-03-27
Hey everyone,

So I've got a home server hosting a website for my restaurant, but I'd like to get another server up to get some redundancy going.

I have another machine I'd like to set up at another location to take over retrieving requests sent for the website whenever my home server goes down.
I've got my domain through godaddy.com, but the domain is hosted through everydns.com for their dynamic dns service (because im not using a static ip).

So I'm guessing having another server set up is just a matter of setting up dns records, however I don't know where to begin with setting that up. Any words of wisdom out there?
Thanks!

---

### Post by jflaker on 2010-03-27
Redundancy would mean that you are in essence load balanced using a round robin approach.  This could be a single server that does a ping then redirect for each server....if server a is unresponsive, it would ping and  redirect to server b...If server b is also unresponsive, put up a message of some sort...

Essentially, you would need a hosted server at some place like godaddy that is ALWAYS up to do this job....

If you have two separate servers, you would need to intervene should there be an issue to redirect DNS to the server b....DNS could take several hours to propagate across the internet and that would not be good as server a could already be up at that point.

Just my 2 cents

---

### Post by koenn on 2010-03-28
> **jflaker said:**
> Redundancy would mean that you are in essence load balanced using a round robin approach.  This could be a single server that does a ping then redirect for each server....if server a is unresponsive, it would ping and  redirect to server b...If server b is also unresponsive, put up a message of some sort...

Essentially, you would need a hosted server at some place like godaddy that is ALWAYS up to do this job....

If you have two separate servers, you would need to intervene should there be an issue to redirect DNS to the server b....DNS could take several hours to propagate across the internet and that would not be good as server a could already be up at that point.

Just my 2 cents
Not really. 
There's redundancy, and there's load balancing, and they are not the same. 

The setup you describe introduces a single point of failure, namely that server that checks which of the other two servers is up and redirects accordingly. And if that "hosted server at some place like godaddy that is ALWAYS up to do this job" is always up anyway, why not just host the website there ? 

The idea of having 2 separate servers and using DNS as 'fail-over' mechanism is not too bad, especially if you set the dns TTL rather short (1 hour or less ?). 
Other scenarios would involve clusters and heartbeats, redundant routes and routers, ...

OTOH, if you're serious about this website, running it from home over (presumably) a residential internet connection with dynamic address, no service level agreement, and limited upstream volume and speed, might not be the best choice.

---

### Post by fiveironfrnzy08 on 2010-03-28
Thank you both for your replies!

Not sure which I actually meant then, redundancy or other. I'm still learning about servers. I really have simply learned enough to set up a web server, direct the everydns.net servers to mine, and host the website. The reason I'm doing it all this way is cost and so I can learn. To get a website created, directed to my residential dynamic ip, hosted, and maintained has costed $14 (for the domain name, that's it). My point here is that I know it would be better to have godaddy or whoever actually host it and take care of everything there, but that's money that I don't want/need to spend when I could just learn about the stuff and do it myself. I'm under no pressure of the restaurant to have a grade-A website.
The website I'm hosting is for a small restaurant generating an average of 5-15 visits a day and the site is not very big, so I'm really not concerned about bandwidth at this point.

So that all being said, could you tell me more about redundancy versus load balancing and which one I'm really looking for? Would I need to set up a DNS server as well as the two web servers (I have several computers at my disposal)? Or can I simpy set up records at everydns.net to use the 2nd server if the 1st cannot be reached? Then how would I do that?
Really my main goal is to learn. This is stuff I want to go into. I'm in no serious rush to get it done, I just want an effective, costless set of servers running and to learn how it works.
Thanks again in advance and already for your advice!

---

### Post by Xipher on 2010-03-28
Redundancy is about handling failure as gracefully as possible.

Load Balancing is about distributing traffic/load across multiple hosts.

Often load balance devices also include redundancy measures so that if a member fails it redirects traffic to the live hosts.

Based on your description I think you're only interested in redundancy. My thoughts are have the backup device attempt to pull and confirm the site's up, if that fails a few times then have it start running the dynamic dns client to get the A record to change over to the backup. Keep in mind that DNS has caching so the longer you wait to start fail over it will take the time for the TTL to expire from that point for every one to get moved over.

---

