---
title: "USP on Edgy"
date: 2006-08-24
forum: Ubuntu System Panel
---

### Post by scav on 2006-08-24
Hi I have USP running on edgy, only problem is  that its taking up to 60% of cpu, even if the i am not in the menu! anybody know whats this about?

---

### Post by pressh on 2006-08-24
You are a lucky guy, mine was eating 97% (also on edgy) :|
It's a shame I had to go back to the original menu bar.

---

### Post by chanders on 2006-08-24
> **pressh said:**
> You are a lucky guy, mine was eating 97% (also on edgy) :|
It's a shame I had to go back to the original menu bar.

I think I might be able to track down the bug. Can you test something for me? Disable the time and USP computer plugins and see if you still have the same results, that would make it easier to track down..

---

### Post by pressh on 2006-08-24
I disabled the USP computer plugin. Not sure what you mean with the time plugin (the time is part of the computer plugin, correct?).
Anyway, the state usp has (with top running in a terminal) you can see on the screenie. Python, hence USP, still eats about 98% of my cpu.
I hope you can track it down, I would love to get this running on edgy without using all my resources :).

thanks

[edit]
the screenie, almost forgotten: 
[[IMG]http://img82.imageshack.us/img82/600/usppz0.th.png[/IMG]](http://img82.imageshack.us/my.php?image=usppz0.png)

---

### Post by dfullers on 2006-08-28
I updated the 100% CPU bug in launchpad with what I have come up with. I will keep working on it to see if I can narrow it down further. Let me know if there is anything I can do to help you find this.

---

### Post by chanders on 2006-08-29
Thanks for your research dfullers! Currently I am still in Venezuela and my download possibilities are somewhat limited.

I should be home in a couple of days, so I will download Knot1 to test then. A USP rewrite is underway so I will try to squash the bug in its infancy in preparation for Edgy's release (or sooner).

Chanders

---

### Post by samoht on 2006-08-29
Same issue here. :( 
I'm already so used to USP that I don't want to get back to the old menu...
Tell me if i can help you with testing/debugging.

Greetings,
Thomas

---

### Post by mat on 2006-08-29
I switched my laptop to edgy to investigate this. I'll try to debug it tomorrow.

---

### Post by scav on 2006-09-08
seems like the problem is gone with todays edgy updates.. at least my usp didnt go frenzy after  the updates today

---

### Post by PWill on 2006-09-09
confirmed, scav. it stopped using 100% CPU about 3 days ago for me after an update.

---

### Post by mat on 2006-09-09
And I was wondering why I couldn't reproduce the bug at all...

---

### Post by chanders on 2006-09-10
Thank goodness! I am about to run USP beta2 on my machine for testing and was dreading having to rewrite for edgy!

---

### Post by dfullers on 2006-09-11
I can confirm this as well. The CPU usage is fixed for both AMD64 and 386. I had suspected this was a bug in upsteam for a while which is why I quit working on it.

---

