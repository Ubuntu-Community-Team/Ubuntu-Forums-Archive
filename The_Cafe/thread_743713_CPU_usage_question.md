---
title: "CPU usage question"
date: 2008-04-02
forum: The Cafe
---

### Post by red_five on 2008-04-02
Howdy, folks. I've got a net-boot frontend for MythTV, and I have it configured to automatically shut down at a certain time every day (to save power and such). However, I only want it to happen if the system is idle, i.e. not watching anything or in a Skype call. I'm thinking I should put in a system load check of some sort, and if CPU load is above a certain level, don't shut down.

Now, I can check if Skype is running, and block the shutdown if it is. But MythTV runs only one process regardless of whether it's idle, or it's playing a video or DVD, so I can't use that. Is the system load counter displayed from the uptime command updated rapidly enough to use in this case, or should I look at another system metric?

---

### Post by erginemr on 2008-04-03
Out of curiosity, how do you check the existence of a process (say Skype) before shutting down the system? And are you using cron for the job?

---

### Post by red_five on 2008-04-03
I am using cron for the shutdown job, and right now, there is no checking; the cron job just runs /sbin/poweroff. So if I'm watching something and 10pm rolls around (Ideally, though, the house would be preparing for bed), it just ends.

Checking for Skype would be easy; a simple pgrep skype is sufficient. But like I mentioned, MythTV doesn't seem to run any extra processes when watching something, either recorded TV or ripped DVDs using the internal player. So that part's a bit of an unknown.

---

