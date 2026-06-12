---
title: "Proxy Server and Geographical Location"
date: 2007-10-14
forum: Server Platforms
---

### Post by moogyd on 2007-10-14
Hi,

Simple question : Can I setup a local proxy server to mask/change my geographical location ?

Certain websites restirct content based (I assume) on checking the IP address and looking up the ISP. I assume that this information is just extracted from the HTTP request.
If my understanding is correct (a big if :) ), then all my proxy server needs to do is change the HTTP requests to change the IP address.

Is my understanding correct? and if so, can anyone recommend a good (easy to setup) server for my Ubuntu installation.

(I have googled but all talk about proxies seems to be related to privacy concerns)

Thanks,

Steven

---

### Post by foxylad on 2007-10-14
Simple answer: yes - in fact any router will do this for you, translating between your internal IP addresses and your external IP address (your actual internet IP address).

But the sting in the tail is that you can't just tell your router to use any old external IP address - if you did nothing would work because responses to packets would go to the rightful owner of that IP address. So to achieve what you want, you have to get your ISP to give you an IP address from some other region, and that just ain't gonna happen.

My final comment would be to test your theory about teh web site using the IP address to distinguish different regions. There are other methods, by looking at character sets and time zones in hte request header, for instance.

---

### Post by MJN on 2007-10-15
A proxy can do exactly what you want but, as foxylad says about your router, it is limited to using the specific address from its location rather than any arbitrary one.
 
Hence, you need to find a public (free/paid-for) proxy that you can use - all requests (and responses) would be sent via this proxy and thus, to the remote end, would appear as if that's where the 'user' is located.
 
However, geographic determination from IP address is fraught with errors and false results hence sites that utilise such methods (e.g. support sections of international companies, global commerce sites etc) usually allow the user to correct the assumed geographic location in order to get the right content.
 
Are you able to share a URL that you suspect of customising content based on location?
 
Mathew

---

### Post by moogyd on 2007-10-15
Thanks for the responses, even though they are not the answers that I wanted. :(

An example of the site I was interested in was the UK ITV (itv.com), where the check the location of the requester before releasing content. This makes it difficult when I am travelling.

It is possible to access this information via a UK based proxy, but these seem to be quite slow.

Thanks,

Steven

---

### Post by MJN on 2007-10-15
Ah, yes, I'd forgotten about media-related stuff. I know a lot of the BBC content (recorded broadcasts) have geographic limitations.
 
Other than looking for a reliable/fast UK-based proxy how about running a server at home to act as your proxy whilst travelling? (presumably with a laptop?)
 
Mathew

---

