---
title: "Squid with Multiple incomming/outgoin ip"
date: 2007-09-27
forum: Server Platforms
---

### Post by JSPT on 2007-09-27
I have both Squid and Webmin running on Ubuntu version 7.04.
The  main purpose is to use it as a proxy server for multiple incoming/outgoing ips.  My problem is with setting up the server with has 30 ips, and getting it to work on 30 open web browsers in the office each when viewed on spotip.com should show different ips. I have set about 7-8 to test on the conf file but only the first ip works. ACL and tcp_outgoing_address are set. Please take a look at my conf file if needed. Thanks, Pete

---

### Post by koenn on 2007-09-27
"ips" - do you mean IP addresses ?

If so, why would a server have / need 30 addresses ? 
And why do you "need" to have all clients show their own address ? 
What is the problem that you're trying to solve with this extremely weird setup ?

---

### Post by JSPT on 2007-09-27
Sorry if I wasn't clear. My problem is I have 30 ips that I want to use as proxy for my software, but I test each of these ips by entering them into I.E to see if they work which they don't, I only get page not found errors. Here is the link to the guide which I followed.
[http://patchlog.com/general/how-to-set-up-an-anonymous-proxy-on-debian/](http://patchlog.com/general/how-to-set-up-an-anonymous-proxy-on-debian/)
so basically setting up anonymous proxy in squid. Sorry if I wasn't clear, it's been
a long week.

Thanks,

Pete

---

### Post by koenn on 2007-09-27
OK, I read that howto and i now think i see the concept of what you're trying to do, but
the howto doesn't make sense to me, in that i don't see how the proxy can pass any of those 30 addresses as the outgoing address and actually get a reply, unless the machine in question actually has 30 addresses, i.e. it has 30 NIC's or it has 30 address aliases to 1 NIC or a combination of both. 
The network design/config to make this work seems to be missing from the howto.
That, or I'm still not getting it. 

That might be the problem you're describing, but your sentences are rather hard to read, and your choice of words (such as " proxy for my software") is confusing. 

Maybe (get some rest and) try to explain more accurately ?

---

