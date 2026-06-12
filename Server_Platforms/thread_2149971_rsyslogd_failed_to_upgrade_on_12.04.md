---
title: "rsyslogd failed to upgrade on 12.04"
date: 2013-05-30
forum: Server Platforms
---

### Post by DizzyD on 2013-05-30
I did an aptitude safe-upgrade on my 12.04 64bit server last week and there was a new version of rsyslog (rsyslog_5.8.6-1ubuntu8.2_amd64) to upgrade to. This failed with the following error

 Setting up rsyslog (5.8.6-1ubuntu8.2) ...
start: Job failed to start
invoke-rc.d: initscript rsyslog, action "start" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up rsyslog (5.8.6-1ubuntu8.2) ...
start: Job failed to start
invoke-rc.d: initscript rsyslog, action "start" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rsyslog


I have tried to remove the package and reinstalling and get the same error

in dmesg I get 

init: error.c:320: Assertion failed in nih_error_get: CURRENT_CONTEXT->error != NULL
init: Caught abort, core dumped
init: rsyslog pre-start process (16533) terminated with status 6

It seems to be a problem with the upstart scripts because rsyslogd exists in /usr/sbin/ and when run from the command line with the following 
rsyslogd -c5 -f /etc/rsyslog.conf
it runs fine.

Thanks

---

