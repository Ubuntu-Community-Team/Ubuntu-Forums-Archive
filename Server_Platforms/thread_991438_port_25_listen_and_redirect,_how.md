---
title: "port 25 listen and redirect, how?"
date: 2008-11-23
forum: Server Platforms
---

### Post by alienseer23 on 2008-11-23
I want to provide incoming smtp redirects, so people behind a port 25 firewall block could use my server as a listening host on port25 that redirects smtp traffic to their server on port xx. 

The idea is to provide this service for free, and charge a small fee for backups and large quotas.

Does anybody have a ready solution for that?

---

### Post by Philio on 2008-11-23
If the user has port 25 blocked on their connection you would surely need to setup your SMTP server on an alternative port?

You would probably set this up with the same principle as a backup MX server. How to set it up would depend on the mail server your going to use for this. A quick Google search shows up guides for all the major MTAs so you shouldn't have a problem doing this.

---

### Post by alienseer23 on 2008-11-24
I'm using postfix. So I can cause postfix to (obviously) listen on port 25 and then "bounce" it to another server? Wouldn't I have to store the mail and then wait for them to log in and grab what's there?

<<google google google>>

---

### Post by Philio on 2008-11-24
Try this: [http://samat.org/node/configuring_postfix_to_act_as_a_backup_mx_server](http://samat.org/node/configuring_postfix_to_act_as_a_backup_mx_server)

Looks like exactly what you need, also includes a bit about port blocking.

---

### Post by CrucifiedEgo on 2008-11-24
The standard solution here is to use the SMTP Submission port on 587.  In fact, all you have to do is comment out the 'submission' line in master.cf(2nd line) and restart, and poke a hole in your firewall.  nothing else to it, and you can feel good about following RFCs.

---

### Post by HermanAB on 2008-11-24
Yup, the above will work for forwarding to another server.

If you have a problem with users who want to send mail through your SMTP server but cannot because their ISP blocks it, then the better solution is to use SSL.  That will allow laptop users to roam around the world without having to change their settings all the time and they will be secure when they use WiFi in a coffee shop. 

Eg:
IMAPS = port 993 (instead of IMAP on 143)
SMTPS = port 465 (instead of SMTP on 25)
HTTPS = port 443 (instead of HTTP on 80)

A common crummy solution is to give Postfix a second listener on port 2525, but SSL is easy and much better, though it means that you need to purchase a certificate.

Cheers,

Herman

---

### Post by CrucifiedEgo on 2008-11-24
> **HermanAB said:**
> 
A common crummy solution is to give Postfix a second listener on port 2525, but SSL is easy and much better, though it means that you need to purchase a certificate.

This isn't a crummy solution (using 2525 is, however.)  The standard for SMTP submission is 587, per RFC 2476 ([http://www.ietf.org/rfc/rfc2476.txt](http://www.ietf.org/rfc/rfc2476.txt)).  SSL is optional on this port, and can be easily enabled by uncommenting the "#  -o smtpd_tls_security_level=encrypt" line in master.cf.

Edit: sorry, don't mean to be harsh.  I'm a bit of an SMTP RFC nazi, having worked in abuse for an email provider for a couple of years.

---

### Post by HermanAB on 2008-11-24
A few years ago, I noticed that IANA had their mail server listening on port 2525 as an ISP block workaround.  That was quite funny to me and I have done the same ever since on my own mail server just as a way to help debug things when the SSL connection won't work.

---

### Post by alienseer23 on 2008-11-25
wow, thank you guys for the great responses, I've not had the time to test any of this, but I certainly appreciate the help, hopefully over the holiday I'll get this implemented. Thanks again!

---

