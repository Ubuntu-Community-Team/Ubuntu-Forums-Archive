---
title: "Help: SSL, TLS, SASL"
date: 2009-12-25
forum: Server Platforms
---

### Post by ooobooontooo on 2009-12-25
Hi,

I'm a little confused about the following terms: SSL, TLS, SASL.

I've read SSL and TLS being used interchangeably and I've actually seen a website declare that they are the same (TLSv1 and SSLv3 that is). But, I'm almost 99% sure this is not the case. To my knowledge, with SSL, you start off with a secure socket and connect to that secure socket. Whereas in TLS, you you start off with an unsecure socket and issue the STARTTLS command to turn the traffic encrypted. I believe TLS also uses stronger encryption than SSL. Please correct me if I'm wrong.

Now SASL, I'm not even sure what that does. To my knowledge, it's another form of authentication mechanism between clients and servers... I often see TLS/SSL and SASL being used together. How do they interconnect? Is TLS/SSL the mechanism which provides encrypted traffic, while SASL the authentication mechanism that authenticates users?

Thanks in advance.

---

### Post by BkkBonanza on 2009-12-25
Why don't you just read up on it...

[http://en.wikipedia.org/wiki/Transport_Layer_Security](http://en.wikipedia.org/wiki/Transport_Layer_Security)

---

### Post by ooobooontooo on 2009-12-25
> **BkkBonaza said:**
> Why don't you just read up on it...

[http://en.wikipedia.org/wiki/Transport_Layer_Security](http://en.wikipedia.org/wiki/Transport_Layer_Security)

Yes, I actually have. I just wanted to get some confirmation. I take it by your response that is a confirmation.

However, your link doesn't address the difference in use between sasl and tls.

---

### Post by BkkBonanza on 2009-12-25
Do I really need to say, type SASL into Wikipedia... it tells you about SASL and how it relates to TLS. Wikipedia articles are generally very good. I don't know why you would think my (or some other postetr) confirmation has any meaning at all. They usually have a clear write up on technical things like this.

---

### Post by ooobooontooo on 2009-12-26
> **BkkBonaza said:**
> Do I really need to say, type SASL into Wikipedia... it tells you about SASL and how it relates to TLS. Wikipedia articles are generally very good. I don't know why you would think my (or some other postetr) confirmation has any meaning at all. They usually have a clear write up on technical things like this.

Like I said before, I have done reading on this (this includes the wikipedia page), and like I said before, I'm just looking for some confirmation. I found the wikipedia page a bit too bare for my taste and posted here because I've known a few wikipedia pages to be wrong in the past and because I've always had the responses from the ubuntu forums to be very good in both technical knowledge and in clarity...

Anyway, it seems you're again confirming to what I'm saying. Thanks for your help.

---

