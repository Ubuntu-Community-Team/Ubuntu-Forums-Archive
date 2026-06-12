---
title: "Postfix Configuration with DynDNS"
date: 2007-10-11
forum: Server Platforms
---

### Post by zcox on 2007-10-11
I'd like to set up an Ubuntu Server to test out at home.  I got LAMP set up perfectly - the 7.04 installer is great.  I have dynamic dns at dyndns.com with the domain xxx.kicks-***.net pointing to my IP (actual domain changed to protect the innocent).

Next I'd like to get a mail server running, so I can send emails from [email]user@xxx.kicks-***.net[/email] and receive emails to [email]user@xxx.kicks-***.net[/email].

I set up Postfix according to:

[https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html)

but no luck.  Emails to [email]user@xxx.kicks-***.net[/email] get returned with the following error:

Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 13): 554 5.7.1 <user@xxx.kicks-***.net>: Relay access denied

And emails going out from the server get stuck in the queue.

I'm pretty sure I need to set the relayhost to my ISP's SMTP server, which should be fine.  What do I need to set mydomain to, to receive emails on this server?

---

### Post by MJN on 2007-10-11
Post your config. You have likely either not told Postfix that you are the final destination for kicks-***.net and/or that you should be allowing non-authenticated remote mail to that domain.

The cause of outgoing mail not being sent will likely be hinted at in your logs (with no relayhost it should be attempting delivery itself so something must be stopping it, e.g. blocked port 25, DNS failures, config mistake etc etc).

Mathew

P.S. That HowTo has got to be the epitome of why I dislike many HowTo's - the main config section is just a list of answers to the wizard questions without any reasoning or explanation behind it... It's no wonder users get stuck when the thing doesn't work! (that's not a dig at you, it's not your fault - I can understand the temptation to use them when you want something that 'just works'... unfortunately that's often not the case!)

---

