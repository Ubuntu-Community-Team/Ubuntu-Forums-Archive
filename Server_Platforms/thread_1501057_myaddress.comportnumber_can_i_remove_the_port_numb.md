---
title: "myaddress.com:portnumber can i remove the port number?"
date: 2010-06-03
forum: Server Platforms
---

### Post by constellanation on 2010-06-03
Hi, 
I have my own server set up and running quite well (for the most part.) I'm using dyndns to host my domain name as I don't have a static ip, and I have it set up to read on port 75 since my isp blocks port 80 (it's a small personal site, I don't want to pay extra for either feature) however this results in my domain address being 
[http://mysite.com:75](http://mysite.com:75)
is there anyway to remove (make invisible) the :75 so I can just give friends [http://mysite.com?](http://mysite.com?)

Thanks in advance.

---

### Post by Bachstelze on 2010-06-03
No-IP supports this. No idea about dyndns, but if it doesn't, I guess you can switch to No-IP.

---

### Post by constellanation on 2010-06-03
I found a service in dyndns that's called webhop, which seems almost like what you mentioned for the no-ip. However when i put 

mysite.com:75 in the redirect for the "webhop" it says that cyclical redirects are not allowed. Guess I'll have to look into no-ip. 


another question do most domain name providers offer that solution, if I decide to purchase a domain (which I am, just perhaps when I've been running a server for more then a week)

---

### Post by NullHead on 2010-06-03
I believe [name.com](http://name.com) supports this feature. I got a cheap *.org domain for $7 and I've had absolutely no issues thus far. Then again, I'm pointing the domain at a dedicated virtual host, so port 80 is available to me, thus I'm not able to tell you if you can specify a different port other than 80.

---

### Post by BoneKracker on 2010-06-03
> **constellanation said:**
> I found a service in dyndns that's called webhop, which seems almost like what you mentioned for the no-ip. However when i put 

mysite.com:75 in the redirect for the "webhop" it says that cyclical redirects are not allowed. Guess I'll have to look into no-ip. 


another question do most domain name providers offer that solution, if I decide to purchase a domain (which I am, just perhaps when I've been running a server for more then a week)

I think all you need to do is make sure you're not using the exact same URL for both.  Look at their example:
```
myhost.dyndns.org to mysecondhost.dyndns.org:8000)
```

I'll bet you can get it to work.

---

