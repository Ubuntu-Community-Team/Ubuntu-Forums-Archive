---
title: "Need help with NGROK TLS to Websockets via SSL"
date: 2017-05-12
forum: Server Platforms
---

### Post by Pandee on 2017-05-12
Hello!

I am not too sure how to explain my current situation (or if it is in the right place to ask)... but i will try.

I have websockets listening into ports - Primarily allowing log file streaming. Which I wish to secure with SSL / credentials 

I decided to get NGROK ([https://ngrok.com/](https://ngrok.com/)) to help me give access to my select users. Now I am trying to get NGROK TLS (SSL) connection to work but i keep getting an SSL mismatch error of some kind. You see, with ngrok you can connect a websocket to an address. In this case my own address. This requires a CNAME to be connected to the domain in question. Which brings in issues.

I first tried making an A record to example: subdomain.domain.com but that didnt work, so then i decided to make a proper subdomain with Lets-Encrypt attached to it. However when i try to install it with the "www" L-E wont work as it isn't pointing to itself (via CNAME) for that SSL check to work. Then, if i try to not use the www and connect the TLS to the SSL certificate it says something like 'www.sub.domain.com is not sub.domain.com'

I'm not sure which way to approach this problem. Any help and input would be greatly appreciated

---

### Post by howefield on 2017-05-13
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

