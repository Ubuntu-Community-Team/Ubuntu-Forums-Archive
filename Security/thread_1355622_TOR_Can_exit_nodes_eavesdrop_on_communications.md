---
title: "TOR: Can exit nodes eavesdrop on communications?"
date: 2009-12-15
forum: Security
---

### Post by emigrant on 2009-12-15
> 
Yes, the guy running the exit node can read the bytes that come in and out there. Tor anonymizes the origin of your traffic, and it makes sure to encrypt everything inside the Tor network, but it does not magically encrypt all traffic throughout the Internet. 
This is why you should always use end-to-end encryption such as SSL for sensitive Internet connections. (The corollary to this answer is that if you are worried about somebody intercepting your traffic and you're *not* using end-to-end encryption at the application layer, then something has already gone wrong and you shouldn't be thinking that Tor is the problem.) 
Tor does provide a partial solution in a very specific situation, though. When you make a connection to a destination that also runs a Tor relay, Tor will automatically extend your circuit so you exit from that circuit. So for example if Indymedia ran a Tor relay on the same IP address as their website, people using Tor to get to the Indymedia website would automatically exit from their Tor relay, thus getting *better* encryption and authentication properties than just browsing there the normal way. 
We'd like to make it still work even if the service is nearby the Tor relay but not on the same IP address. But there are a variety of technical problems we need to overcome first (the main one being "how does the Tor client learn which relays are associated with which websites in a decentralized yet non-gamable way?"). 

```
https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#ExitEavesdroppers
```

so hows this going to effect the users? i mean the exit node dont really know who is the first node (original user) right?

thank you for your time.

---

### Post by cdenley on 2009-12-15
> **emigrant said:**
> ```
https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#ExitEavesdroppers
```

so hows this going to effect the users? i mean the exit node dont really know who is the first node (original user) right?

thank you for your time.

Yes, that is the idea. Tor doesn't hide your traffic, it only hides the origin. In the unlikely scenario that someone controls both the first node and exit node, they might be able to analyze traffic patterns and determine where the traffic is coming from, though. Also, if you disclose your identity within your traffic's data, then tor doesn't help much.

---

### Post by emigrant on 2009-12-15
thank you for your reply. then how to achieve maximum anonimity. ? or is that something i need to care about? or is tor enough?

---

### Post by User3k on 2009-12-15
> **emigrant said:**
> thank you for your reply. then how to achieve maximum anonimity. ? or is that something i need to care about? or is tor enough?


Turning off flash, java, javascript. Having no add-ons. Is a good start.

This link might be helpful to you so you know what info, some of it, that you give away every time you go to a website.

[http://www.auditmypc.com/anonymous-surfing.asp](http://www.auditmypc.com/anonymous-surfing.asp)

---

### Post by emigrant on 2009-12-15
thank for your reply. how to make the isp unaware what site u visit. does tor does that job? i think this is important bcz since recently govs put more censorship like china nd australia ;)

---

### Post by User3k on 2009-12-15
I haven't used tor in awhile. Someone else that is using it now might be able to answer that question better then me. But when I did use/try it, it seemed to work well, but can be slow.

---

### Post by cdenley on 2009-12-15
> **emigrant said:**
> thank for your reply. how to make the isp unaware what site u visit. does tor does that job? i think this is important bcz since recently govs put more censorship like china nd australia ;)

With tor, all traffic going through your ISP is encrypted, so your ISP and anyone between you and the tor exit node won't know what sites you visit, unless you accidentally reveal this information with unencrypted traffic like DNS requests or flash/java generated traffic, or they can analyze traffic patterns as I described earlier.

---

