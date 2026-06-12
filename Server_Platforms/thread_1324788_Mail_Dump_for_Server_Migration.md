---
title: "Mail Dump for Server Migration"
date: 2009-11-12
forum: Server Platforms
---

### Post by Oatworm on 2009-11-12
I'm about to begin (hold your laughter 'til the end, please) a migration from a single Exchange 2003 server to a different Exchange 2007 server.  At the end of the day, there will only be one mail server on site.  While this migration is taking place, I want to route all mail to a different server that does the following:

- Holds on to all incoming mail in a queue until I'm done migrating.  This means that it shouldn't check to see if the recipient mail address exists; it doesn't matter.  It should just accept everything and hold on to it.
- At the flip of a switch (or after editing a configuration file and restarting the Postfix service - whatever), I want it to relay everything in that queue to the Exchange 2007 server, which will have the user's mailboxes, as well as appropriate spam and anti-virus filtering software installed and properly configured for my network.

The motivation behind this is to keep mail-receiving downtime to a minimum - while the migration is taking place, I don't want the Exchange servers doing *anything* other than moving mailboxes in order to reduce possible hiccups.  Plus, I don't want to have to rely on Exchange's ability to "intelligently" route mail to the right server while mailboxes are moving from one server to another.

Understandably, there's not a whole lot of documentation that I can find about Postfix to really accommodate this scenario.  Is there anybody that can point me in the right direction?  I don't mind reading documentation - I just need to whittle some of it down to the more relevant parts.  It looks like smtpd is roughly where I want to start, if that helps.  I have time to try a few things, so no major rush.

As an aside, yes, I know about Zimbra, OpenXchange, and all that good stuff.  Unfortunately, full Outlook compatibility is a must, as is full OMA-push style mobile support, and the yearly subscriptions for things like Zimbra end up being more expensive for me than just buying a really expensive set of Exchange licensing and CALs in one shot since we have a five year refresh cycle on software here.  So, if your answer is "don't use Exchange", I'll nod appreciatively, say, "Yeah, I'd love to," then go to the next post.

Thanks in advance!

---

### Post by cviniciusm on 2009-11-13
Hello,
 
I hope this help, yet ([http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)), perhaps can point to the right direction:
"Canonical versus hosted versus other domains
Most Postfix systems are **final destination** for only a few domain names. These include the hostnames and [the IP addresses] of the machine that Postfix runs on, and sometimes also include the parent domain of the hostname. The remainder of this document will refer to these domains as the [canonical domains]("http://ubuntuforums.org/VIRTUAL_README.html#canonical"). They are usually implemented with the Postfix [local domain]("http://ubuntuforums.org/ADDRESS_CLASS_README.html#local_domain_class") address class, as defined in the [ADDRESS_CLASS_README]("http://ubuntuforums.org/ADDRESS_CLASS_README.html") file.
Besides the [canonical domains]("http://ubuntuforums.org/VIRTUAL_README.html#canonical"), Postfix can be configured to be **final destination** for any number of additional domains. These domains are called hosted, because they are not directly associated with the name of the machine itself. Hosted domains are usually implemented with the [virtual alias domain]("http://ubuntuforums.org/ADDRESS_CLASS_README.html#virtual_alias_class") address class and/or with the [virtual mailbox domain]("http://ubuntuforums.org/ADDRESS_CLASS_README.html#virtual_mailbox_class") address class, as defined in the [ADDRESS_CLASS_README]("http://ubuntuforums.org/ADDRESS_CLASS_README.html") file. 
But wait! There is more. Postfix can be configured as a backup MX host for other domains. In this case Postfix is **not the final destination** for those domains. It merely queues the mail when the primary MX host is down, and forwards the mail when the primary MX host becomes available. This function is implemented with the [relay domain]("http://ubuntuforums.org/ADDRESS_CLASS_README.html#relay_domain_class") address class, as defined in the [ADDRESS_CLASS_README]("http://ubuntuforums.org/ADDRESS_CLASS_README.html") file. 
Finally, Postfix can be configured as a transit host for sending mail across the internet. Obviously, Postfix is not final destination for such mail. This function is available only for authorized clients and/or users, and is implemented by the [default domain]("http://ubuntuforums.org/ADDRESS_CLASS_README.html#default_domain_class") address class, as defined in the [ADDRESS_CLASS_README]("http://ubuntuforums.org/ADDRESS_CLASS_README.html") file. 
"
 
 
Regards.

---

### Post by Oatworm on 2009-11-15
The relay_domain_class parameter looks absolutely *perfect*!  I'll take a stab at it on Monday and let you know what happens!

Thanks!

---

### Post by Oatworm on 2009-11-19
Okay - I think I figured it out, though it took a little bit.  The key parts of main.cf that anybody might care about:

```
myhostname = tempmail.test.local
mydestination = tempmail.test.local, localhost.test.local, localhost
relay_domains = myactualdomain.com
relay_transport = smtp:[IP address of the mail server]
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
inet_interfaces = all
proxy_interfaces = [My public IP]
```

Please note that there were other options that dpkg-reconfigure threw in there, but I left them alone.  The big keys are the following, near as I could figure out:
[LIST]
[*]Do not use your public e-mail domain as one of the "mydestination" listings, otherwise Postfix thinks it's responsible for delivering that e-mail in a mailbox on the system.  This will lead to "mailbox does not exist on the server" errors.
[*]Set relay_domains to your actual working domain.
[*]Set relay_transport to the IP address of your mail server.  Note that, if you feed it a bad value, it'll just queue it up until a good address is fed in and Postfix restarts again - consequently, setting it to a ridiculous value (i.e. a private IP that's not accessible on your local network) seems like an effective way to force Postfix into queue mode.  Then, once you're done migrating, change it to the IP address of the new mail server and restart the Postfix service.  Once you do that, it'll eventually start blasting whatever mail server you are now pointed at.  If you want to speed the process up a bit, give it a "postfix flush" and you'll be right as rain.
[*]Don't let the mail server trust anybody but itself for regular relaying in this scenario.  Presumably nobody in the company is sending mail out - the point is to just queue up incoming mail while the migration is completed.
[*]If you don't turn on inet_interfaces, it won't listen on port 25.
[*]Not sure if proxy_interfaces does anything, but the Postfix documentation suggested using it if you're behind a NAT, which I am, so I did.
[/LIST]

Any cautionary notes that people would like to add?

---

