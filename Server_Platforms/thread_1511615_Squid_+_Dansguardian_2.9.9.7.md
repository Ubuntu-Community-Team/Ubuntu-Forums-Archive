---
title: "Squid + Dansguardian 2.9.9.7"
date: 2010-06-17
forum: Server Platforms
---

### Post by hmx_ryan on 2010-06-17
Hi, I'm having problem with my Proxy Server running Ubuntu 9.04 with Squid + Dansguardian 2.9.9.7 as my Web Cache Proxy and Content filtering at the same time...

Hope you could help me figuring out on this...

Here's my Problem:

When I access sports.yahoo.com, I get **Content Encoding Error**... But if I add my IP Address in the **Exceptioniplist** of Dansguardian, I can browse the sports.yahoo.com

Is there something I missed with my settings in dansguardian... ?

Please help

---

### Post by hmx_ryan on 2010-06-17
anyone here who could help me...uppp

---

### Post by metzen_w on 2010-06-18
It may be a bug related to 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501192](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501192)

More detail here
[http://squidproxy.wordpress.com/2008/04/29/chunked-decoding/](http://squidproxy.wordpress.com/2008/04/29/chunked-decoding/)

I quote from the site: 

How to tell if this is your problem?

Use squidclient to make a web request that bypasses the squid proxy. It should send out the HTTP/1.0 request and get a page back. If the headers of the response include “Transfer-Encoding: chunked” there is your problem.

This is currently only an issue in Squid 2.5 or earlier and 3.0, which is still highly modeled around 2.5.

The solutions are varied depending on your capabilities.

Simplest for some will be to just bypass squid for those domains.

[ UPDATE: (thanks Michael Graham)

Apparently several people are having success with simply dropping the Accept-Encoding header to certain of these broken servers. Adding this to their squid.conf :

# Fix broken sites by removing Accept-Encoding header
acl broken dstdomain ...
request_header_access Accept-Encoding deny broken

NP: don't forget to remove it again when you upgrade out of 3.0

]

Next best is to use peer-routing to divert those domain requests at a squid 2.6 (or if you are feeling experimental a 3.1 build)

If its a serious issue and you are accelerating for one of these broken web servers. Then you will need to stick with Squid 2.6 until 3.1 is available for production use.

---

### Post by hmx_ryan on 2010-06-25
Thanks for the Reply..

I also tried this one, however, I still got the same Content Encoding Error
> # Fix broken sites by removing Accept-Encoding header
acl broken dstdomain ...
request_header_access Accept-Encoding deny broken

I am running SQUID 2.7.STABLE3

---

