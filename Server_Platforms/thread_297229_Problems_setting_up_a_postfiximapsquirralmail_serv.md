---
title: "Problems setting up a postfix/imap/squirralmail server"
date: 2006-11-10
forum: Server Platforms
---

### Post by elminster13 on 2006-11-10
hi all,

hope someone can help, i followed the wikipedia trying to setup a mail server using postfix, dovecot and squirrelmail so that i can manage my own mails but am encountering problems.
first off i can email out using sendmail, but when i try to use squirrelmail i get the following errors in mail.err:

[SIZE="1"][FONT="Book Antiqua"][SIZE="2"][SIZE="2"]Nov 11 01:32:59 trantor postfix/smtpd[16906]: fatal: unexpected command-line argument: 192.168.1.0/24
Nov 11 01:34:00 trantor postfix/smtpd[16910]: fatal: unexpected command-line argument: 192.168.1.0/24
Nov 11 01:37:32 trantor amavis[16907]: (16907-01) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20061111T013730-16907/parts: lstat() failed. ERROR\n
Nov 11 01:37:33 trantor amavis[16907]: (16907-01) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:37:33 trantor amavis[16907]: (16907-01) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:[/SIZE][/SIZE][/FONT][/SIZE]

when i telnet localhost 10025 i get:
[SIZE="1"][FONT="Book Antiqua"][SIZE="2"]telnet localhost 10025
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.[/SIZE][/FONT][/SIZE]

in mail.info:
[SIZE="1"][FONT="Book Antiqua"][SIZE="2"]
Nov 11 01:46:10 trantor postfix/smtpd[16966]: warning: cannot get certificate from file /etc/postfix/ssl/smtpd.crt
Nov 11 01:46:10 trantor postfix/smtpd[16966]: warning: TLS library problem: 16966:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/etc/postfix/ssl/smtpd.crt','r'):
Nov 11 01:46:10 trantor postfix/smtpd[16966]: warning: TLS library problem: 16966:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
Nov 11 01:46:10 trantor postfix/smtpd[16966]: warning: TLS library problem: 16966:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:720:
Nov 11 01:46:10 trantor postfix/smtpd[16966]: cannot load RSA certificate and key data
Nov 11 01:46:10 trantor postfix/smtpd[16966]: connect from localhost[127.0.0.1]
Nov 11 01:46:10 trantor postfix/smtpd[16966]: warning: restriction `my_networks' after `permit' is ignored
Nov 11 01:46:10 trantor postfix/smtpd[16966]: 2EE3925814E: client=localhost[127.0.0.1]
Nov 11 01:46:10 trantor postfix/cleanup[16969]: 2EE3925814E: message-id=<50028.192.168.1.16.1163209570.squirrel@192.168.1.10>
Nov 11 01:46:10 trantor postfix/qmgr[16767]: 2EE3925814E: from=<duanea1@duaneville.co.uk>, size=731, nrcpt=1 (queue active)
Nov 11 01:46:10 trantor postfix/smtpd[16966]: disconnect from localhost[127.0.0.1]
Nov 11 01:46:10 trantor dovecot: imap-login: Login: user=<duanea1>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Nov 11 01:46:10 trantor amavis[16908]: (16908-01) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20061111T014610-16908/parts: lstat() failed. ERROR\n
Nov 11 01:46:10 trantor amavis[16908]: (16908-01) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:46:10 trantor amavis[16908]: (16908-01) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:
Nov 11 01:46:10 trantor amavis[16908]: (16908-01) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014610-16908
Nov 11 01:46:10 trantor postfix/smtp[16970]: 2EE3925814E: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.23, delays=0.08/0.02/0.03/0.1, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=16908-01, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))
Nov 11 01:46:10 trantor dovecot: IMAP(duanea1): Disconnected: Logged out
Nov 11 01:46:10 trantor dovecot: imap-login: Login: user=<duanea1>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Nov 11 01:46:10 trantor dovecot: IMAP(duanea1): Disconnected: Logged out[/SIZE][/FONT][/SIZE]


in mail.log:
[SIZE="1"][FONT="Book Antiqua"][SIZE="2"]Nov 11 01:47:27 trantor postfix/qmgr[16767]: CB97F25812C: from=<duanea1@duaneville.co.uk>, size=746, nrcpt=1 (queue active)
Nov 11 01:47:27 trantor postfix/qmgr[16767]: 7616625812B: from=<duanea1@duaneville.co.uk>, size=736, nrcpt=1 (queue active)
Nov 11 01:47:27 trantor postfix/qmgr[16767]: 7FB72258132: from=<root@duaneville.co.uk>, size=302, nrcpt=1 (queue active)
Nov 11 01:47:27 trantor postfix/qmgr[16767]: 5345D25813F: from=<duanea1@duaneville.co.uk>, size=734, nrcpt=1 (queue active)
Nov 11 01:47:27 trantor postfix/qmgr[16767]: A7FC0258143: from=<duanea1@duaneville.co.uk>, size=727, nrcpt=1 (queue active)
Nov 11 01:47:27 trantor postfix/qmgr[16767]: EA404258147: from=<duanea1@duaneville.co.uk>, size=738, nrcpt=1 (queue active)
Nov 11 01:47:27 trantor amavis[16907]: (16907-02) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/
amavis-20061111T014727-16907/parts: lstat() failed. ERROR\n
Nov 11 01:47:27 trantor amavis[16907]: (16907-02) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:47:27 trantor amavis[16907]: (16907-02) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNE
RS FAILED:
Nov 11 01:47:27 trantor amavis[16908]: (16908-02) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/
amavis-20061111T014727-16908/parts: lstat() failed. ERROR\n
Nov 11 01:47:27 trantor amavis[16908]: (16908-02) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:47:27 trantor amavis[16908]: (16908-02) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNE
RS FAILED:
Nov 11 01:47:27 trantor amavis[16908]: (16908-02) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014727-16908
Nov 11 01:47:27 trantor amavis[16907]: (16907-02) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014727-16907
Nov 11 01:47:27 trantor postfix/smtp[16983]: 7616625812B: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay
=3230, delays=3230/0.03/0.01/0.11, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing,
 id=16908-02, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))
Nov 11 01:47:27 trantor postfix/smtp[16970]: CB97F25812C: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay
=3180, delays=3180/0/0.02/0.13, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id
=16907-02, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))
Nov 11 01:47:27 trantor amavis[16908]: (16908-03) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/
amavis-20061111T014727-16908/parts: lstat() failed. ERROR\n
Nov 11 01:47:27 trantor amavis[16908]: (16908-03) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:47:27 trantor amavis[16908]: (16908-03) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNE
RS FAILED:
Nov 11 01:47:27 trantor amavis[16908]: (16908-03) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014727-16908
Nov 11 01:47:27 trantor amavis[16907]: (16907-03) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/
amavis-20061111T014727-16907/parts: lstat() failed. ERROR\n
Nov 11 01:47:27 trantor amavis[16907]: (16907-03) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:47:27 trantor postfix/smtp[16983]: 7FB72258132: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay
=3130, delays=3130/0.17/0.02/0.11, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing,
 id=16908-03, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))
Nov 11 01:47:27 trantor amavis[16907]: (16907-03) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNE
RS FAILED:
Nov 11 01:47:27 trantor amavis[16907]: (16907-03) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014727-16907
Nov 11 01:47:27 trantor postfix/smtp[16970]: 5345D25813F: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay
=1929, delays=1929/0.21/0.01/0.11, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing,
 id=16907-03, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))
Nov 11 01:47:27 trantor amavis[16908]: (16908-03-2) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tm
p/amavis-20061111T014727-16908/parts: lstat() failed. ERROR\n
Nov 11 01:47:27 trantor amavis[16908]: (16908-03-2) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:47:27 trantor amavis[16908]: (16908-03-2) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCAN
NERS FAILED:
Nov 11 01:47:27 trantor amavis[16908]: (16908-03-2) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014727-169
08
Nov 11 01:47:27 trantor postfix/smtp[16983]: A7FC0258143: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, conn_
use=2, delay=1284, delays=1284/0.32/0/0.08, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in pr
ocessing, id=16908-03-2, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))
Nov 11 01:47:27 trantor amavis[16907]: (16907-03-2) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tm
p/amavis-20061111T014727-16907/parts: lstat() failed. ERROR\n
Nov 11 01:47:28 trantor amavis[16907]: (16907-03-2) (!!) WARN: all primary virus scanners failed, considering backups
Nov 11 01:47:28 trantor amavis[16907]: (16907-03-2) (!!) TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCAN
NERS FAILED:
Nov 11 01:47:28 trantor amavis[16907]: (16907-03-2) (!) PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20061111T014727-169
07
Nov 11 01:47:28 trantor postfix/smtp[16970]: EA404258147: to=<elminster13@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, conn_
use=2, delay=1131, delays=1131/0.35/0/0.11, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in pr
ocessing, id=16907-03-2, virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED:  (in reply to end of DATA command))[/SIZE][/FONT][/SIZE]

anyway enough logs i have them coming out of my yingyangs but they don't mean very much! any ideas?

---

### Post by elst on 2006-11-12
From experience Linux logging is very good at telling you precisely the problem in more detail than you may want to know.

It looks like two issues:

The first is that Postfix can't find the specified digital certificate:

"Nov 11 01:46:10 trantor postfix/smtpd[16966]: warning: TLS library problem: 16966:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/etc/postfix/ssl/smtpd.crt','r'):"

The second is your ClamAV anti-virus service isn't working, so attempts to scan your mails are failing.

---

