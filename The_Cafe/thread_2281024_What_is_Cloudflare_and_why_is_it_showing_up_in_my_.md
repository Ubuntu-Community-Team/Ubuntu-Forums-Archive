---
title: "What is Cloudflare and why is it showing up in my browser?"
date: 2015-06-03
forum: The Cafe
---

### Post by wizrddreams on 2015-06-03
I don't think this is necessarily the right place to be posting this. 
But I am curious to see if anyone else on the forums has run into this or knows what it is. 
I will attach screenshot's of the output below. 
I am slightly concerned/interested as I have never seen this before. 
I ran into it when I was going to do stuff on <removed>. 
[IMG]http://i.imgur.com/SsOuy7K.png[/IMG]
[IMG]http://i.imgur.com/aEpPKH6.png[/IMG]

---

### Post by sandyd on 2015-06-03
*Moved to Cafe*

Cloudflare is a CDN and security gateway that some websites may use to accelerate their content and to block DDOS/other malicious attacks. The traffic passes through Cloudflare, and then to the server hosting the site content.

That particular page shows up when Cloudflare has a connectivity issue with the server that actually hosts the content.

---

### Post by night_sky2 on 2015-06-04
It means the server is down.

Either because they are too many people trying to access it, or because they got hit by a DDOS attack (which is quite frequent on these types of website).

---

### Post by Habitual on 2015-06-05
I saw it on occasion when I used CF.
It's transitory and should not last long.

---

