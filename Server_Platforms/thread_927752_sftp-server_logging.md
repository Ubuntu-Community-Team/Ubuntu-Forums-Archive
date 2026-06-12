---
title: "sftp-server logging"
date: 2008-09-23
forum: Server Platforms
---

### Post by Desbocado on 2008-09-23
Hello people,

I'm trying to log all the actions who users type in my sftp-server.
I have an ubuntu server LTS (8.04) and I did the "standard" method for it.

in /etc/ssh/sshd_config
```
# Logging
SyslogFacility AUTH
LogLevel DEBUG

Subsystem sftp /usr/lib/openssh/sftp-server -f AUTH -l DEBUG
```

so I though it was a problem of openssh (version? OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007). Then I downloaded the lastest version of openssh (openssh-5.1p1), compiled it and replacing the old sftp-server with the new version.

OkOk.. it doesn't work too. Ssh logs with level debug works but sftp-server doesn't do nothing...

Do you know if it's a problem of syslogd? /dev/log? do I have to edit any permission? I don't know what more to do... I though it was possible with the version 4.4p1 of OpenSSH...

Thanks a lot :) cheers!!

---

### Post by Desbocado on 2008-09-23
Well... I "solved" it. How?

I went to the source code of the new OpenSHH 5.1 and added this lines (and recompile and replace)

```
log_level = SYSLOG_LEVEL_DEBUG1;
log_facility = SYSLOG_FACILITY_AUTH;
```

after the function getopt() at sftp_server_main().

It tells me that the problem is about the args I put. I don't know why... but sftp-server didn't take them like I wrote up. Maybe I had to enter in another form...

(( when I looked for a solution I saw that sftp-server is called as 
```
sftp-server -c /usr/lib/openssh/sftp-server -f AUTH -l DEBUG
```
I don't know if it's right, but I didn't like so much... :S ))

---

