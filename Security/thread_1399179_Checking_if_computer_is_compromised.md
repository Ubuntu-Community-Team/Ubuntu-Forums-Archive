---
title: "Checking if computer is compromised?"
date: 2010-02-05
forum: Security
---

### Post by tg103 on 2010-02-05
I run Ubuntu 9.04 and was recently told by my university that my computer is massively port scanning the network.
  I am interesting in learning more about figuring out what is happening to stop it, but I am lost at where to begin. What steps should I take (or files to look at) to figure out what is happening?

---

### Post by Grenage on 2010-02-05
You could start by typing *netstat* into a terminal, this should display active connections.

---

### Post by BkkBonanza on 2010-02-05
Also a simple process listing will likely show something you don't know about running - unless you've been rootkit'd. In which case none of your diagnostics will be trustworthy.

You could post this for feedback about suspicious processes,

ps afx

---

### Post by tg103 on 2010-02-05
I ran rkhunter and it gave some warnings saying there was outgoing traffic on port 6667 which could be indicative of a rootkit. Also, another user was created on my computer with the same uid as root (named 'slym'). 

Root's crontab says 
'* * * * * /root/.bash/update >/dev/null 2>&1' . This directory contains a bunch of files, some created by my user, some by user 'slym'. 

Netstat says that there was an established TCP connection from port 6667 on some random high numbered port. 

From all of this, I assume my system has been compromised. I could go ahead and wipe my OS and restart, but I would rather learn more about why this happened. What steps would you take to figure out how this happened and possibly eliminate the damages?

---

### Post by FuturePilot on 2010-02-05
That definitely sounds compromised. I would take a look at those files to see what they're doing. Perhaps image the drive for analysis later and then reinstall, but I would definitely take that computer offline immediately.

---

### Post by BkkBonanza on 2010-02-05
Check the logs for indications of when this started. They may have been wiped clean but it is worth looking in case the hacker didn't cover up.

For example,

grep slym /var/log/*

may indicate first occurences or even log entries for adding the user which will help locate date/times. You may be able to find events which led to the compromise at the same time. eg. VNC use or logins. A good hacker would have covered this up but you want to check in case there are clues there. This would be a good first step.

I don't think you will be able to reverse this but you may learn something about how it happened. You will end up re-installing to be certain that the rootkit is gone. You need to know what method was used to get in if possible.

---

### Post by koryGander on 2010-02-05
Thank you very much for this great insight. Never though of netstat

---

### Post by tg103 on 2010-02-05
I checked the logs and in auth.log there are a bunch of failed ssh login attempts for user 'guest' and 'root'. I did not remember having a user 'guest', but perhaps it was there and  it had a weak password. Even still, not sure how getting that password would help it get root access. 

Anyway, in auth.log there are also a bunch of entries mixed in with these ssh failed login attempts (1 per minute) that look like:
CRON: pam_unix(cron:session); session opened for user guest (by uid=0). 

and then a second later:
CRON: pam_unix(cron:session); session closed for user guest.

Also, there are the same for user root. Not sure what these entries mean..how could there be cron jobs if they did not have access to these accounts?

General questions:
1) is there a log file that lets me see a history of which commands a user has run?
2) is there a way to human read files like btmp/utmp/wtmp?

Thanks very much for your help so far.

---

### Post by BkkBonanza on 2010-02-05
Guest may be a user created afterwards to try and ensure the ability to get back in. The log entries you list above seem to inidcate that guest either has uid=0 or that root opened a session for guest. I'm not sure which but uid=0 is the root uid.

The file .bash_history lists past commands (for each user in their home). Take a look, you may find something. I had a look at mine to see how far it went but it didn't go too far back and had no datestamps. Still, possibly could help.

Unfortunately, I'm not an expert at forensics so you really need help from someone with more experience, or perhaps you can find forensics tutorials/help online.

---

