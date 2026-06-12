---
title: "Server Responsive / But Does Not Respond to Requests / SSH"
date: 2015-01-08
forum: Server Platforms
---

### Post by bsntech on 2015-01-08
Been running a server for years.

A graphing system is used to monitor the server - network, load, cpu, etc.  A few days ago, I saw that the server started taking a heavy load.  Went from 0 up to 4 and stayed there for several hours.  The system was still responsive and I could login to it with no problem.  Was able to issue a reboot command (since the server is remote) and it restarted normally.

This server has the following:

mail (exim4)
dovecot (pop3 / imap)
mysql
apache2
bind9
spamassassin
clamav
virtualbox (for virtual machines)

In essence, it is a fully-featured server that does e-mail and web services.

Last night, graphing stopped about 9:30 pm.  I am not able to get access to the server at all.  Here is what is occurring:

- Server is responding to ping requests normally
- Server is accepting connections on the ports (mail, web, etc) but is not returning any kind of responses at all.  Doing a telnet to the ports will open the connection but the server doesn't respond with the typical 'go ahead' sort of text.
- Three of the four virtual servers are responsive and are completely working with zero problems
- SSH - when using putty - accepts the certificate and prompts for me the username.  Upon entering the username, the connection is terminated.

Looking for some assistance on where the troubleshooting steps may be.  The Virtual Server drives are loaded on a separate partition of the SSD hard drive.  So my first thoughts are I have either some bad spots in the memory modules - or there may be some kind of hard drive issue.  Possibly the fourth virtual server that I cannot get to is causing some kind of interference?

What kinds of things can be checked for in the logs - and which logs to check?  When the server started taking load a few days ago, I went through the syslog and didn't see anything out of the ordinary.  I also used "top" before restarting the server to see if I could figure out what was causing the load - but wasn't able to do so.  There was nothing out of the ordinary and CPU usage was only averaging about 8%.

---

### Post by volkswagner on 2015-01-08
Your early guesses seem logical. When I had a failing hard drive I had similar symptoms.

Check dmesg logs. Look for any I/O errors in syslog.

Since I'm no expert I tend to list logs in each directory in time order while also looking for large log files as well.

```
ls -alth /var/log
```
```
ls -alth /var/log/exim4
```
```
ls -alth /var/log/fsck
```
```
ls -alth /var/log/mysql
```
etc. blah, blah, blah

---

### Post by bsntech on 2015-01-08
Appreciate the reply.  Server was just restarted about an hour ago.  Looking at the syslog - it clear stops at 9:36 PM with the last line from Dovecot with an error  about an aborted login request due to a timeout.

Then it skips right to the time the server was booted back up.

Ran badblocks and it didn't come up with any problems, 0 bad blocks found.  It is an SSD drive - and although I know errors can occur on them, it is less likely than platter drives.  So I may be leaning more towards memory.

---

### Post by MAFoElffen on 2015-01-11
I'm curious and have questions...

What was wrong with getting dropped on ssh and being locked out. Was that refusal in the logs?

Next, what ports does the host show open? What ports from the virtual servers?

Did you find out what was happening with the fourth virtual server? Wondering if anything from that could have been a factor... Did you say your virtual's were running in VirtualBox?

You said the serevr host's cpu load seemed okay, but what was the network load at the time? (Thinking collisions or any network type errors...) Since from VirtualBox- NAT?

---

