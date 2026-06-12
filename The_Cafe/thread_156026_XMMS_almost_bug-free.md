---
title: "XMMS almost bug-free"
date: 2006-04-06
forum: The Cafe
---

### Post by openmind on 2006-04-06
Interesting article about a massive Bug-Hunt;

[http://news.zdnet.com/2100-1009_22-6057669.html?tag=nl.e550]("http://news.zdnet.com/2100-1009_22-6057669.html?tag=nl.e550")


> Amanda, a backup tool, was the worst performer in Coverity's first analysis. It had the highest number of bugs per 1,000 lines of code, with a bug density of 1.237. The Amanda developers fixed 108 defects in a couple of weeks, according to Coverity.  XMMS, an audio player, had the lowest bug density, with 0.051 defects per 1,000 lines of code. A total of six holes have now been fixed, Coverity said. 


---

### Post by BoyOfDestiny on 2006-04-06
> **openmind]Interesting article about a massive Bug-Hunt said:**
> http://news.zdnet.com/2100-1009_22-6057669.html?tag=nl.e550[/URL]

Pretty cool.

---

### Post by paul cooke on 2006-04-06
as far as I know, it only finds buffer overruns and other security flaws... it doesn't actually find logic errors in the code, those such as having != instead of == or a variable being incorrectly initialised... those you have to hunt down the hard way by discovering unexpected or incorrect behaviour and then sticking breakpoints in at the appropriate paces or by inspection of the code against the requirements spec... 

I fixed six bugs today where my software engineer hadn't quite read my spec correctly and had logic errors (a != had been used instead of a == and thus a chunk of code wasn't being executed) or typos (the wrong variable had been used, but because the variable existed, no error was flagged up in compilation.) or I'd had a typo in my spec itself that I'd not seen or my reviewer hadn't picked up or my softie hadn't picked up on either... so he'd coded to the spec... ;)

---

### Post by Ubunted on 2006-04-06
[QUOTE=paul cooke]as far as I know, it only finds buffer overruns and other security flaws... it doesn't actually find logic errors in the code, those such as having != instead of == or a variable being incorrectly initialised... those you have to hunt down the hard way by discovering unexpected or incorrect behaviour and then sticking breakpoints in at the appropriate paces or by inspection of the code against the requirements spec... 

I fixed six bugs today where my software engineer hadn't quite read my spec correctly and had logic errors (a != had been used instead of a == and thus a chunk of code wasn't being executed) or typos (the wrong variable had been used, but because the variable existed, no error was flagged up in compilation.) or I'd had a typo in my spec itself that I'd not seen or my reviewer hadn't picked up or my softie hadn't picked up on either... so he'd coded to the spec... ;)[/QUOTE]

It's talk like that that makes me immensly glad I went into Networking and not Programming. I feel like my head's about to pop.

---

### Post by htinn on 2006-04-06
Can you say "unit testing"?

---

### Post by paul cooke on 2006-04-06
[QUOTE=htinn]Can you say "unit testing"?[/QUOTE]

we produce training systems that emulate all the systems on an aircraft. 

It's impossible to unit test every single module as the entire thing only behaves correctly when fully integrated. We do pre-integration testing of systems using test harnesses to handle the system boundaries. Then when the systems are behaving according to whatever verification instructions we've given our test team, things get integrated. 

At this point, we then attempt to carry out the maintenance procedures that the trainees have to do (both without and with emulated faults such as open circuits in the virtual circuits). Sometimes, it's only at this point that things start to show up, usually because our source data is wrong. Things such as the maintenance procedures we've been given haven't themselves been verified against the real aircraft (so the instructions or results are wrong) or there's been a mistake in a circuit diagram and the manufacturer didn't think to let us know, or even in my own system the source data has been changed subsequently because the real thing was behaving incorrectly in exactly the same way my system was misbehaving.

We are only a small team, five analysts, five software engineers, two graphic artists and two testers... It's amazing what we do produce in the limited time the customer gives us to do it in... especially as they are so tardy in giving us correct data on time. I'm still waiting for photographs and video of two test sets in action that I'm expected to emulate... the manufacturers manuals for them are very lacking in detail.

---

### Post by K.Mandla on 2006-04-06
No matter how you look at it, though, the Samba crowd must've been drinking a lot of Mountain Dew to move that fast. ;)

---

### Post by openmind on 2006-04-06
[quote=Ubunted]It's talk like that that makes me immensly glad I went into Networking and not Programming. I feel like my head's about to pop.[/quote]

I felt the same way after reading Paul's post! I just didn't want to say anything!;)

---

### Post by htinn on 2006-04-06
[QUOTE=paul cooke]We are only a small team, five analysts, five software engineers, two graphic artists and two testers... It's amazing what we do produce in the limited time the customer gives us to do it in... especially as they are so tardy in giving us correct data on time. I'm still waiting for photographs and video of two test sets in action that I'm expected to emulate... the manufacturers manuals for them are very lacking in detail.[/QUOTE]

Wow, you guys got it rough. I don't think I could do programming like that.

One of the great virtues of a nice, casual, open-source project is that you can take your time and do code whenever you feel like. No dead lines. :-D

---

