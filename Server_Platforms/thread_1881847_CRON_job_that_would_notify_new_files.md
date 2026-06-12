---
title: "CRON job that would notify new files"
date: 2011-11-16
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-11-16
Have a Windows application that FTPs a text file report to a folder /var/data/errorlog should an error occur in the application.

At the moment, there has to be a manual check on the folder /var/data/errorlog to determine if there are any new files.

At the least, would like to setup a CRON job that would run every n minutes and send an email notification advising that a new report had been received.

At best, it would be helpful if the text file report could be sent as an attachment in case one was away from the office.

Either way, the CRON job could then move any new text file reports to a folder such as /var/data/errorlog/archive.

ssmtp is installed on the server.

Ideas, please?

TIA

---

### Post by littlegreiger on 2011-11-16
Take a look at incron. It runs scripts through "incrontab" (similar to cron and crontab) based on inotify notifications. Take a look at [http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/]("http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/") for an example of how to use it. You can set up an entry to run a script when a new file is created in /var/data/errorlog. You would still have to write the short script to send your email though.

---

### Post by Lars Noodén on 2011-11-16
It's in the package, [incron](http://packages.ubuntu.com/oneiric/incron)

---

### Post by ChrisRChamberlain on 2011-11-17
Thanks both

Will go find

---

