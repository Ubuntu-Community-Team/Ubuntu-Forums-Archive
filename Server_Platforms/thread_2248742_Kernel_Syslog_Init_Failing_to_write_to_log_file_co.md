---
title: "Kernel Syslog Init Failing to write to log file consumes ALL free space"
date: 2014-10-16
forum: Server Platforms
---

### Post by regnumimbriumx on 2014-10-16
Hi friends,

I've got a 14.04 server onto which I had installed the free CommaFeed software. In the last few days, I started experiencing regular losses of all of my free space. Today I searched for all files greater than 1G and found that my syslog files were huge, with one particular file - syslog.1 - reading a whopping 22 gigabytes. I looked into the file and about 99.9% of it was repeated attempts to write to another log file that I had deleted to create some free space. It read:

Oct 14 15:33:27 user kernel: [59383.490556] init: Failed to write to log file /var/log/upstart/commafeed.log
Oct 14 15:33:27 user kernel: [59383.490782] init: Failed to write to log file /var/log/upstart/commafeed.log

...over and over and over again.

It was essentially 22 gigs of that same line. Why is this happening? Can someone advice a best-practices solution?

Thank you very much for your help!

---

### Post by tgalati4 on 2014-10-16
What are the permissions of commafeed.log?  Perhaps:

```
sudo chmod 777 /var/log/upstart/commafeed.log
```

Only after you clean up the logs. Linux hates running out of space:  "Elbow room cried Daniel Boone!"

---

### Post by regnumimbriumx on 2014-10-21
Thanks for the suggestion, [COLOR=#000000]tgalati4. Can you / anyone else tell me which process is making all of these attempts to write to the file? Are you aware of any way to prevent it from doing this so frequently? [/COLOR]

---

### Post by SeijiSensei on 2014-10-21
I don't see anything in the repositories for "commafeed" so you need to ask on that program's own support site.

---

