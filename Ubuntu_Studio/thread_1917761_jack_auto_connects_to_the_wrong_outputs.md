---
title: "jack auto connects to the wrong outputs"
date: 2012-01-30
forum: Ubuntu Studio
---

### Post by youWho on 2012-01-30
Hi all. A quick question, but a frustrating issue: whenever I start qjackctl and some audio apps they are automatically connected in the qjackctl "Connect" dialog to the "system" outputs in the "Audio" tab, except that they are always automatically patched to outputs 1 and 2, and equally consistantly sound actually comes out of the speakers only when I connect to outputs 3 and 4. I've searched quite a bit but perhaps it's one of those that's hard to define the right keywords for; in any case I never get any useful results. Does anybody happen to know how to get jact to automacticaly connect to 3 and 4 instead?? Or to redefine the outputs such that 1 and 2 are the right ones? I spend a lot of time just manually disconnecting all those and reconnecting, etc. Thanks in advance.

Ubuntu studio natty 64 bit, on a laptop.

---

### Post by jejeman on 2012-01-30
What happens if you set just two channels for playback?

---

### Post by youWho on 2012-01-31
> **jejeman said:**
> What happens if you set just two channels for playback?

Thanks.

But how would I do that? In Qjackctl somewhere (I don't know where that would be tho) or somehow else??

---

### Post by jejeman on 2012-01-31
for output channels select 2
[IMG]http://qjackctl.sourceforge.net/image/qjackctlSetupForm1.png[/IMG]

---

### Post by youWho on 2012-02-01
Ah. Of course. Somehow I missed that. *And* it works! Thanks!!

---

