---
title: "Firefox 11 SPDY"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cap10devnull on 2012-02-05
Anyone enabled SPDY in firefox  11 ?
[http://hacks.mozilla.org/2012/02/spdy-brings-responsive-and-scalable-transport-to-firefox-11/](http://hacks.mozilla.org/2012/02/spdy-brings-responsive-and-scalable-transport-to-firefox-11/)
>  
Firefox 11 contains the first Firefox implementation of the SPDY  protocol. SPDY is a secure web transport protocol that encapsulates  HTTP/1 while replacing its aging connection management strategies. This  results in more responsive page loads today and enables better  scalability with the real time web of tomorrow.
 
any reviews , are you experiencing any difference while browsing ?

---

### Post by dino99 on 2012-02-05
thanks for the news, its the first time i hear about that, so may give it a try.

well you can already get some ideas about it by reading the comments:
[http://hacks.mozilla.org/2012/02/spdy-brings-responsive-and-scalable-transport-to-firefox-11/](http://hacks.mozilla.org/2012/02/spdy-brings-responsive-and-scalable-transport-to-firefox-11/)

---

### Post by zika on 2012-02-05
> **cap10devnull said:**
> Anyone enabled SPDY in firefox  11 ?
[http://hacks.mozilla.org/2012/02/spdy-brings-responsive-and-scalable-transport-to-firefox-11/](http://hacks.mozilla.org/2012/02/spdy-brings-responsive-and-scalable-transport-to-firefox-11/)
 
any reviews , are you experiencing any difference while browsing ?Thank You very much for this HU...
Using FF13 but did not know nothing about SPDY...

---

### Post by jfernyhough on 2012-02-05
Had this enabled since it appeared in Nightly (around 4th Dec). about:config , network.http.spdy.enabled .

Hasn't seemed to make a huge difference so far for me, though I do use Chromium for things like Google Maps. :)

[https://bugzilla.mozilla.org/show_bug.cgi?id=528288#c174](https://bugzilla.mozilla.org/show_bug.cgi?id=528288#c174)

---

### Post by zika on 2012-02-05
> **jfernyhough said:**
> Had this enabled since it appeared in Nightly (around 4th Dec). about:config , network.http.spdy.enabled .

Hasn't seemed to make a huge difference so far for me, though I do use Chromium for things like Google Maps. :)

[https://bugzilla.mozilla.org/show_bug.cgi?id=528288#c174](https://bugzilla.mozilla.org/show_bug.cgi?id=528288#c174)
Even for Chrom{e,ium} command line switch is needed, isn't it? It doesn't seem to be on by default at my place...
(--enable-websocket-over-spdy I guess)

---

### Post by paul_in_london on 2012-02-05
> **jfernyhough said:**
> Had this enabled since it appeared in Nightly (around 4th Dec). about:config , network.http.spdy.enabled .

Hasn't seemed to make a huge difference so far for me, though I do use Chromium for things like Google Maps. :)

[https://bugzilla.mozilla.org/show_bug.cgi?id=528288#c174](https://bugzilla.mozilla.org/show_bug.cgi?id=528288#c174)

Thanks guys. I didn't realise SPDY could now be enabled in FF (Like **zika**, I'm using FF 13). It'll be interesting to see how this pans out.

Some more links:

```
[www.webpronews.com/google-spdy-gaining-adoption-2012-01](www.webpronews.com/google-spdy-gaining-adoption-2012-01)
[news.cnet.com/8301-17939_109-57364563-2/googles-spdy-accelerator-gets-new-wind-in-its-sails/](news.cnet.com/8301-17939_109-57364563-2/googles-spdy-accelerator-gets-new-wind-in-its-sails/)
[www.webmonkey.com/2012/01/google-works-on-internet-standards-with-tcp-proposals-spdy-standardization/](www.webmonkey.com/2012/01/google-works-on-internet-standards-with-tcp-proposals-spdy-standardization/)
[lists.w3.org/Archives/Public/ietf-http-wg/2012JanMar/0098.html](lists.w3.org/Archives/Public/ietf-http-wg/2012JanMar/0098.html)
[lists.w3.org/Archives/Public/ietf-http-wg/2012JanMar/0111.html](lists.w3.org/Archives/Public/ietf-http-wg/2012JanMar/0111.html)
```

---

### Post by Bobhuber on 2012-02-06
Thanks - Seems to be a noticeable  difference on my system .

---

### Post by lovinglinux on 2012-02-07
I haven't been able to detect any perceivable difference.

---

### Post by sammiev on 2012-02-07
Some of my pages have been noticeable faster and others still the same. Over all I will keep using it.

---

### Post by pressureman on 2012-02-07
Very few sites currently support SPDY... a couple of Google sites, other than that, I haven't heard of anywhere else. Simply enabling it on Firefox will not automatically make the whole web faster for you.

The Apache module mod_spdy is still in its very early stages, so even though Apache is the most widely deployed web server on the Internet, very, very few sites will be running that module.

Where SPDY is most likely to be noticeably faster are on sites that send a lot of small AJAX requests (like Facebook, if/when they support it).

---

### Post by deuscool on 2012-03-14
hey guys, i am not very techy guy. so can anyone tell me how to enable spdy. i searched in google wiki. all of them are telling that It can be turned on through the *network*.*http*.*spdy*.*enabled* preference in about:config but how to go this page i copied and pasted the above path *(network*.*http*.*spdy*.[I]enabled) but it was not going to the page can anyone tell me how to enable the spdy in firefox 11 (a detailed way).


- Deuscool - 
[/I]

---

### Post by Space_Balls on 2012-03-14
> **deuscool said:**
> hey guys, i am not very techy guy. so can anyone tell me how to enable spdy. i searched in google wiki. all of them are telling that It can be turned on through the *network*.*http*.*spdy*.*enabled* preference in about:config but how to go this page i copied and pasted the above path *(network*.*http*.*spdy*.[I]enabled) but it was not going to the page can anyone tell me how to enable the spdy in firefox 11 (a detailed way).


- Deuscool - 
[/I]

You need to open the url "about:config" in firefox, then you can use the filter to search for "network.http.spdy.enabled". Set it to true (double lick) and you should be done.

---

### Post by Gregory Lee on 2012-03-14
In the spirit of adventure, I enabled SPDY for my Firefox 11, and about an hour later, Firefox killed my system.  Well, it could have been Firefox, anyway -- system froze up completely when I had just clicked my right mouse button on a web page link.  Maybe it was a coincidence.  There's nothing relevant in /var/crash/.

---

### Post by pressureman on 2012-03-15
I've been running Firefox with SPDY enabled since the first 11.0 betas hit the repos. No noticeable side effects. No noticeable improvement either, although I didn't expect to see any.

---

### Post by Gavin77 on 2012-03-15
SPDY only works on secure (https) pages so you won't see any difference on most webpages but it definitely makes an improvement.

For me:
[http://spdytest.com/](http://spdytest.com/) loads in 2316ms
[https://spdytest.com/](https://spdytest.com/) loads in 1658ms

---

### Post by pressureman on 2012-03-16
> **Gavin77 said:**
> SPDY only works on secure (https) pages so you won't see any difference on most webpages but it definitely makes an improvement.

For me:
[http://spdytest.com/](http://spdytest.com/) loads in 2316ms
[https://spdytest.com/](https://spdytest.com/) loads in 1658ms

Cool, I didn't know about that site. I got 2197ms on the HTTP site and 1330ms on the HTTPS/SPDY site - about 40% faster. Not bad.

---

### Post by pressureman on 2012-03-16
For anyone interested, the Apache mod_spdy project is hosted at [https://code.google.com/p/mod-spdy/](https://code.google.com/p/mod-spdy/)

The tl;dr version is that it requires an extremely recent version of OpenSSL (1.0.1, released two days ago as of writing this) in order to support SSL NPN (Next Protocol Negotiation), and you need to compile your own mod_ssl before you can even tackle the mod_spdy module.

Considering that most distros are VERY conservative at updating OpenSSL, it could be a while before we see support for this. There is however a (fairly old) Debian request for packaging at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628643](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628643)

I also ran across a Twitter post claiming that Nginx is aiming for SPDY support by May this year.

The IETF are also considering SPDY for inclusion in the HTTP 2.0 standard ([http://www.webmonkey.com/2012/01/google-works-on-internet-standards-with-tcp-proposals-spdy-standardization/](http://www.webmonkey.com/2012/01/google-works-on-internet-standards-with-tcp-proposals-spdy-standardization/)) although realistically, this could be years away. At least it will be possible in the interim via the NPN extensions to SSL.

I've attached an updated version of the build_modssl_with_npn.sh script, referred to in step 1 of [https://code.google.com/p/mod-spdy/wiki/GettingStarted](https://code.google.com/p/mod-spdy/wiki/GettingStarted) to pull down the official release of OpenSSL 1.0.1, and Apache 2.2.22 (as opposed to the beta release of OpenSSL, and Apache 2.2.21). The mod_ssl patch still applies cleanly, and everything builds successfully (on Debian wheezy - presumably also OK on Ubuntu precise). Just follow the rest of the steps on that "Getting Started" page. I have it running on my server - seems to be working fine :)

---

### Post by pqwoerituytrueiwoq on 2012-03-16
[http://spdytest.com/](http://spdytest.com/)
load time: 1315ms

[https://spdytest.com/](https://spdytest.com/)
load time: 804ms

[img]http://www.speedtest.net/result/1838294660.png[/img]

any chance OpenSSL 1.0.1 will make it into 12.04?

---

### Post by pressureman on 2012-03-16
> **pqwoerituytrueiwoq said:**
> any chance OpenSSL 1.0.1 will make it into 12.04?

Since OpenSSL 1.0.1 is not even packaged for Debian, I strongly doubt that we'd see it appear in Ubuntu first - especially in an LTS release. Besides, that's only one piece of the puzzle. You would still need to run a patched mod_ssl and compile mod_spdy yourself.

It's interesting to note in the SPDY draft:

> 
User-agents MUST support gzip compression. Regardless of the Accept-Encoding sent by the user-agent, the server may always send content encoded with gzip or deflate encoding.


The default Debian/Ubuntu Apache config has run with mod_deflate enabled for certain content-types for a while now, but the [http://spdytest.com](http://spdytest.com) (non-SPDY) mentioned a couple of posts back does not use gzip-encoding in the response. However, the SPDY version of that site will be using gzip-encoding as required by the spec. I wonder how much of the speed improvement is simply due to the gzip compression.

There will be some performance gains due to the fact that SPDY makes multiple URL requests in a single TCP connection, although this will mainly be visible on higher latency connections, where the cost of the TCP three-way handshake is high. In any case, HTTP 1.1 has supported this request pipelining for quite some time anyway - it's just that it's disabled in most browsers, mostly due to buggy server implementations. Perhaps SPDY is a chance to get it right.

---

### Post by pressureman on 2012-03-24
Well I didn't think it would happen in this release, but OpenSSL 1.0.1 has just been uploaded to precise, and is also packaged in Debian sid.

That just eliminated one of the steps needed to compile mod_spdy :)

---

