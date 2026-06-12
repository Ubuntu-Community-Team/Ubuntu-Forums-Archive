---
title: "Rebuild webalizer stats."
date: 2015-05-13
forum: Server Platforms
---

### Post by ahulshof on 2015-05-13
Have to rebuild my webalizer stats from the daily access.log's. Can this be done and if yes how?
Thanks

---

### Post by QIII on 2015-05-13
Moved to Server Platforms.

---

### Post by ahulshof on 2015-05-13
Can someone help me??

---

### Post by SeijiSensei on 2015-05-13
I don't use webalizer, but I have used analog.  As far I as know, both of them will compile results from as long a log file as you have.  Perhaps you should start by reading the [webalizer man page](http://www.webalizer.org/webalizer.1.html) at [http://www.webalizer.org](http://www.webalizer.org).

---

### Post by ahulshof on 2015-05-14
tried 1 big access.log from 7 weeks. did not work

---

### Post by SeijiSensei on 2015-05-14
You need to show us the exact command line you used.  No one can diagnose "did not work" without a lot more details.  Include any configuration files you wrote as well.

---

### Post by ahulshof on 2015-06-01
First try:
I created 1 big file with all access.log contents sorted on date time and run webalizer with this file in directory: /var/www/clients/client1/web1/log after deleting webalizer.hist in the stats directory
This did not recreate the stats for that time period

Second try:
First I deleted webalizer.hist in /var/www/clients/client1/web1/web/stats/ running rm webalizer.hist
Then I went to directory: /var/www/clients/client1/web1/log where the webalizer.conf file is for this domain.
In webalizer.conf I changed for each day the Logfile from /var/log/apache2/access.log to Logfile /access location where i put all daily 
i.e. 20150503-access.log files to 20150531-access.log
After changing the webalizer.conf for each access.log file I saved it and run service apache2 restart. After this I run webalizer still in the log directory
For every day I run sequentially, still in the log directory, webalizer for the access.log of that day 
This did not recreate my stats either.

Please help me resolve this.
Thanks

---

### Post by ahulshof on 2015-06-01
I did, But it did not give a clue

---

### Post by cariboo on 2015-06-01
Could you copy and paste the commands you used and their results in your next post. I access my home server via ssh in a terminal, which allows me to cut and paste the output in the terminal.

---

