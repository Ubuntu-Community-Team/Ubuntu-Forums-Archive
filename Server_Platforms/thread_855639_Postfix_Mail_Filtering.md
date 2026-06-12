---
title: "Postfix Mail Filtering"
date: 2008-07-10
forum: Server Platforms
---

### Post by turtle02 on 2008-07-10
I am running 7.10 lamp server, I had postfix and dovecot up and running fine. I am trying to setup mail filtering using these instructions [https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html](https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html). I am unsure of all the info you need to help me out. Just let me know and i will  post it. Here is my log file.

This is mail.warn file

]: (07411-03) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20080710T134901-07411
Jul 10 14:59:03 sitesvsmail amavis[7759]: (07759-03) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20080710T145901-07759/parts: lstat() failed. ERROR\n
Jul 10 14:59:04 sitesvsmail amavis[7759]: (07759-03) (!!) WARN: all primary virus scanners failed, considering backups
Jul 10 14:59:04 sitesvsmail amavis[7759]: (07759-03) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED: 
Jul 10 14:59:04 sitesvsmail amavis[7759]: (07759-03) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20080710T145901-07759
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20080710T160859-07411/parts: lstat() failed. ERROR\n
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!!) WARN: all primary virus scanners failed, considering backups
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED: 
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20080710T160859-07411




This is Mail.info file

Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20080710T160859-07411/parts: lstat() failed. ERROR\n
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!!) WARN: all primary virus scanners failed, considering backups
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED: 
Jul 10 16:09:00 sitesvsmail amavis[7411]: (07411-04) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20080710T160859-07411
Jul 10 16:09:00 sitesvsmail postfix/smtp[8787]: 7A16017BF4A: to=<me@mydomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=13063, delays=13062/0.08/0.21/0.63, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=07411-04, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))

---

