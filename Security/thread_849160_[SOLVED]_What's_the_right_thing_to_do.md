---
title: "[SOLVED] What's the right thing to do?"
date: 2008-07-04
forum: Security
---

### Post by ene_dene on 2008-07-04
I've recently checked auth.log file and saw that lot of people try to ssh in to my computer. I went to check IP addresses and usually it is from some company with a nice website, you would never think that they would do that intentionally. As I understand there are two possibilities:
1. some employee is trying to do something that he should not
2. they have a breach in security, someone is using their computers to do nasty work.
So what is the right thing to do? Should I email them and paste part of a log file, do I have to check some more before accusing them or should I just leave it alone?

---

### Post by hyper_ch on 2008-07-04
install denyhosts or fail2ban and then auto-blacklist IP addresses that try to connect with false credentials in a too short timeframe...

You can send them an email/notice that there are countless connection attempts by ssh from their network and that they should cease & desist doing so.

---

### Post by ene_dene on 2008-07-04
> **hyper_ch said:**
> install denyhosts or fail2ban and then auto-blacklist IP addresses that try to connect with false credentials in a too short timeframe...

You can send them an email/notice that there are countless connection attempts by ssh from their network and that they should cease & desist doing so.
Thanks I do have fail2ban installed, and it bans their addresses but I wanted to know is it customary to report the accident.

---

### Post by lisati on 2008-07-04
> **ene_dene said:**
> Thanks I do have fail2ban installed, and it bans their addresses but I wanted to know is it customary to report the accident.

It is possible that what you're experiencing probably breaches some terms and conditions somewhere, and respectable companies would probably appreciate reports of abuse of their system.

---

### Post by kevmitch on 2008-09-18
The ip addresses have probably been spoofed. The actual owners of the addresses in question are likely not associated and there's probably not much they can do.

---

