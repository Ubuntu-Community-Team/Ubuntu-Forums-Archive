---
title: "Postfix/Dovecot - lost connection with [private/dovecot-lmtp]"
date: 2014-04-12
forum: Server Platforms
---

### Post by Marcus_Forsberg on 2014-04-12
Hello!

I've been working on this one for days now.
Running Ubuntu 12.04 on DigitalOcean. I'm a totally new to server management but it's been going OK so far and it's great fun, except...

I followed this tutorial to set up Postfix, Dovecot, ViMbAdmin and RoundCube: [https://rtcamp.com/tutorials/mail/server/postfix-dovecot-ubuntu/](https://rtcamp.com/tutorials/mail/server/postfix-dovecot-ubuntu/)

Everything has been working fine for almost a week so far until suddenly today my incoming mail started getting stuck in the queue.

The following message appears for all incoming email in the log:

> 
Apr 12 13:44:05 marcusforsberg postfix/qmgr[2616]: 62382160456: from=someone@somedomain.tld>, size=12193, nrcpt=1 (queue active)
Apr 12 13:44:05 marcusforsberg postfix/error[10785]: 62382160456: to=<info@marcusforsberg.net>, orig_to=<marcus@marcusforsberg.net>, relay=none, delay=259502, delays=259502/0/0/0, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with marcusforsberg.net[private/dovecot-lmtp] while receiving the initial server greeting)

I can send mail just fine. The only changes recently made was that I rebuilt my DigitalOcean droplet from a snapshot to increase disk space (both my web server and mail server are on the same VPS).
I also changed my DNS settings in order to add another domain pointing to my IP, but no changes were made to the MX records or anything.

[http://mxtoolbox.com/](http://mxtoolbox.com/) gives me OK on all relevant tests I've run.

I have no firewall that's blocking port 25 (at least *ufw status verbose* tells me I don't):

> 
25   ALLOW IN       Anywhere
25   ALLOW IN       Anywhere (v6)


25   ALLOW OUT    Anywhere
25   ALLOW OUT    Anywhere (v6)

Here is my Postfix main.cf: [http://pastebin.com/YtmD3Mdq](http://pastebin.com/YtmD3Mdq)
And master.cf: [http://pastebin.com/fyYKBvWs](http://pastebin.com/fyYKBvWs)

I've posted this on several other places with no luck, so I hope to find help here. Please do go easy on me, as I said, this is all new to me.
If any other logs, configuration files (dovecot?), or a look at my DNS setup is required, please let me know.

Thanks in advance!

---

### Post by Marcus_Forsberg on 2014-04-13
It turns out I had missed an error in dovecot.log:

> lmtp(11750): Fatal: Error reading configuration: Invalid settings: postmaster_address setting not given

After some searching I stumbled upon this blog post:

[http://projectnotedump.wordpress.com/2013/09/08/our-email-server-is-online/](http://projectnotedump.wordpress.com/2013/09/08/our-email-server-is-online/)

And it solved it all. Weird that this error so suddenly started to happen, but it all works now.

Moving on! :)

---

