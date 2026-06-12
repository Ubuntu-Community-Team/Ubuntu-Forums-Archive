---
title: "Squid should serve the file from the cache no matter what mirror/url it is being req"
date: 2009-06-20
forum: Server Platforms
---

### Post by marklodge on 2009-06-20
[COLOR=DarkGreen][COLOR=Black]I'm having mixed success with squid cache proxy.
for example, i tried downloadin the file: [/COLOR][/COLOR][COLOR=DarkGreen]clamav-0.95.2.tar.gz
[COLOR=Black]The first time, it downloaded normally, the second time, it downloaded from the cache and the third. Then i wen to another pcon the network, and tried downloadin the same file and it downloaded from the cache. I was happy[/COLOR]..

[COLOR=Black]Then, after a few hours, i tried downloading it again and it did not download from the cache.

Have a look at the access.log attached[/COLOR][/COLOR][COLOR=DarkGreen][]("http://edugeek.net.woopra-ns.com/ping")
[COLOR=Black]
Maybe the download is coming from different mirrors[COLOR=DarkGreen][COLOR=Black]?
Will Store URL Rewriter work to maek all downloads of a certain file download from the cache if it has ben cached, whether or not it is downloadin the file from different hosts. 
For eg if the requested file is named[/COLOR]: [/COLOR][/COLOR][/COLOR][COLOR=DarkGreen][COLOR=Black][COLOR=DarkRed]clamav-0.95.2.tar.gz[/COLOR], and it resides in the cache, then squid should serve the file from the cache no matter waht mirror/url it is being requested from. Is this possible?[/COLOR] 
[/COLOR]

---

### Post by MJWitter on 2009-06-20
Just off hand I can't see this working unless you have a set list of filetypes which this applies to.  The reason I say that is that many sites will have files with the same name, say "logo.png" for example,  and this would lead to the same logo on every page.

---

### Post by marklodge on 2009-06-21
> **MJWitter said:**
> Just off hand I can't see this working unless you have a set list of filetypes which this applies to.  The reason I say that is that many sites will have files with the same name, say "logo.png" for example,  and this would lead to the same logo on every page.

thats true, therefore i would want to do it only for .zip .rar and other popular download extensions.

Anyway, how do i do it?

---

