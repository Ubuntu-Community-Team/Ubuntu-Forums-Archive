---
title: "syslogd Restart and  signal 15"
date: 2006-10-18
forum: Server Platforms
---

### Post by acgiglyph on 2006-10-18
Looking at the messages log on my Ubuntu Breezy server I noted that every day @ about 6:30 I get the following errors:
Oct 17 06:27:38 ccrNas exiting on signal 15
Oct 17 06:27:40 ccrNas syslogd 1.4.1#17ubuntu7: restart.

No other log seems to have any signs of issues, we only run the server as a backup device, so no apache etc is running.  

Can anyone clue me into what is terminating every night?

---

### Post by sonic2000gr on 2006-10-19
It is the system log daemon that is restarting at 6.25ish every morning.

Nothing to worry about actually. The system cron daemon
(Configuration file is in /etc/crontab) runs a daily job every 6.25 in the morning. (Runs everything in /etc/cron.daily). Part of the job is to run the logrotate program that rotates system logs (and any logs you configure). Details can be found in /etc/logrotate.conf and you can add your rotation directives in /etc/logrotate.d as well. You may want to have a look at these files.

After rotating the log files (that is removing all the text they contain and saving it to a .gz file) the syslogd daemon is restarted so it writes to a new empty file. You will find the compressed log files in /var/log usually as syslog.1.gz, syslog.2.gz and so on. If you take a close look you will see the time stamp on them is around 6.25.

---

### Post by acgiglyph on 2006-10-19
Looks like you are correct, thanks for the info.  I knew it wasn't bad, just couldn't figure out what it meant.

---

