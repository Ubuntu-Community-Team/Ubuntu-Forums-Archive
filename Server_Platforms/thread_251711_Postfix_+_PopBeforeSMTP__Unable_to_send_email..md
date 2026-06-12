---
title: "Postfix + PopBeforeSMTP : Unable to send email."
date: 2006-09-05
forum: Server Platforms
---

### Post by prodsacnetworking on 2006-09-05
Hi, I installed a mail server:
Ubuntu 6.06 srv, Postfix +MySQL, Courier IMAP+POP3, AMAVIS, SPamAssassin, Clam...

When the users are locally (at the office or by VPN) it workfs fine. No error logs anywhere.
When I install and configure pop-before-smtp, everything is still fine... but laptops users (outlook 2003) are'nt able to send using SMTP connct with auth..

the log reading by pop-before works well:
postmap -q ip.add.re.ss hash:/etc/postfix/pop-before-smtp
ok

Like I said the VPN works fine, but some people does'nt undestand that they need to connect... 

What logs or files do you  need to help? Thanks.

Marc

---

### Post by gruepig on 2006-09-06
I haven't used pop-before-smtp in a long time ....

Are IPs getting added to /etc/postfix/pop-before-smtp?  What's in your pop-before-smtp conf file?  What does the pop-before-smtp line in your postfix/main.cf file say, and is it before the relevant rejects?

Mail may be logging to different places, depending on how it's configured.  Check /var/log/mail.log and mail.err for a start.

(By the way, you might consider smtp auth (saslauthd) rather than pop-before-smtp.  It might be harder to configure, but I've found it's more intuitive for email users than pop-before-smtp.  I've set it up with postfix/cyrus, but not postfix/courier.  Looks like this [http://linox.be/index.php/2005/07/25/60/](http://linox.be/index.php/2005/07/25/60/) might be a start towards setting it up.)

---

### Post by prodsacnetworking on 2006-09-06
Thanks I'M gonna check it out.

---

