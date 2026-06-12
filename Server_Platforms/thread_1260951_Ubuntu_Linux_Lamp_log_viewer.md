---
title: "Ubuntu Linux Lamp log viewer"
date: 2009-09-08
forum: Server Platforms
---

### Post by Cardale on 2009-09-08
[FONT=monospace]I was looking at serveral threads regarding security and I have slowly become more aware of ways of prevention, but how can anyone possibly look at every single log file on the system?  Is there a good shell script or maybe seperate little program that displays all important UBUNTU LAMP server log files at once?
[/FONT]

---

### Post by R.Bucky on 2009-09-08
You do not have to look at every logfile. The main logs that I look at are the auth.log, mail.log (only if you have a mail server), and the apache2/error.log. Every other day or so for me and I host 10+ domains. 5 minutes every other day or so...

---

### Post by ainsworth_t on 2009-09-09
I haven't used it myself, but I came across Logwatch, might be what you're interested in: [https://help.ubuntu.com/community/Logwatch](https://help.ubuntu.com/community/Logwatch)

---

