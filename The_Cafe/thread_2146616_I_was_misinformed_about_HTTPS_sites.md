---
title: "I was misinformed about HTTPS sites"
date: 2013-05-19
forum: The Cafe
---

### Post by kenweill on 2013-05-19
Normally, when I have a website, mywebsite.com, that has a link going to other's website, otherswebsite.com, the other's website is able to determine where the traffic comes from. The other website will be able to determine that someone access their website via my website.

And then I asked some of my friends, "Is it possible to have a link in my website going to another website, that the other's website will not be able to determine that a traffic was coming from my website?". Most of them answered, "Yes, and it's only possible if my website is an https website."

For some reason, I did some experiment with my website. I availed a free 1 years SSL certificate from my hosting, they installed it in my website and so my website became an https website. I did some tests, with my other website, and this time it really seemed like the other website can't trace or doesn't record a log about my website accessing the other website. As if traffic comes from a direct link (or a link entered directly on browser), from somewhere else, where it doesn't show that it has a traffic coming from my website.

I then applied for an affiliate website where I need to register an account, and an affiliate link pointing to their website. From their logs, it was recorded that a traffic came from my website, https website. 

And so I wondered, "what went wrong?". 

I was having an impression that when my website is using SSL or is an https website, any website that I linked to is not able to determine that the traffic came from my website, since it's an https website.

Is there actually a way to post a link from my website going to another website without telling the other website that the traffic came from my website?

---

### Post by flanagan on 2013-05-19
If your secure location (HTTPS) links to a non-secure location (HTTP) then the referer field is withheld, otherwise the referer field is sent. See [HTTP_referrer]("http://en.wikipedia.org/wiki/HTTP_referrer") for more of an overview of the referer field, including some methods for withholding it.

---

### Post by kenweill on 2013-05-19
> **flanagan said:**
> If your secure location (HTTPS) links to a non-secure location (HTTP) then the referer field is withheld, otherwise the referer field is sent. See [HTTP_referrer]("http://en.wikipedia.org/wiki/HTTP_referrer") for more of an overview of the referer field, including some methods for withholding it.

The target URL is in fact an https site. So that's the reason why it's able to determine the traffic source.

https to https determines traffic source.
https to http, doesn't determine the traffic source.

As with my experiment, the other website is an http site which is why it doesn't determine the incoming traffic from my website since my website is an https site.

So all https sites are able to determine the source of the incoming traffics. And http sites can only determine incoming traffic if the referring site is not an https site.

Since my target affiliate link is an https site, I'll try to experiment changing the https part to http part. I'm not sure though if it still able to determine my website as the referring website. Accessing it via http still works but it automatically convert to https.

What if, my website is a https website and link is http site, but on http site side, they automatically convert http to https, will the target URL be able to determine the referring website?

---

