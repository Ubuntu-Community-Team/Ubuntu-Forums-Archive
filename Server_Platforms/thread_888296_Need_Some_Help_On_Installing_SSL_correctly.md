---
title: "Need Some Help On Installing SSL correctly"
date: 2008-08-13
forum: Server Platforms
---

### Post by kustomjs on 2008-08-13
Hey Guys
I need some help on installing SSL correctly onto my ubuntu 8.04 server and I am using webmin as my gui so I just need some help on installing the ssl correctly onto my server.

---

### Post by kustomjs on 2008-08-13
~bump back on top~

---

### Post by sndnichols on 2008-08-13
sudo apt-get install ssh openssh-server.

---

### Post by MJN on 2008-08-13
SSH is not the same as SSL.

Kustomjs, you may get more help if you elaborate on your question a bit more - specifically what you are trying to achieve and what you have tried so far (presumably you've searched both here and on the web for guidance?).

Mathew

---

### Post by gishaust on 2008-08-13
if your are looking to install ssl for the use on webmin I found this howto
```

http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html

```

---

### Post by kustomjs on 2008-08-13
I tried to do ssl through webmin it doesn't work what I am trying to do is I am hosting 3 different sites on my server and it needs SSL for checkout.

---

### Post by gishaust on 2008-08-13
so is the ssl for an online shop that is going to talk to paypal or something like that?

---

### Post by kustomjs on 2008-08-14
alright gishaust please do not reply to my post ever again you dont know what I am talking about here so here what I am talking about I am using oscommerce shopping cart I need to install SSL to make my site secure because I am storing personal data so I need to get my ssl installed correctly on to my server.

---

### Post by MJN on 2008-08-14
With that atitude kustomjs I'd be surprised if anyone will reply to your post again. I think gishaust was trying to help.

Good luck,

Mathew

---

### Post by sndnichols on 2008-08-14
> SSH is not the same as SSL.


Maybe I should get my glasses checked.

---

### Post by ByteJuggler on 2008-08-14
Google turns up this page [here]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html"), which explains how to install an SSL certificate on Apache housed on Ubuntu and also contains a link should you need to create a self-signed certificate.  I think that should solve your problem  If not, post back.  (And try to be polite.  None of us are paid for being here, the only payback we receive is the satisfaction of being thanked and helping other people.  If people are rude then that largely removes the incentive for being helpful in the first place.)

---

### Post by kustomjs on 2008-08-14
I already tried that site you linked over it didnt work and the reason why I posted what I said on my last post because he didnt know what he was even talking about or anything so I had the rights to be rude just FYI read what my post said before replying with stupid off topic post.

---

### Post by MJN on 2008-08-14
Kustomjs, come on do please try to be a bit more civil. Far be it for me to tell you how to behave but do let me point out that people on here will be far more likely to take the time and effort to help you out if you show a little more appreciation for their efforts.

We all know how frustrating it can be when you're trying to solve a problem, and it can be exasperating when a call for help is not immediately forthcoming with an answer. But give us a break - we may all disagree from time to time and not see eye to eye but we're all here for the same reason and that's to help and learn off each other. That's surely only going to work if we show a little respect. If one of us gives a duff answer then so be it, but we're at least trying! Just point it out and move on!

Now, back to your problem, introducing SSL to Apache is not a one-step process and so what we're really looking at is finding you a guide to walk you through the steps. There really is little point in somebody doing that for everyone that asks the question if such information is already out there. ByteJuggler's suggested link certainly looks like a good one so can you elaborate on where it failed and/or in what way etc?

I'm not challenging you, just asking you to help us to help you. We can't say fairer than that can we?

Mathew

---

