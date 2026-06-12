---
title: "Real-time graphs ?"
date: 2009-01-05
forum: The Cafe
---

### Post by ProgramErgoSum on 2009-01-05
Is there a package to get real-time, streaming graphs in a web-page ? Something similar to the plots of CPU utilization. After some Googling, I came across [luagraph]("http://luagraph.luaforge.net/"). **But, my Firefox immediately stops responding once the link is clicked !** So, I haven't been able to explore it more. I do see one in Synaptic Manager though not with that exact name. Plus, there were some s/w available which was dedicated to network bandwidth utilisation, network traffic, stock analysis, etc. Whereas, I am looking for something that is not tied with a particular 'industry'. 

So, would you know of such a s/w ?

---

### Post by amauk on 2009-01-05
Munin

Example
[http://mayday.indymedia.org/munin/indymedia.org/chavez.indymedia.org.html](http://mayday.indymedia.org/munin/indymedia.org/chavez.indymedia.org.html)

---

### Post by ProgramErgoSum on 2009-01-05
Munin looks interesting, thanks.

As described in its page, it has been designed for monitoring computers. Whereas, I want to be able to send input generated in some other way (say, rise and fall of temperature as recorded in a lab, etc.) that is then displayed as a 'streaming graph'. Perhaps, Munin source can be hacked accordingly. I will have to check it out.

---

### Post by amauk on 2009-01-05
oh, sorry
misunderstood what you wanted

Munin uses RRDtool to generate the graphs from flat files
[http://en.wikipedia.org/wiki/RRDtool](http://en.wikipedia.org/wiki/RRDtool)

you may want to look into this, and see if you can use it to graph your own data

---

