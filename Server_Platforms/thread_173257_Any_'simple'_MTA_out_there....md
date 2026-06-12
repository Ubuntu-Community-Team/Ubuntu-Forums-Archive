---
title: "Any 'simple' MTA out there..."
date: 2006-05-10
forum: Server Platforms
---

### Post by bushtor on 2006-05-10
Hi,

I just need to send short status messages from cron scripts to internet email addresses.  Do I really need to install beasts like postfix or sendmail just for this?

I know my ISP's smtp server address and I'd like to use their smtp server for this if possible.

Thanks for hints on how to use mailto in cron on a barebone ubuntu server ;-)

Tor

---

### Post by jimwillsher on 2006-05-10
Neither Sendmail nor Postfix requires much in the way of configuration, hough postfix is the easier one.

---

### Post by Sendervictorius on 2006-05-10
You could download mailx from synaptic. It is a traditional command-line-mode mail user agent.

---

### Post by bushtor on 2006-05-10
I did:

sudo apt-get install mailx

.. and was prompted to insert the server cd.  Then the postfix config wizard came up, but as I thought that mailx was something else than postfix, I selected 'No configuration'.  The installation finished by the line 'Setting up mailx... and seem to have been done w/o any errors.

How do I proceed from now, do I need to use/config postfix anyhow?

When I have this up and running, can I use this from, say, crontab to send a test message:

mail -s "This is a test message sent `date`" [email]myemail@domain.net[/email]

or do I use:

mail('myemail@domain.net', 'My Subject', 'This is a test message sent `date`');

Thanks for comments

Tor

---

### Post by Sendervictorius on 2006-05-11
The instructions on how to use mailx can be found here: [http://www.mkssoftware.com/docs/man1/mailx.1.asp](http://www.mkssoftware.com/docs/man1/mailx.1.asp)

You can get the same thing, although not as pretty, by firing up a terminal and typing man mailx. 

There is nearly always a man entry for any command-line conmmand - which explains how to use the command, what options do, etc etc.

You can also navigate through Gnome-help (system->help) application into "manual pages", and then select mailx from the list. But that takes too long for me, so I use terminal.

---

### Post by Sendervictorius on 2006-05-11
Had a quick read of the man pages, and came to the conclusion that mailx won't meet your requirements:

"It has no built-in facilities for sending messages to other systems, but combined with other programs (a mail routing agent, and a transport agent), it can send messages to other systems."

So, it looks like I steered you wrong. Sorry.

Some ideas:
1. If you can program scripting languages (like perl, python, or ruby), they come with modules that will programatically send emails - and don't require any local mail agents. They will send the email directly to your ISPs smtp gateway.

2. You could use telnet, and connect to your ISPs smtp server on port 25, redirecting a predefined file as stdin, to form your email content. That would be a one-line command in cron.

---

