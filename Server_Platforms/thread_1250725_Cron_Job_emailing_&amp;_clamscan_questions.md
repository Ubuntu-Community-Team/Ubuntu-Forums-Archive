---
title: "Cron Job emailing &amp; clamscan questions"
date: 2009-08-26
forum: Server Platforms
---

### Post by Lori700698 on 2009-08-26
Ok, I'm probably just not hitting the right keywords but I can't seem to find an answer to this. (which I can generally find everything I need here without needing to post)

1. My cron jobs are not emailing me after they run or with any type of reports.  I think it has to do with me using Citadel, I use webmin (love this)and I can't find anywhere to change the default mail to program.  The cron's I set up on my own emails me with no issues, but I had to set them to| citmail security@localhost (which root would work too, I have both set up as alias's to my citmail inbox.  All the examples I saw were for mail -s, which didn't get to my inbox.

2. How do I get my clamscan report to clear before I get a new one, at the moment I have a huge running report.
clamscan -r -l virus.txt; cat virus.txt;  /home |citmail "Virus Scan: virus.txt" security@localhost

Thanks in advance!
Lori

---

### Post by Lori700698 on 2009-08-27
I figured out that I needed to put the report in the log file and set it up to rotate weekly, which will give me a nice clean report.

The cron mail issue, could it be that I don't have sendmail set up?  Or can I change a setting somewhere to have cron/whole system use citmail instead?

Thanks
Lori

---

### Post by Lori700698 on 2009-08-28
Solved my problem!  SpamAssassin was spamming mail sent from my server!

Dah, don't I feel silly!

---

