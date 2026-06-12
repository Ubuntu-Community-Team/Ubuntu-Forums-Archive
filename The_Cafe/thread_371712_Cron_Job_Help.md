---
title: "Cron Job Help"
date: 2007-02-27
forum: The Cafe
---

### Post by MattSMiddleton on 2007-02-27
Hello,

At my work the guy that previously held my position made a cron job that seems to run every two hours.  However, when you look at the cron tab entry it shows:

"0 * * * * rsync..." 

Which should run every hour.  Any suggestions as to why it would only run every other hour?

Thank you ahead of time,
Matthew

---

### Post by Mateo on 2007-02-27
what if you tried this:

0 0-23 * * * rsync...

---

### Post by MattSMiddleton on 2007-02-27
It's actually ok that it is running every other hour, I am just trying to understand why it has this behavior since the crontab entry is showing that it should run every hour.  Thank you for your suggestion though.

---

### Post by Mateo on 2007-02-27
i don't know what to tell you.  Your command is correct.  Crontab is just a weird thing.  I had a problem one time where it would only run a command for a set time (about 15 minutes) when it was supposed to run for 3 hours.  Eventually it just started working right, without me changing anything.

maybe try restarting your computer?

---

### Post by OffHand on 2007-02-27
Try: 1 * * * *

---

### Post by TheWizzard on 2007-02-27
for hourly jobs, you can simply put the script in the /etc/cron.hourly/ folder. 

crontab works ok, but i think you'll need to restart the con deamon after changes.

---

### Post by MattSMiddleton on 2007-02-27
Well it turns out that it was running every hour, the person who was receiving the hourly e-mails that it sent missed one so he told me that it was doing it only every other hour when it was working correctly. :lolflag:  Thank you to everyone who helped me out!!

---

