---
title: "log monitoring"
date: 2008-11-03
forum: Security
---

### Post by LRT on 2008-11-03
anyone have any suggestions on a good log monitoring package... is anyone using "splunk" ??? what's the best one out there?

---

### Post by bodhi.zazen on 2008-11-03
What are you wanting ?

The only one I am familiar with is logwatch

(it is in the repos)

---

### Post by ryanisablond on 2008-11-03
I agree with bodhi.zazen. It depends greatly on what you want/need. 

[Splunk]("http://www.splunk.com/") has very nice command line and graphic interfaces. The free version is especially nice for the price. In my limited experience, it's worked well at our University, fitting well into our Linux environment. It's also cross-platform, so it can install on a XP or a Linux box. The downside is that it can be rather bulky and needs its own dedicated hardware for any semi-serious indexing and archiving. 

[Snare]("http://www.intersectalliance.com/projects/SnareWindows/") and [Kiwi]("http://www.kiwisyslog.com/") are supposed to be pretty good for Windows environments, but I have never used them personally (except using Snare to pipe Win logs over to my Splunk server).

That's the experience of my dabbling in log management. Good luck with yours!

---

### Post by LRT on 2008-11-04
i want something that can help me manage ALL my server logs from one friendly interface. splunk seems to do the trick so far i have been using it for the past 24 hours and already i have become aware of ssh brute force attacks that i was not aware was happening so often!

---

### Post by ryanisablond on 2008-11-07
Glad you found something that's working for you. Hope your experience is all smooth sailing!

---

