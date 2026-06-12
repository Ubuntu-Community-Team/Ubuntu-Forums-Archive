---
title: "Problem with Postfix, many spawned instances, then freezes"
date: 2009-02-23
forum: Server Platforms
---

### Post by AbeyMarquez on 2009-02-23
Hi,

I have Ubuntu Server 8.04.2 completely up-to-date running in an esx vm. I configured the box as an anti-spam gateway using MailScanner with Postfix. This problem has happened ever since I created/configured the server.

The problem I'm having is that every few days (this is very random, sometimes 1 day and sometimes two weeks) the OS becomes unresponsive. Mail doesn't get through, apache won't respond, the cpu usage is through the roof. Sometimes I can manage to log in and run commands but sometimes I can't. When I've been able to run **ps -A** I can see that there's tens of instances (50+) of **smtpd**, **spawn**, and **perl** even though I've set the max postfix instances to be 5 per cpu (I have 2 virtual CPUs on this box) in the MailScanner config file. There's no way I can tell when this is happening until a user lets me know they haven't received mail during the day. I've also checked all logs that have to do with mail or system errors but I haven't been able to see anything that would help.

Please let me know if you have any idea what could be causing this problem and if there's any logs or specs that I need to post.

Thanks!

-Abey

---

### Post by AbeyMarquez on 2009-02-26
anyone?

---

### Post by E_K on 2009-02-26
install logwatch

very nice, it will email you each day (or whatever you tell it to) with a compilation of logs, in a detail you specify, read the logs each day, you should notice a difference in the logs when it freezes up, as to what is happening on that day that isnt normally happening

---

