---
title: "weird wifi?"
date: 2009-10-11
forum: The Cafe
---

### Post by sandyd on 2009-10-11
in my local library (toronto public library : Central Library)
the wifi connection requires me to agree to a terms of service each time i conenct .
I  have to accept the terms of service, otherwise all my traffic is redirected towards the terms of service.
it does this by redirecting to spyders.local

in ubuntu, when i connect, i can't access the terms of service page - the dns address just doesn't resolve.
which means i can't use internet
however, if i wait about 10-20 minutes, the internet magically starts working.

what in the world???

---

### Post by Bachstelze on 2009-10-11
Wrong DNS server maybe. Are you using DHCP to get an IP address?

---

### Post by sandyd on 2009-10-11
yep.

im not using any custom domain resolvers either.

i also tried pinging the server from my vista dual boot.
then inputed the address in firefox at ubuntu.
no luck either.

---

### Post by mr-woof on 2009-10-11
deffo sounds like a dns problem, does it work in vista?

---

### Post by sandyd on 2009-10-11
works properly in vista and xp machine.

---

### Post by Tipped OuT on 2009-10-11
> **mr-woof said:**
> deffo sounds like a dns problem, does it work in vista?

Nothing works in Vista. :)

---

### Post by mr-woof on 2009-10-11
do you get the same dns servers in both linux and windows?

---

### Post by sandyd on 2009-10-11
both are on auto dns - which means they use the DNS server provided by the network.
hmm. that might be the problem.
because the redirect code may be covering my laptops request for a DNS server. which means i won't be able to load the libary's servers.

---

### Post by mr-woof on 2009-10-11
might be worth taking the ip address down of the dns server and setting a static ip in linux and trying that

---

### Post by sandyd on 2009-10-11
lets see if manually overriding the DNS servers in /etc/hosts works....
by mapping spyders.local to the address i just found by pinging spyders.local in vista....

---

### Post by mr-woof on 2009-10-11
it shows i'm still learning and quite new to ubuntu, i didnt realise ubuntu had a host file like windows lol :)

that would of been my first suggestion :D

---

### Post by cariboo on 2009-10-11
The host file in Windows is still a leftover from when MS used the bsd tcp/ip stack. MS claims they don't use it any more, but it wouldn't surprise if they just suppressed the licensing info.

---

### Post by fduplex on 2010-04-03
I just came from the Maria A Shchuka library and had exactly the same problem with my laptop running Ubuntu.

I spent about 20 minutes trying to figure out why I was able to resolve the hostnames google.com and their own spyders.local from the terminal (host spyders.local returns an IP), and yet from Midori or Chrome browsers I get a resolution error, the same occurs when using wget at the prompt.

I verified both browsers have no proxy defined.

I have a suspicion now that IPv6 may be to blame.  Maybe their DNS server returns both IPv4 and IPv6 addresses, the browsers/resolver picks v6 over v4 and tries to connect to the IPv6 address resulting in some kind of error? or the DNS server is somehow broken

At the time I wasn't able to google how to disable v6 entirely, I will do so now and when I return to the library next week I'll give it another try and post my results here.

Toronto Public Library wireless is managed by Spyders, their website appears to be [http://spyders.ca/]("http://spyders.ca/") .. they also have a support phone number that I did not try yet, 1-888-855-3555.

---

### Post by sandyd on 2010-04-03
> **fduplex said:**
> I just came from the Maria A Shchuka library and had exactly the same problem with my laptop running Ubuntu.

I spent about 20 minutes trying to figure out why I was able to resolve the hostnames google.com and their own spyders.local from the terminal (host spyders.local returns an IP), and yet from Midori or Chrome browsers I get a resolution error, the same occurs when using wget at the prompt.

I verified both browsers have no proxy defined.

I have a suspicion now that IPv6 may be to blame.  Maybe their DNS server returns both IPv4 and IPv6 addresses, the browsers/resolver picks v6 over v4 and tries to connect to the IPv6 address resulting in some kind of error? or the DNS server is somehow broken

At the time I wasn't able to google how to disable v6 entirely, I will do so now and when I return to the library next week I'll give it another try and post my results here.

Toronto Public Library wireless is managed by Spyders, their website appears to be [http://spyders.ca/]("http://spyders.ca/") .. they also have a support phone number that I did not try yet, 1-888-855-3555.
its quite easy to fix you know. just add the ip and "spyders.local" to /etc/hosts

---

