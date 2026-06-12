---
title: "What is Gnome-session-Unity.log.6.gz?"
date: 2015-08-26
forum: Security
---

### Post by category_1 on 2015-08-26
Hey all,

Did an anti-virus scan on my Ubuntu with Clam and it came up with "Gnome-session-Unity.log.6.gz" as a phishing infection. Can any one confirm what exactly Gnome-session-Unity.log.6.gz is and does? as clam seems to bring up a number of files that are definitely not viruses and a google search proved inconclusive.

Thanks

---

### Post by cariboo on 2015-08-26
You can use the System Log application to view the contents of the log to see if there is anything suspicious. I'd say that more than likely it is a false positive.

---

### Post by CharlesA on 2015-08-26
Adding to what cariboo said, the gz extension indicates a file compressed with gzip, and the naming convention reminds me of a file created via logrotate.

Where is that file located? If it is in /var/log, it is more than likely a backed up log file that was compressed to save space.

---

### Post by category_1 on 2015-08-27
The file was located in the following directory:

/home/username/.cache/upstart/gnome-session-Unity.log.6.gz

---

### Post by CharlesA on 2015-08-27
Yeah, should be fine.

---

