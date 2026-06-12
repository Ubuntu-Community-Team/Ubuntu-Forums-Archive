---
title: "unity8-desktop-session-x11 borks system"
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-02-27
I opened proposed, updated and installed the x11 session of unity:

```

sudo apt-get install unity8-desktop-session-x11


```

and it borked my system.  I can get CLI but nothing else with the exception of low graphics through recovery mode.

---

### Post by ventrical on 2014-02-27
Fresh installed as I had to upgrade to amd64 bit anyways.

---

### Post by rrnbtter on 2014-02-28
Greetings, 
I did a clean install on my alternate HD using daily iso Feb 27. It won't give me a login option. I used several methods. 
sudo apt-get install unity8-desktop-session-mir - Produced nothing.
sudo apt-get install unity8-desktop-session-x11 - Produced nothing.

There are other options available including building from scratch. 
I may give those a try when I get a chance. My take is that it only 
works on select chipsets. I have a Intel Mobile 4 i915.

---

### Post by grahammechanical on 2014-02-28
Did you have the proposed repository enabled? Sorry, if it so obvious.

On my system I get the login option but it goes to a black frozen screen requiring a hard shutdown. Using Nvidia GT220 and Nouveau. I suspect that it will break with proprietary video drivers. But it should work with Nouveau.

---

### Post by rrnbtter on 2014-02-28
Greetings,
@grahammechanical - Definitely have proposed enabled. I also have the dependency PPA's installed. I think I will just wait for this to mature a bit more. But Thanks!

---

### Post by xc3RnbFO8P on 2014-02-28
@ventrical 
do you have the same version (see screenshot)

[[img]http://farm3.staticflickr.com/2814/12844549043_54e09e25b3_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12844549043/)
[Screenshot from 2014-02-28 21:59:52](http://www.flickr.com/photos/96052779@N07/12844549043/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by ventrical on 2014-03-01
I removed it for now. I'll get back testing it later. btw .. I was talking about the x11 session , not the mir session.

---

### Post by xc3RnbFO8P on 2014-03-01
> **ventrical said:**
> I removed it for now. I'll get back testing it later. btw .. I was talking about the x11 session , not the mir session.

I need glasses :)

---

### Post by ventrical on 2014-03-01
> **Ringi said:**
> I need glasses :)


Me too :) New ones.

---

