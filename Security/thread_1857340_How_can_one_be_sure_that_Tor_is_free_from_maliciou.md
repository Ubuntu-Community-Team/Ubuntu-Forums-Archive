---
title: "How can one be sure that Tor is free from malicious actions?"
date: 2011-10-10
forum: Security
---

### Post by arroy_0209 on 2011-10-10
There is no doubt that (theoretically) Tor is a powerful program/method to maintain anonymity while browsing net. However it involves bouncing encrypted data from end user (like me) by a number of servers maintained by volunteers worldwide. I would like to know how one can be sure that out of so many volunteers, no one is having bad intentions? Is it not easy for any of them to hack any random computer connected to the net? Or am I missing some crucial point here? 

Another concern I have is that using Tor may give rise to ethical issues since one can use it to anonymously do bad things over internet. Perhaps that is why some governments are not not in favor of using Tor. I would like to get opinions regarding these issues (especially the first one). Thanks.

---

### Post by OpSecShellshock on 2011-10-10
There is no way to know what's going to happen with the traffic ultimately. Once traffic leaves the last node it does so in the clear, and anyone operating the node, anyone on the server side (the destination site), and anyone in between (the ISP of the exit node) has access to it, at least in principle. Whether those parties will do anything you'd be unhappy with is up to them. It's not much different than anything else, in the sense that the privacy and/or security of any information or communications system is going to be determined by the least trustworthy position in the stack. That's life.

Honestly a lot of users undermine what privacy protections are provided by TOR by signing in to services once they're out the other side or even just by allowing scripts to be run.

To answer the second question? Well, the open mic night types might route their malicious activities that way, but the ones who do it for a living are using other people's compromised machines for the most part.

---

### Post by haqking on 2011-10-10
> **arroy_0209 said:**
> There is no doubt that (theoretically) Tor is a powerful program/method to maintain anonymity while browsing net. However it involves bouncing encrypted data from end user (like me) by a number of servers maintained by volunteers worldwide. I would like to know how one can be sure that out of so many volunteers, no one is having bad intentions? Is it not easy for any of them to hack any random computer connected to the net? Or am I missing some crucial point here? 

Another concern I have is that using Tor may give rise to ethical issues since one can use it to anonymously do bad things over internet. Perhaps that is why some governments are not not in favor of using Tor. I would like to get opinions regarding these issues (especially the first one). Thanks.

You trust the post office but no guarantee they wont open your letter ;-)

web of trust, or dont trust them.

---

### Post by Dangertux on 2011-10-10
Simple answer you can't, Tor Endpoints are a huge target. Even if the endpoint owner is legit, there is nothing to say the endpoint itself won't be targeted. 

Tor is a great idea in theory, not as great in practice.

---

### Post by bodhi.zazen on 2011-10-10
> **arroy_0209 said:**
> There is no doubt that (theoretically) Tor is a powerful program/method to maintain anonymity while browsing net. However it involves bouncing encrypted data from end user (like me) by a number of servers maintained by volunteers worldwide. I would like to know how one can be sure that out of so many volunteers, no one is having bad intentions? Is it not easy for any of them to hack any random computer connected to the net? Or am I missing some crucial point here? 

Another concern I have is that using Tor may give rise to ethical issues since one can use it to anonymously do bad things over internet. Perhaps that is why some governments are not not in favor of using Tor. I would like to get opinions regarding these issues (especially the first one). Thanks.

I agree you can not trust TOR for a number of reasons. IMO people are overly reliant on TOR see

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

TOR - a simple solution to a complex problem. If it sounds too good to be true ...

And yes, the other problem with TOR is the inevitable abuse. If you run a server for any length of time you will start to see abuse emanating from TOR exit points, which is then self defeating as people running "legitimate" servers (not just government) then simply black list the exit points.

Think about TOR from a sys admin side of the coin. If you were a bank or site of commercial commerce, would you allow connections from TOR ? And what would you do if you see cracking attempts emanating from a TOR exit node ?

As an admin on the forms, I have had to black list TOR exit nodes to stop spam on these forums for example.

It is a catch 22, how can TOR network police it's own for abuse? 

And if they do not, how can they expect others to trust it's exit points ?

---

### Post by tubbygweilo on 2011-10-11
You may also like to consider information and data that can be extracted from your browser as when coupled with TOR may well lead people to your door. 

[EFF's panopticlick & TOR]("https://blog.torproject.org/blog/effs-panopticlick-and-torbutton") +  [Panopticlick]("http://panopticlick.eff.org/")

---

### Post by marin123 on 2011-10-11
About your first question, it's simple. Use encryption. As much as you can.
Most web pages that need security have https, and even IM clients and torrents support encryption.
That way, you can prevent eavesdropping on your private traffic.
It's still possible to see what websites you are visiting, but if that presents a problem, then don't use Tor.

---

