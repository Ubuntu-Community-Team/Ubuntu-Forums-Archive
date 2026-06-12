---
title: "Cron spawns multiple instances of script"
date: 2011-11-01
forum: Server Platforms
---

### Post by sgardne on 2011-11-01
I have a perl script that I'd like to run every 2 hours. The script takes several minutes to run. If I run the script from the command line, it works exactly like I expect and stops when I expect. However, if I put it in my crontab, it will spawn 3 or more instances of the script while it's running. I'm really at a loss and am hoping there is something simple I'm missing. Here's the line from my crontab: ```
* */2 * * * /usr/bin/perl /home/sgardne/Scripts/Perl/Database/get_active_arp.pl >> /home/sgardne/logs/active_arp.log
``` Any insight would be appreciated. Thank you.

-Scott

---

### Post by SeijiSensei on 2011-11-01
I don't know why you get the multiple executions, but I have a suggestion to limit the problem.  When I write scripts that have long execution times, I write a lock file to /tmp.  When the script starts, it looks to see if the lock file exists and quits if it finds one.  When the legitimate script completes, it deletes the lock file.

---

### Post by cj13579 on 2011-11-01
I think I had a simmilar thing and I was dead confused by it but looking at the process Id's was the answer for me. It looked as though there was more than one instance of the script running but it was infact the commands within the script that were causing the extra "instances" <- for want of a better word.

I don't know if it is how cron runs stuff but the ps -ef command that I ran when running from the terminal and running via cron looked different but essentially gave the same answer. Another big clue for me was that my script sent an email and I would only ever get one copy of the mail. Try looking at your log, if you were getting multiple instances of the script running I would have thought your log file would look mental!

---

### Post by sgardne on 2011-11-01
> **cj13579 said:**
> I think I had a simmilar thing and I was dead confused by it but looking at the process Id's was the answer for me. It looked as though there was more than one instance of the script running but it was infact the commands within the script that were causing the extra "instances" <- for want of a better word.

I don't know if it is how cron runs stuff but the ps -ef command that I ran when running from the terminal and running via cron looked different but essentially gave the same answer. Another big clue for me was that my script sent an email and I would only ever get one copy of the mail. Try looking at your log, if you were getting multiple instances of the script running I would have thought your log file would look mental!

Actually, looking at the log file is what clued me in that there were multiples running. I started noticing that the "print" commands issued at the beginning of the script were showing up in the log midway through the script. I think it really is running multiple instances, although I'll check the PIDs like you suggest.

---

### Post by sgardne on 2011-11-01
> **SeijiSensei said:**
> I don't know why you get the multiple executions, but I have a suggestion to limit the problem.  When I write scripts that have long execution times, I write a lock file to /tmp.  When the script starts, it looks to see if the lock file exists and quits if it finds one.  When the legitimate script completes, it deletes the lock file.
I've been experimenting with "flock" but it's not giving me the results I want, so I may end up doing this. Thanks for the suggestion.

---

### Post by sgardne on 2011-11-01
D'oh! It was the crontab line. I'm an idiot. The crontab line should look like this: ```
0 */2 * * * /usr/bin/perl /home/sgardne/Scripts/Perl/Database/get_active_arp.pl >> /home/sgardne/logs/active_arp.log
``` Not like this: ```
* */2 * * * /usr/bin/perl /home/sgardne/Scripts/Perl/Database/get_active_arp.pl >> /home/sgardne/logs/active_arp.log
```

---

### Post by cj13579 on 2011-11-01
> **sgardne said:**
> I'm an idiot. 

Ha - glad you figured it out! 

Perhaps also creating the log with a timestamp is a good way forward as well?

---

