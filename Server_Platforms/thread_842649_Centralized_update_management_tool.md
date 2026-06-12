---
title: "Centralized update management tool"
date: 2008-06-27
forum: Server Platforms
---

### Post by yield999 on 2008-06-27
Hi,

Here is the situation. I have multiple machines that are exactly the same and that does the exact same job's and so on. 

When I want to update them (apt-get update/upgrade) I have to do it one by one by ssh to them then run the apt patch system...

Is there any way to do that one time for all of them. I could test the patch on one of the machines and then deploy once on the other one's...

Regards, 
:guitar:

---

### Post by HalPomeranz on 2008-06-28
You could use a command like fanout, sshmux, or cluster SSH to run the same apt-get commands simultaneously on all of the machines.

You could set up a cron job that runs apt-get at the same time on all the machines.  Maybe have the cron job only fire if you touch a particular file on the system.  That way you get final say on when the apt-get commands run.

You could use an imaging tool like Clonezilla to simply rebuild all of the machines from a standard image whenever you wanted to do an update.

---

