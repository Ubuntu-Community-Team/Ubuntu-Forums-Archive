---
title: "DNS based failover"
date: 2006-10-31
forum: Server Platforms
---

### Post by catfox on 2006-10-31
Hi there,
I want to set up a network with some failover.
I have a firewall/dns box, and behined that I have two webservers (webA and webB).

the dns knows webA and webB by the ip addresses 192.168.100.101 and .102, with the hostname webserver.network.com.
I'd like the dns server to switch from using .101 to .102 if the .101 machine is down.

Is this done with some kind of daemon process which monitors the webserver connections, and changes the dns?

any thoughts would be appreciated.
thanks.

---

### Post by kidders on 2006-10-31
Hi there,

Unfortunately, swapping two computers' IP addresses like you described isn't always smart. Something like Heartbeat might suit you.

---

### Post by jimm on 2006-10-31
Hi,

One way to do this is using a reverse proxy function. I am not sure off the top of my head how you set it up, but I know apache will do reverse proxying and will probably handle the basic fail-over for you as well.

You wont need to worry about IP addresses, just the DNS names of the servers.

Have a look at the apache proxypass and proxypassreverse directives and see if there are any hints in there.

From memory I think you can do some fairly tricky stuff like this with Squid (the proxy server) as well. So check that out...

You can also use things like application firewalls (application proxies or whatever you want to call them) to do it. I mucked around with Delegate ([http://www.delegate.org/delegate]("http://www.delegate.org/delegate")) a bit for doing some stuff generic proxy stuff as well. 

Look at apache and squid first though. Delegate is a bit more of a config hassle!

Thanks,
James
Hope this helps!

---

