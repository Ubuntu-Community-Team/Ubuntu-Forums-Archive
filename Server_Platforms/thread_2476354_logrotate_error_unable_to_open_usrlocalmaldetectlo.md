---
title: "logrotate: error: unable to open /usr/local/maldetect/logs/inotify_log.1 for compress"
date: 2022-06-23
forum: Server Platforms
---

### Post by andbiz on 2022-06-23
[COLOR=#24292F][FONT=-apple-system]Hello. Ubuntu v20.04. I've been trying to set up logrotate for a month now. The error "cannot open /usr/local/maldetect/logs/inotify_log.1 for compression" occurs. The error occurs at night. How can this be fixed?[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]&#9679; logrotate.service - Rotate log files[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Jun 22 00:00:00 server.easywork.com.ua systemd[1]: Starting Rotate log files...
**Jun 22 00:00:00 server.easywork.com.ua logrotate[2617698]: error: unable to open /usr/local/maldetect/logs/inotify_log.1 for compression**
Jun 22 00:00:00 server.easywork.com.ua systemd[1]: logrotate.service: Main process exited, code=exited, status=1/FAILURE
Jun 22 00:00:00 server.easywork.com.ua systemd[1]: logrotate.service: Failed with result 'exit-code'.
Jun 22 00:00:00 server.easywork.com.ua systemd[1]: Failed to start Rotate log files.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Scripts I've tried:[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]/usr/local/maldetect/logs/event_log
/usr/local/maldetect/logs/clamscan_log {
weekly
rotate 4
size=100M
missingok
notifempty
compress
delaycompress
create 0644 root root
}
/usr/local/maldetect/logs/inotify_log {
weekly
rotate 4
size=100M
missingok
notifempty
compress
delaycompress
create 0640 root root
postrotate
/bin/systemctl condrestart maldet.service > /dev/null 2>/dev/null || true
endscript
}[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]/usr/local/maldetect/logs/event_log
/usr/local/maldetect/logs/clamscan_log {
weekly
rotate 2
missingok
notifempty
compress
delaycompress
create 0644 root root
}
/usr/local/maldetect/logs/inotify_log {
daily
rotate 7
missingok
notifempty
compress
delaycompress
create 0644 root root
postrotate
/bin/systemctl condrestart maldet.service > /dev/null 2>/dev/null || true
endscript
}[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Maldet is archived properly with commands:
/usr/sbin/logrotate -vf /etc/logrotate.conf
logrotate -f /etc/logrotate.d/maldet
logrotate -d -f /etc/logrotate.d/maldet[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Changing permissions didn't help.
root@server:/usr/local/maldetect/logs# ls -l /usr/local/maldetect/logs
total 22956
-rw-r--r-- 1 root root 0 Jun 1 21:20 clamscan_log
-rw-r--r-- 1 root root 15157 Jun 15 20:25 event_log
-rw-r--r-- 1 root root 1215 Jun 15 17:08 event_log.1
-rw-r--r-- 1 root root 388 Jun 15 17:07 event_log.2.gz
-rw-r--r-- 1 root root 15733 Jun 13 20:39 event_log.4.gz
-rw-r--r-- 1 root root 21230954 Jun 15 20:25 inotify_log
-rw-r--r-- 1 root root 93 Jun 15 17:08 inotify_log.1
-rw-r--r-- 1 root root 100 Jun 15 17:07 inotify_log.2.gz
-rw-r--r-- 1 root root 199223 Jun 15 17:07 inotify_log.3.gz
-rw-r--r-- 1 root root 633 Jun 14 20:45 inotify_log.4.gz
-rw-r--r-- 1 root root 1310370 Jun 14 20:41 inotify_log.5.gz
-rw-r--r-- 1 root root 264 Jun 13 20:40 inotify_log.6.gz
-rw-r--r-- 1 root root 696653 Jun 13 20:39 inotify_log.7.gz[/FONT][/COLOR]

---

