---
title: "how to  fix the problem Error rsyslog  in syslog"
date: 2024-04-26
forum: System76 Support
---

### Post by pitakskli on 2024-04-26
how to  fix the problem Error rsyslog  in syslog.   please help me verify the error on below  


 rsyslogd[1067]: imfile: internal error? inotify provided watch descriptor 5 which we could not find in our tables - ignored [v8.2112.0 try [https://www.rsyslog.com/e/2175](https://www.rsyslog.com/e/2175) ]

 rsyslogd[1067]: imfile: internal error? inotify provided watch descriptor 5 which we could not find in our tables - ignored [v8.2112.0 try [https://www.rsyslog.com/e/2175](https://www.rsyslog.com/e/2175) ]

 rsyslogd[1067]: imfile: internal error? inotify provided watch descriptor 5 which we could not find in our tables - ignored [v8.2112.0 try [https://www.rsyslog.com/e/2175](https://www.rsyslog.com/e/2175) ]


systemd-journald[637]: Forwarding to syslog missed 1 messages.
Subject: One or more messages could not be forwarded to syslog
Defined-By: systemd
Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

---

### Post by euol on 2024-08-05
You can edit the rsyslog configuration file, usually found at /etc/rsyslog.conf or within /etc/rsyslog.d/. Check if the imfile settings are correct and match the files being monitored.

after you are done

sudo systemctl restart rsyslog

---

### Post by &amp;KyT$0P# on 2024-08-05
What System76 hardware is this happening on?

---

