---
title: "New server, no DNS forwarders given"
date: 2007-04-04
forum: Server Platforms
---

### Post by BitHosts on 2007-04-04
Hey all, 
thanks in advance for having a read!

Ive got a new server and im tyring to get everything up and running.

First off - Ubuntu 6.06 (x86) fully up-to-date up until about a week ago...

I put the server in the data centre and havent been told the DNS servers to forward queries to, so while im waiting for the email response from the support team, im wondering if I could run my own DNS.  Ive looked around online and cant find much of help, all the tutorials etc talk about hosting your own DNS while I want to run a server to resolve my queries for external hosts.  Is it easy to query the root DNS servers, or am I missing the point?

I hope that made sense :s

Cheers All!

Felix

---

### Post by Zwalther on 2007-04-04
About dns servers: you can always use the servers from [http://www.opendns.com](http://www.opendns.com). 

I'm not sure what exactly you want to do with your own dns server. Do you mean you want to run a dns proxy? You could try dnsmasq, or do "apt-cache search dns proxy".

---

### Post by BitHosts on 2007-04-04
Sorry I wasnt very clear.

Primarily im trying to get my server to install packages and because the machine cant resolve any hostnames its not succeeding.  I think this is because i dont have any DNS servers set up and I wasnt given any by the datacentre (waiting on support email reply).  But one of the things im wondering is if i can bypass the need for the datacentres DNS servers by running my own that looks up directly from the root servers or something.

Thanks again!

Felix

---

### Post by Zwalther on 2007-04-04
Ok, I understand.

You can use some other dns server, but I wouldn't recommend using root servers. I would recommend opendns. It is pretty easy and quick to set up (see [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)), so you won't have to wait for the datacentre guys :)

---

### Post by BitHosts on 2007-04-05
Thats excellent, thankyou very much!

---

