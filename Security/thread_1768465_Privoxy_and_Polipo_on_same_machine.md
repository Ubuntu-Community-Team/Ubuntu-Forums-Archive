---
title: "Privoxy and Polipo on same machine?"
date: 2011-05-26
forum: Security
---

### Post by TravisFX on 2011-05-26
Hi - a new guy here - and thanks in advance if you can help. :)
Sorry if its a dumb question. I was looking around to try to find a way to possibly setup a caching machine to help with my bandwidth usage - this is a home issue with my family's 3 or 4 pcs in use.
 
Sounds like Privoxy and Polipo will help as a fairly simple and free solution But can they be run on the same box? Or do I need them separated physically on 2 machines?
 
If they can be run on the same, how is that done?
 
Thanks;
TravisFX

---

### Post by bodhi.zazen on 2011-05-26
They can run on the same box, you simply configure them to listen on different ports. You can then chain them together.

You might want too look at squid as squid may be better on a lan as a transparent proxy.

At any rate , here are some links to get you started:

[http://blog.bodhizazen.net/tag/proxy/](http://blog.bodhizazen.net/tag/proxy/)

---

### Post by TravisFX on 2011-05-26
Cool. Starting to get it. From what I read, Polipo sounds like a good choice for caching, and same goes for Privoxy for filtering ads crap etc. They seem simple enuf and I'd like to try it on a free pc I have.
So tell me if I have this about right.
 
Browser > Polipo > Privoxy.  Browser proxy points to Polipo which is then chained to Privoxy. Seems to make sense that priv will filter out incoming first then Pol caches THAT. Better than other way around right?  
Ok so I should probably run a very slim "server" to get max out of the pc. Is that just standard Ubuntu install without running the gui? (how's that done again?.. sorry been a while.)
Or what's up with server ver? Just Ubuntu without gui? Still free? What the diff between the 2.
 
Thanks again.
TravisFX

---

