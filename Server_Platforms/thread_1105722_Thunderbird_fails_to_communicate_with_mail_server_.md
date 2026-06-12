---
title: "Thunderbird fails to communicate with mail server - workarounds found"
date: 2009-03-25
forum: Server Platforms
---

### Post by PapaNerd on 2009-03-25
Background:
The /home partition on my mail server died last week resulting in quite a few kernel errors.  After replacing the disk drive and reinstalling Ubuntu v8.04.2 server, I had a lot of trouble getting sendmail to run again like it was before.  I ended up copying in the old /etc/mail directory backups and rebuilding the .cf and .db files, and this got email working fine for remote users as well as inbound connections to the mail server from other domains.  However, two problems remained.

Problem #1 (receiving email on local clients):
Thunderbird clients on the internal LAN could receive email from dovecot on the mail server, but were pestered to death with a certificate warning message each time the client connected (every minute on some machines).  

Solution to Problem #1:
Edit the /usr/share/ssl-cert/ssleay.cnf file, replacing "@HostName@" in the "commonName" parameter with the FQDN of the mail server (as configured in DNS settings).  Regenerate the certificate using the "make-ssl-cert generate-default-snakeoil --force-overwrite" command.

Problem #2 (sending email from local clients):
Thunderbird clients on the internal LAN were unable to send email to sendmail on the mail server.  After clicking on "Send", a pop-up titled "Mail Server Password Required" would appear.  No matter how many times the password was entered, the same box would pop back up.  If one clicked on "Cancel", a pop-up error message appeared:  "Sending of message failed.  The message could not be sent because connecting to SMTP server <mail server name> failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server setting is correct and try again, or else contact your network administrator."  At the same time, the mail server would record a "<date> <server name> sm-mta: <mssg id>: <client name> [<client IP>] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA" message.

Debugging of Problem #2:
A telnet from the client machine to port 25 on the mail server and issuing low level commands to sendmail worked fine, and non-local clients were not affected, so it did not appear to be a server issue.  I tried various SMTP settings in Thunderbird.  For the Server Name, I tried the DNS name, a DMZ LAN IP address, and a private LAN IP address (via an Ethernet cable directly between a client and the server and secondary NICs).  For the SMTP port, I tried 25, 465, and 587.  For the secure connection, I tried all four settings (None, TLS if available, TLS, and SSL).  Nothing worked.

Workaround for Problem #2:
After doing a lot of web surfing, I found many postings on various discussion groups and no solid solutions offered.  The cause of this problem appears to have been a setting in the Thunderbird email client that was cached behind the scenes and not updated automagically when the mail server was reinstalled.  My workaround was to close Thunderbird, open a terminal window, and then do an ssh to the mail server with the added parameter "-L10025:localhost:25".  With this connection open, I re-started Thunderbird and set [1] the Server Name to "localhost", [2] the SMTP port to 10025, [3] no user ID, and [4] the secure connection to "None".  At this point, Thunderbird sending began working, so I was then able to close the ssh session down, reset the Server Name to the DNS same, and return to using SMTP port 25.  I could not, however, successfully re-enable the login info without the original problem returning.

Postmortem on Problem #2:
When I cloned this workaround to a second client, I did a grep for "smtp" in the "~/.mozilla-thunderbird/*default/prefs.js" file both before and after the change, and was not able to identify the parameter that caused the problem.  This workaround is not a good long-term solution for secure operations, but at least it got the clients up and running.  Perhaps someone else can use this workaround information, find the root cause of the problem, and figure out why TLS to the mail server is not working correctly.

---

### Post by ssivil on 2009-04-03
I experienced everything you stated in problem #2.  I contacted my ISP (wideopenwest), and the solution they are giving callers is to replace Thunderbird with Evolution.  I did.  Even though I refer Thunderbird (less resources), Ubuntu's default Evolution Mail works perfectly.

---

