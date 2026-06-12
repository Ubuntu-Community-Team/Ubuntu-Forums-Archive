---
title: "Ubuntu Server 10.10 DNS Tutorial"
date: 2011-03-08
forum: Server Platforms
---

### Post by UndeadCircus on 2011-03-08
Hey all,
 
I'm so sorry if this has been posted before, but I am a COMPLETE newb when it comes to managing my own server. I usually purchase reseller hosting from a vendor and just monitor everything using cPanel and WHM. Well, I'm at a crossroads with my host and things just seem like they would get so much better if I could, in fact, run my own server from my cable connection at home. Nothing too extravagent, but something that works.
 
ANYWAY. I have been able to follow all tutorials and setup Apache2, PHP5 and MySQL along with phpMyAdmin with no problems. I even got so far as to setup ISPConfig3 and it seemed to work just fine. This is the issue I'm having.
 
I have the domain mediaqore.com registered at GoDaddy and I would love for that domain to point to my home server so that people can go to mediaqore.com and they get my server at home. In addition to that, I'd like to set it up so that I have ns1.mediaqore.com and ns2.mediaqore.com so that I can setup a couple extra side-projects and have their domain nameservers point to ns1 and ns2.mediaqore.com and also have those reside on my home server.
 
I can continue talking until I'm blue in the face about how big of a noob I am when it comes to setting up this kind of stuff, but I'd rather spend my time reading through the forums here for different solutions (which to this point, I've found none, at least I don't think I have.)
 
So anyway. Can any of you fine folks point me in the right direction? I would prefer a walkthrough/tutorial that is setting everything up on Ubuntu Server 10.10. I found some old tutorials but they're for <=7.0 of Ubuntu Server...which I don't think are going to help me much at all.
 
Thanks everyone!
Ricky

---

### Post by hictio on 2011-03-08
Have you read this one? [Ubuntu Server Guide (10.10)](https://help.ubuntu.com/10.10/serverguide/C/), specifically the [DNS setup chapter](https://help.ubuntu.com/10.10/serverguide/C/dns.html)?
Setting up an authorative DNS server is not that hard, just make sure you read the tutorials, and grab the concept, which is not that hard, a Master and a couple of Slaves to simplify administration and prevent downtime.
On Godaddy all you have to do is, if you are going to host your own DNS server, point those to the server that will do so, and wait till it propagates.

---

