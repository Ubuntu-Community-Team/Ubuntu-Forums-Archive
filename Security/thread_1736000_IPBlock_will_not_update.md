---
title: "IPBlock will not update"
date: 2011-04-22
forum: Security
---

### Post by FLCL on 2011-04-22
So I was looking for a similar program to PeerBlock on Windows, as most/some might know it's the project that took over after PeerGaurdian halted. 
So I have installed IPBlock and was having issues with updating the lists so i removed them, re-added them and still cannot. 

I can't import lists from URL's either without getting the same error. Kinda seeming like a waste of time right now...

```
ipblock[7147]:error:update of badpeers.gz failed
ipblock[7147]:error:update of level1.gz failed
ipblock[7147]:error:update of level2.gz failed
ipblock[7147]:error:update of Primary failed

```
Etc...any ideas?

---

### Post by ad libitum on 2011-06-11
bump  having the same problem, just installed IPblock on a fresh install of Maverick. when trying to update for the first time, I get the following message:

> ipblock[23111]: error: update of level1.gz failed
ipblock[23111]: error: update of ads-trackers-and-bad-pr0n.gz failed
ipblock[23111]: error: update of edu.gz failed
ipblock[23111]: error: update of spyware.gz failed
ipblock[23111]: error: update of bogon.gz failed
ipblock[23111]: error: update of level2.gz failed
ipblock[23111]: error: update of rangetest.gz failed


---

### Post by ad libitum on 2011-06-27
bump, still no luck! has anyone gotten ipblock to work in ubuntu? how do we enable ipblock to update lists properly?

---

### Post by FLCL on 2011-06-29
Hey, I ended up scrapping IPBlock and went with Moblock, works perfectly. Similar to PeerBlock on Windows. I suggest if you're experiencing the errors I did then to go with Moblock

---

