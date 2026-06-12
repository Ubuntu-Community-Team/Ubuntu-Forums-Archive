---
title: "Automatically rolling security keys?"
date: 2014-04-10
forum: Security
---

### Post by pcman312 on 2014-04-10
I am building a chat application (for fun and learning) and I was wondering how useful is it to regenerate RSA/AES/etc. security keys automatically during runtime? I'm envisioning something where a new RSA/AES key is generated for both clients and server(s) at arbitrary intervals (every hour or whatnot, assuming the conversation lasts that long). If it is not useful, why not? Are there similar solutions that would be better?

---

### Post by ant2ne on 2014-04-10
Why?

---

### Post by open2reason on 2014-04-10
For your own education then fine, but please be sure to point this out to all who join you and chat with you using your hand rolled solution.

---

### Post by ant2ne on 2014-04-10
Why? What would be the point of rekeying so frequently?

---

### Post by pcman312 on 2014-04-10
> **ant2ne said:**
> Why?

[LIST]
[*]To use a different sized key. The keys in my design will be created at runtime and never stored on disk, so during startup a smaller RSA key would be created in the interest of latency for the user, then replaced with a larger key.
[*]To enact a form of forward secrecy (according to my admittedly limited understanding of it). If a given chat is kept open for a long time, it would effectively be the same 'session' for a long time, but if the keys are rolled every X timeframe, it would split it into multiple sessions.
[/LIST]

My biggest question is whether this is useful or not. The idea is I create an arbitrarily sized RSA key (say 2048, which takes about half a second to generate in Java) to transfer an arbitrarily sized AES key (say 256 bit). Then asynchronously I generate a much larger RSA key (say 8096, which takes about 90 seconds to generate) to transfer a new arbitrarily large AES key so the user isn't sitting there waiting for the key to be generated. Then regenerate both RSA and AES keys every arbitrary timeframe (every 30 minutes, every hour, etc.), would this timed regeneration provide any worthwhile security over the data in flight?

---

### Post by pcman312 on 2014-04-10
> **open2reason said:**
> For your own education then fine, but please be sure to point this out to all who join you and chat with you using your hand rolled solution.

Well, this is a totally self-contained chat program, so the changing of the keys would be made invisible to the user.

---

### Post by pcman312 on 2014-04-11
If this doesn't provide any valuable security benefits, I want to know that too. Feel free to pick apart and/or destroy the idea.

---

