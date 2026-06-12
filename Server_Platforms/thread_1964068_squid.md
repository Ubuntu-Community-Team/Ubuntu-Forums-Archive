---
title: "squid"
date: 2012-04-23
forum: Server Platforms
---

### Post by madunix on 2012-04-23
I have blocked file by extension to prevent downloading via squid,

acl BlockExt url_regex -i \.mp3$ \.zip$ \.asx$ \.wma$ \.wmv$ \.avi$ \.mpeg$ 
http_access deny BlockExt all

but still they could bypass proxy if they want download .zip , they write into the URL .zip?mmmm to get the file downloaded .... how can be this stopped.

---

### Post by newbie-user on 2012-04-23
I suppose you may have tried this already, but could you add .zip?mmmm to your list of regex.

---

### Post by madunix on 2012-04-23
after "?" they could write any string .... to get the file downloaded   file.zip?[anystring] will bypass the squid

---

### Post by newbie-user on 2012-04-23
That's interesting. What does the $ in your squid mean (.zip$)? I use regex blocking for my squid, but I do the blocking by specifying a file which contains keywords without $.

Here's my config:
```
acl localnet src 192.168.1.1-192.168.1.254
acl block_sites url_regex "/etc/squid/block_sites.acl"
http deny localnet block_sites
```

snippet from block_sites.acl:
```
swcdn.apple.com
facebook
.exe
```

I'll have to try adding ?[string] at the end of a url to see if I can bypass squid.

---

