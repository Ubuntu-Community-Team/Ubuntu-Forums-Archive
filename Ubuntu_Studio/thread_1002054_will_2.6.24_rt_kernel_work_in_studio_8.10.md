---
title: "will 2.6.24 rt kernel work in studio 8.10"
date: 2008-12-04
forum: Ubuntu Studio
---

### Post by johnapeterson on 2008-12-04
Hello,
This might be a stupid question:oops:, but as I like to think, the only stupid question is the one that is not asked.

Anyway, I have upgraded to ubuntu studio 8.10, I know that there are some problems with the new realtime kernel, but is it possible for the 2.6.24 rt kernel to run the 8.10 op?

Thanks,
John

---

### Post by raboofje on 2008-12-04
> **johnapeterson said:**
> I have upgraded to ubuntu studio 8.10, I know that there are some problems with the new realtime kernel, but is it possible for the 2.6.24 rt kernel to run the 8.10 op?

Sort of: it should mostly work, but some things might break (for example, when using the 2.6.24 rt kernel on 8.10, suspending the machine breaks networking for me).

---

### Post by Stochastic on 2008-12-04
I'd recommend against this unless you're seasoned enough to be able to fix issues from the command line, hold back disagreeable drivers via apt, and generally maintain your box without logging into X.  Not that those skills will be required, but rather that that general level of competence with system maintenance should be there before you begin to purposefully mismatch system parts.

I'm running the 2.6.27-rt kernel in 8.10 and find it to work fine - there are a few more xruns than in 8.04, but I've been working around that.  I only have one core to my processor so the shutdown issue is the only bug I run into.

I would personally expect more issues running a 2.6.24-rt kernel in 8.10 than a 2.6.27-rt kernel.  Though I'm no kernel expert - have never even built my own.

---

