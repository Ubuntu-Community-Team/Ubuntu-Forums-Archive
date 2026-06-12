---
title: "security update notifications and security vs. function updates"
date: 2006-08-09
forum: Server Platforms
---

### Post by opensensesolutions on 2006-08-09
As an Ubuntu solution provider, we rely on the stability of Ubuntu.  When a package is updated for security, we must re-verify that that package did not break anything in our systems.  We get security notifications, but those come out after the packages are in the repositories.  At that point people have possibly already upgraded and broken their systems.

So, how can we be notified as soon as a new package is being worked on by the Ubuntu maintaners, so we can schedule testing and be ready for the change? 
  
Some people might tell us to always run a server that constantly looks for updates to Ubuntu packages and sends out an email to interested parties, but really that is too late.  For example, when a kernel version changes, we need to recompile and package up modules like lirc, and have the updates ready at the same time as the new kernel version package is released if we don't want to break the customer.  So how can we get notice as soon as possible in advance that there will be a new security package released?

---

### Post by LordHunter317 on 2006-08-10
The right solution is to use a proxy like approx and force all your customer's updates through that so you can control what they update and when.

---

### Post by opensensesolutions on 2006-08-10
Thanks LordHunter317, that is part of the solution.  We have looked at mirroring the Ubuntu repositories before, approx may be the most efficient way, thanks for bringing it to our attention.  However, that still leaves a critical delay in the process.

Once a new security package is released, we will have to scramble to verify it and get it into our proxy.  With this approach, our customers might not see critical security fixes until a day after the fix is released in the Ubuntu repository.

If we could simply be notified that new security fixes were being worked on, we could be ready and have the fix verified and released to our proxy repository within an hour of when the package is released.  

I'm sure some sort of "we're working on this package" notification system would be useful to other people such as sysadmins and Ubuntu maintainers.  It could also be useful for other repositories such as ubuntu-updates or backports.
Who would I lobby to make this happen, the Ubuntu security team?

---

### Post by LordHunter317 on 2006-08-10
> **opensensesolutions said:**
>  However, that still leaves a critical delay in the process.Verification requires delay.  That's the end of the story.  No solution is going to let you always audit packages and just let them through instanteously.

> If we could simply be notified that new security fixes were being worked on,You'll have to bug Canonical for that.

> I'm sure some sort of "we're working on this package" notification system would be useful to other people such as sysadmins and Ubuntu maintainers.Not really.  If there's a live 0-day exploit out there before the patch hits the mirrors, either you're prepared to handle it or you're already dead. 

While I'm not advocating leaving machiens unpatched or anything of the sort, the time window to patch is normally on the order of days (say, a week), or on the order of, "Needed to patch before the patch exists".

---

