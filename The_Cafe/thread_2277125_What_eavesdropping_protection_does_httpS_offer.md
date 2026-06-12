---
title: "What eavesdropping protection does httpS offer?"
date: 2015-05-06
forum: The Cafe
---

### Post by triciasurfer on 2015-05-06
What eavesdropping protection do you have when surfing the  http**S** (secure) version of a website (e.g. https://facebook.com, https://gmail.com) ? 

  What types of information is not protected? (I'm guessing that the website URLs are public? 
What else would be public?)  And what type of information is protected? (I'm assuming username and password are kept secret.) 


 I'm speaking about people in the following positions: 
1) ISP 
2) Owner/administrator of a  wireless network router

---

### Post by grahammechanical on 2015-05-06
Read about it

[http://en.wikipedia.org/wiki/HTTPS](http://en.wikipedia.org/wiki/HTTPS)

---

### Post by Lars Noodén on 2015-05-07
Those who control either the first router in the loop or control your DNS lookups, which is usually your ISP, can do a lot.

For example, because of the inherent shortcomings in how browsers manage certificates, doing your own redirect in any of those cases is trivial:
[http://www.mouedine.net/relayd/](http://www.mouedine.net/relayd/)

That example simply redirects to a warning page but is one or two steps away from real trouble.  So if you are designing a service to run over HTTPS, count TLS as no more than just one layer of the many others needed.

---

### Post by WinEunuchs2Unix on 2015-05-11
If you have something to say that other people would want to spy on then don`t say it especially if it contains the letters S, E or X.

If you think people are spying on you because you are important and you might be set up for any slip of the tongue then need not worry because you are not GOD.

How much time are we collectively wasting over fear of being spied uponÉ

---

### Post by wewantutopia on 2015-05-12
> **WinEunuchs2Unix said:**
> If you have something to say that other people would want to spy on then don`t say it especially if it contains the letters S, E or X.

If you think people are spying on you because you are important and you might be set up for any slip of the tongue then need not worry because you are not GOD.

How much time are we collectively wasting over fear of being spied uponÉ

Yes, let us all welcome our future Orwellian overlords with open arms...

---

