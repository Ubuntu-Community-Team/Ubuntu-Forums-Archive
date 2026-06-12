---
title: "emails continuously build in queque"
date: 2008-10-06
forum: Server Platforms
---

### Post by jay0316 on 2008-10-06
We had sendmail running on our Ubuntu 7.10 Web Server with Webmin, and I had written a php script to send about 500 emails out from our database using the php mail function.  

After sending them out, messages continued to build up in the queue and even doubled.  We were eventually blacklisted because of the HELOing that was going on possibly related to Debian bug #375787 according to the blacklister. 

So, we shut sendmail down and were able to get off of the black list.  The problem is that we have the server running again with the port blocked at the firewall and the emails are still generating in the queue.  

We deleted the emails in the queue and they come back.  We tried rebooting the server, and that didn&#8217;t work.  We also uninstalled sendmail and installed postfix, but the emails are now building up in postfix&#8217;s queue (currently 1,076 of them).

We are new to hosting a webserver and don&#8217;t know where to start in solving this issue.  I&#8217;ve done several searches online and have come up short.  I&#8217;m hoping that someone here will be able to offer some good advice.

We think that either the php script is still running, or there is a process that is still running which could be generating them.

Any suggestions?

---

### Post by alastair on 2008-10-06
Step 1 :

Look in your mail server log file for information on what mail is being queued.

If you were running Postfix mail server, I would do something like this :

a) Open a terminal
b) Type : sudo tail -f /var/log/mail.log
c) Hit <ENTER> a few times to put some newline space in
d) Wait ... until you see a message printed

This will be a mail message being queued probably. Watch for a while and see what messages appear. Then post the log messages here.

Alastair

---

### Post by jay0316 on 2008-10-08
I tried running that command from Webmin's command shell and it just sat there and ran.  The page didn't refresh.  I will try to run it directly from the server if it's still necessary.  However, I can see the queue within Webmin's Postfix Module.  I attached an image with several of the messages that are currently sitting in there.

[IMG]http://www.coastalpet.com/queue.jpg[/IMG]

I hope this info will help.  If not let me know and I'll try running the command directly on the server.

Additional info: I found out that our I.T. department did not reboot the system.  They had something come up and didn't get to it.  So, that may be something we need to try as well.

---

### Post by jay0316 on 2008-10-08
Update: 

Server has been rebooted and we deleted the messages. We are going to see if the messages show up again tomorrow.

The emails all appear to be the same ones that were being called in the original php script.

---

### Post by jay0316 on 2008-10-08
Is there anything else we can check while we are waiting to see if the emails generate again?

We are going to need to figure out why this is happening so that we don't have this issue when we go to send another email.

---

### Post by alastair on 2008-10-08
Well, shame it's only webmin ...

Nevertheless, the problem is apparent - a lot of mails getting "connection timed out" i.e.

from : [email]www-data@coastalpet.net[/email] 
to : [email]waynepet@verizon.net[/email]

etc. The mails are attempting to connect to the recipients mail server, but not getting through.

Why are some status fields empty? e.g. one to a "gmail" address? Were they received?

Why not log into a shell on this system and try manually sending a mail i.e. below, do not type the ">", just what is after that) :

telnet relay.verizon.net 25

> EHLO youremail.com
..
> MAIL FROM:<you@yourhost.com>
..
> RCPT TO:<waynepet@verizon.net>
...
> DATA
.. write something ... end with a "." on a newline

Does that work?

Maybe your ISP is blocking your port 25 emails ... or a firewall somewhere.

Alastair

P.S. If you cannot figure it out, pay a friendly neighbourhood sysadmin to have a look :-)

---

