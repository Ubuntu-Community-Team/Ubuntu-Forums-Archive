---
title: "Different DNS replies depending on IP block"
date: 2008-08-21
forum: Server Platforms
---

### Post by kurtkraut on 2008-08-21
I own a service that has mirrors all around the world. I'd like to Bind to respond a DNS request of my A ADDRESSes differently, depending on the IP block that made the request

For instance, from a computer from an ISP provider would have this:
```

[root@computer1 etc]# host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12
```


And another person from another ISP would have:

```
[root@computer2 etc]# host ubuntuforums.org
ubuntuforums.org has address 208.69.32.230
```

Anyone has a clue how I could do that ? Thanks in advance

---

### Post by MJN on 2008-08-22
Sure - search for information on 'BIND views'.
 
[Here's]("http://www.oreillynet.com/pub/a/oreilly/networking/news/views_0501.html") as a good starting point, and whilst you're at it consider buying Cricket's 'DNS and BIND' book as it is considered by most, if not all, to be the DNS bible.
 
Mathew

---

