---
title: "apache access.log strange entry"
date: 2013-03-01
forum: Server Platforms
---

### Post by SlugSlug on 2013-03-01
Hi I get quite a lot of stuff like this showing in the logs & in webalizer
```

209.232-pool.nikopol.net - - [01/Mar/2013:19:28:54 +0000] "HEAD / HTTP/1.1" 200 711 "http://mogin.p-hilton.net/forum/4/drayver-klaviaturi-samsung/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
209.232-pool.nikopol.net - - [01/Mar/2013:19:28:55 +0000] "HEAD / HTTP/1.1" 200 711 "http://mogin.p-hilton.net/forum/4/drayver-klaviaturi-samsung/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
209.232-pool.nikopol.net - - [01/Mar/2013:19:29:33 +0000] "HEAD / HTTP/1.1" 200 711 "http://duet.p-hilton.net/list/11/ibm-t41-drayvera/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
209.232-pool.nikopol.net - - [01/Mar/2013:19:29:33 +0000] "HEAD / HTTP/1.1" 200 711 "http://duet.p-hilton.net/list/11/ibm-t41-drayvera/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
209.232-pool.nikopol.net - - [01/Mar/2013:19:30:13 +0000] "HEAD / HTTP/1.1" 200 711 "http://potew.microtronixsystems.com/list/6/drayver-dlya-printera-canon-ip2200/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
209.232-pool.nikopol.net - - [01/Mar/2013:19:30:13 +0000] "HEAD / HTTP/1.1" 200 711 "http://potew.microtronixsystems.com/list/6/drayver-dlya-printera-canon-ip2200/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"



```


Thats domain & IP has nothing to do with me am not to wooried just wondering how / why it shows in my logs :/

Thanks

---

### Post by GordThompson on 2013-03-01
The first entry, '209.232-pool.nikopol.net', is the remote host that is sending the HEAD requests to your server. If it is not being spoofed then it is an IP address for the ISP "PP MainStream" in Ukraine.

The other URLs are the "referrer" page. They may be bogus, but they do seem to have something in common: they look like discussion forums in Russian that appear to be for the distribution of device drivers.

My guess is that it is just bot noise. You could always consider banning the source IP address (or range) if it would make you feel better.

---

### Post by SlugSlug on 2013-03-02
So would they be somehow spoofing referrer's to climb search engine ranks?

---

### Post by Doug S on 2013-03-02
> **SlugSlug said:**
> So would they be somehow spoofing referrer's to climb search engine ranks?That seems likely, at least to me. On my site, and for several months now, I have been having troubles with forged referrer's. 95% of the issue is from Russia, Ukraine, and Romania. Since I don't care about possible collateral dammage (i.e. blocking an innocent party), I am now blocking some large IP address blocks from these areas. After some study of access logs, a tell tale signature became apparent: Always the same page; Always the same number of bytes in the response, and not typical for a real "GET"; Never gets favicon.ico; Never gets related .css file; Never gets embedded .png files. What I don't understand with this one, is why they bother, as I do not publish access data and such. However, I have published segments before, when writing up some investigation or other.

As a slight digression, I have another type of similar access issue, always for the same (but a different one than the above) web page, but the forged referrer is my own site (a page that does not link to the one in question). Other tell tale signature stuff is the same. So, again, why bother? What is the point? For this case, in my tcpdump logs, I did notice they were doing some odd stuff at the packet level with the TCP session, with new SYN packets and RST packets sort of jammed into the normal flow.

---

