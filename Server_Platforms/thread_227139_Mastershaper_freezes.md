---
title: "Mastershaper freezes"
date: 2006-08-01
forum: Server Platforms
---

### Post by dixon on 2006-08-01
I've just installed mastershaper. Everything works except for one thing. When I load ruleset It freezes. 

Has anybody solved this?

---

### Post by Mithrilhall on 2006-08-04
You didn't apt-get this did you?

I just installed it on Kubuntu and I'm configuring it now.

---

### Post by dixon on 2006-08-08
I haven't found it in repository. There may be some problem with sudoers, but I don't know how to solve that...

---

### Post by Mithrilhall on 2006-08-10
I'm having the same problem. It's freezing whenever I click "Load Ruleset" or "Unload Ruleset".



Any solution? :confused:

---

### Post by Mithrilhall on 2006-08-11
Ok...this is what I've found so far.

I start tc_collector.pl like so:

> sudo tc_collector.pl -v3


Now it just displays over and over....

> 
Fri Aug 11 10:59:45 2006: Storing tc statistics now.
Fri Aug 11 10:56:45 2006: No data available for statistics. tc rules loaded?
Fri Aug 11 10:56:55 2006: Storing tc statistics now.

I'm not sure why it keeps displaying this message though.

---

### Post by Mithrilhall on 2006-08-11
Okay..I got it working now. I'll post what I had to do once I get home tonight.

If I have time I'll write up a How-To and/or a script to install it.

:KS

---

### Post by robertjamesdavies on 2008-02-04
Hey,

I've currently got the same issue. Did you ever write the guide?

---

