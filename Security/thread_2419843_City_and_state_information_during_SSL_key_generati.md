---
title: "City and state information during SSL key generation"
date: 2019-05-26
forum: Security
---

### Post by sandman887 on 2019-05-26
I want to generate an SSL key for a site of mine. But during the process, I don't know if I should enter my personal city and state, or the city and state where the physical server of the web hosting company is. Which one should I use, the physical location of the server, or where I live?

Thanks!

---

### Post by TheFu on 2019-05-26
It doesn't matter at all.  I lie.

---

### Post by sandman887 on 2019-06-05
Is it illegal to lie on those?

---

### Post by SeijiSensei on 2019-06-05
No.  Still I use the name/address of my place of business, these days my home.  I've had registrations since the mid-1990s without many consequences other than annoying emails telling me (incorrectly) that I need to renew my registration, usually for outlandish fees like $80+ per year.  Right now I pay $15 at directnic.com.  There are cheaper options, but directnic has been very reliable and provides excellent support.

---

### Post by 1clue on 2019-06-05
If you're getting something from a recognized trusted certificate authority (e.g. VeriSign, GlobalProtect), then it should be where your business license is for your company. If you're a multi-site organization (warm bodies in more than one place) then it could get more complicated, but if you have a main office I would use that.

Those organizations verify that the person ordering the certificate is actually working for the company the certificate is for, and that the company actually exists and is a real business. They'll look at your web site, they'll make sure a business license exists and is current for that address, they'll make you change something on the website according to their specification to prove you control the website. The more "trusted" the certificate authority, the more expensive their certificates and, by design, the more of a PITA getting a certificate is. That extra money is spent researching you.

While some of them don't seem to examine the parameters you put in on your CSR I imagine that some might.

---

### Post by TheFu on 2019-06-05
> **sandman887 said:**
> Is it illegal to lie on those?

If this is for a business, then I'd only provide sufficient truth so the responsible company could be found easily.  I will NOT enter a data center address, ever. I'd put the business address, as stated on the INC or LLC documents registered with the govt.  That info is already leaked.  Leaking DC locations for private entities is asking for trouble if they don't have high security with multiple on-site guards inside and outside the DC.

When I initially read the post, I assumed it was for a self-signed cert that might be placed on the internet. For those, intended for personal use, lie, lie, lie.

If you use Let's Encrypt certs, I don't think they even request any location information ... let me check ... nope.  

When I'm trying to find a responsible company over network abuse, I tend to use DNS contacts, but now that those are mostly hidden, I suppose the certs would be my next place to check.  The most likely use for any of this information is by someone who found a security flaw and wants to let you know about it, not some bad-actor.  At least in my experience.

---

### Post by kevdog on 2019-06-11
I don't think its required at all for a certificate generation -- well let me clarify.  I've only obtained certs through LetsEncrypt and they don't require this information.  Perhaps other companies require the information -- i'm not sure.  I know if you generate self-signed certs you could skip this field and the cert can be recognized.

---

### Post by 1clue on 2019-06-11
Those fields are encrypted into the certificate for a reason. While you may technically not be required to fill out the information, doing so reduces the value of your certificate because doing so decreases the certainty that the site owner/operator is actually the party you think you're doing business with.

The entire point of these certificates is to establish trust and secure communications with a KNOWN entity.

With that in mind, it seems pretty obvious to me that the certificate should reflect what's on the business license of the entity being represented.

---

