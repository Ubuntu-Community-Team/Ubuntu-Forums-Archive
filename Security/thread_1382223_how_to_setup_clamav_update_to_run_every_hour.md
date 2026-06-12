---
title: "how to setup clamav update to run every hour?"
date: 2010-01-15
forum: Security
---

### Post by miamia1 on 2010-01-15
hello,
I am newbie to ubuntu so please can you explain me how to schedule updates for clamav (every hour)? 
 
thank you in advance

---

### Post by Enigmapond on 2010-01-15
Truthfully you wouldn't need to as the chances of it ever finding a virus on any Ubuntu distro is little to none. They just don't exist. I use it to scan something I'm running through wine...but very rarely. I don't know what the default updating but whatever it is...it's MORE than sufficient.

---

### Post by miamia1 on 2010-01-15
ok thanks for reply. maybe wrong question but - after clamav installation on ubuntu it is automatically preconfigured to download updates? (does not matter how often)

---

### Post by Enigmapond on 2010-01-15
To the best of my knowledge yes. All I know is that the database is always up to date when I look at it...and again...I rarely ever do or need to.

---

### Post by miamia1 on 2010-01-15
thank you very much :-)

---

### Post by HermanAB on 2010-01-16
To answer your question, put a link in /etc/cron.hourly to freshclam.

---

### Post by Freiheit on 2010-01-31
lol dont answer such questions without mentioning, that updating EVERY HOUR will get you banned from clamav-servers.
what do you think, that clamAV updates its virus definitions every hour?
all windows virus scanners update their virus definitions only every 2-3 days.
this was far from being professional, HermanAB ;)

---

### Post by cariboo on 2010-01-31
When you run freshclam, it creates a cron job that checks for updates every hour by default.

---

### Post by sf-it-services on 2010-06-18
I have clamav set up with default updates.  Which is definately every hour based on the logs.  I  wish to change this to a daily update but checking in the hourly cron jobs I cannot find where clamav is making the hourly requests from, it must be somewhere.

---

### Post by sf-it-services on 2010-06-18
its okay, I just found the clamAV database update schedule in /etc/clamav/freshclam.conf

# Check for new database 24 times a day
Checks 24

This whole situation arose from wanting to problem solve a broken pipe issue with the connection between clamAV and openwebmail.   I hope I get that one fixed sooner too

---

