---
title: "How to configure 8.04 server to check / notify when updates are available?"
date: 2010-08-15
forum: Server Platforms
---

### Post by mdlueck on 2010-08-15
Starting with Ubuntu Server 9.04, when I log in at times the OS smartly reports the number of updates available. I have a couple of questions of how to extend this functionality:

1) How could I back-port that functionality to 8.04 servers? Does that happen somewhere in the /etc/cron.daily/apt script? (Just the checking on # of packages needing updates, does not need to appear on the login screen.)

2) Then with that information, if the number >0 then use mailx to send admins an email. Since 9.04 and higher already do the first item, then in my mind #2 is the only thing needed for 9.04 and higher servers, and #1 is also needed for 8.04 boxes.

Suggestions please? Thanks!

---

### Post by mdlueck on 2010-09-15
The solution to this question was to simply utilize the apticron package. That package checks apt for security updates, and if found sends an email detailing the updates required.

"Package: apticron"
[http://packages.ubuntu.com/hardy/apticron](http://packages.ubuntu.com/hardy/apticron)

No scripting trying to capture the newer Ubuntu login message necessary! :p

Sincerely,

---

