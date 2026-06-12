---
title: "Outgoing email logging and control."
date: 2009-09-23
forum: Server Platforms
---

### Post by h6w on 2009-09-23
Hello,

I have an Ubuntu 9.04 server acting as a firewall, DNS, and DHCP server for our internet access.

We currently shift a large amount of emails in and out of the office, but particularly out.  This hasn't been a problem for us.  We only email those who request it, but the database that does that is large and sophisticated.   Mailouts larger than 100 are put into automatically generated mailing lists and sent from elsewhere outside our office, but we regularly send emails with 20-100 email addresses attached.

We recently tried shifting to an ISP with Ironports, and their Ironports system blocked us from sending too much email at a time.  I don't have any issue with them doing that.  We try to be a good email citizen also, with automatic processes for unsubscribing and deleting email addresses, etc, etc, etc.

However, since their Ironports blocked us, I must presume that someone here is emailing larger than appropriate levels.  I know someone must be doing it, but I have no way of proving this.

We tried running a SMTP relay with user/password access, but it kept rejecting perfectly good email addresses because servers were down, which was a pain.  But I understand this was a side-issue.

How can I track which user it is that's sending too much email?  How can I configure our server to stop whoever it is from sending too much email?

Currently we have no restrictions on sending email.  It just passes it through from internal to external.  I'd like to control, and maybe log the message that are getting sent out to ensure that we don't overload our ISP's restrictions on sending email.

Does anyone know of how I would go about doing this?

---

