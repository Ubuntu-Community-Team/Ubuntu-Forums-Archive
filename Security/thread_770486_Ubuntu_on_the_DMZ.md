---
title: "Ubuntu on the DMZ"
date: 2008-04-27
forum: Security
---

### Post by MCAccord on 2008-04-27
Hey everyone, I just upgrade to Ubuntu 8 yesterday, and so far I'm quite impressed. Anyways, I'm wondering about putting my Ubuntu box on the DMZ of my network, I've experimented with it, and it seems to work pretty good. However, I don't know how to secure the system. I run a MythTV box, and I'd like to be able to do throw up a web page on that box, as well as Myth has some web services for scheduling and such. Do I run any risks by just throwing my box out in the DMZ? I would never do this with a Windows system, but Linux seems to be more secure. Basically I guess the question is, what do I have to do to be able to have the convenience of scheduling TV programs remotely over the internet, without being hacked and my box being torn apart?
Thanks!

---

### Post by Monicker on 2008-04-27
Any box can be hacked.  It just depends on what services are exposed, and how well those services have been secured.  I would start with the sticky on security in this forum.

One gotcha specific to Mythtv - Make sure you use some type of authentication to view the web page if you are using MythWeb, and that service is available to anyone.  People have had all of their recordings deleted before, because the google search spider will actually traverse the Delete links and trigger them.  :)

---

### Post by MCAccord on 2008-04-27
Cool, thanks for the heads up.

---

