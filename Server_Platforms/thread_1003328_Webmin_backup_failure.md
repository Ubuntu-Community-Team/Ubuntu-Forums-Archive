---
title: "Webmin backup failure"
date: 2008-12-06
forum: Server Platforms
---

### Post by R.Bucky on 2008-12-06
I am trying to backup my filesystem using Webmin. I received the message "File size limit exceeded." Essentially, Webmin is being used to backup my /home/user directory to an external drive. Unable to located documentation for this problem. The backup stopped at 4GB. Suggestions?

Attached is a screenshot.[IMG]http://buckyspalace.net/images/webmin_filesize.png[/IMG]

---

### Post by R.Bucky on 2008-12-06
SOLVED

Further searching on the internet clicked the nuerons in my brain. I realized that I was trying to have Webmin post a backup file to an external drive that was partitioned file allocation table 16 (fat16). The maximum file size for fat16 is 4GB minus 1MB. 

The solution to this problem was a reformatting of my external drive to ext3 using gparted. Webmin does not have a problem backing up my hard drive now!

---

