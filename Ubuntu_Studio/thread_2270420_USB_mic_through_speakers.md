---
title: "USB mic through speakers"
date: 2015-03-22
forum: Ubuntu Studio
---

### Post by burges80 on 2015-03-22
I installed Ubuntu Studio hoping to be able to hear sound through my USB Mic straight to my speakers hooked up to an optical cable out.  I am able to record sound in Audacity and play it fine, just can't figure out how to make it live.  I looked in JACK and don't have a Pulse Audio listing as some sites suggest should I should have.  I was able to get it to work in normal Ubuntu, but with quite a bit of latency and a little static. Is there a specific program on Ubuntu Studio that makes this easy?

---

### Post by jejeman on 2015-04-04
You are dealing with two sound cards here. It is possible what you want, but not recommended.
In JACK choose Mic's card as input, and on board card as output.

---

