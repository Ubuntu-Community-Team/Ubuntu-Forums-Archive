---
title: "rsyslog + mysql + phplogcon"
date: 2009-04-01
forum: Server Platforms
---

### Post by Useless on 2009-04-01
Its been quite a while since i have posted here.  I am looking to set up a syslog server which i can point my network devices to in order to capture and save logs.  Now, i want something which will take those logs, write them to a databse, and have a nice web interface to read them from.  

I am hoping this combination will work.  rsyslog, mysql, and phplogcon.  Before i kill myself trying to get this to work, has anyone set this up before?  Any pointers?  I am not that great with anything SQL related, but can usually get by.

---

### Post by de0xyrib0se on 2009-04-15
Your combination is quite useful. As for your question, yes I and presumably others have done this before.

What I can suggest is, go to the rsyslog site and follow their install guide for Debian. **Pay particular attention to the MySQL part**, it is critical you use the template provided in their source package to create the database schema if you want phplogcon to work correctly.

Last but not least make sure you update everything from the startup scripts to the daily rotate cron scripts so that things are rolled over nicely and everything starts up when the system does. If you are doing this on a server you can update just runlevel 2.

Anyway, hope this helps and good luck. To spare you the headache of looking for a config file I have attached one for you.

---

