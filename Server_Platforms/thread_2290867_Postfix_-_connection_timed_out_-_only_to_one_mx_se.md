---
title: "Postfix - connection timed out - only to one mx server, three separate clients"
date: 2015-08-16
forum: Server Platforms
---

### Post by Grant_Millar on 2015-08-16
Hi all

My Ubuntu server with postfix works well but fails to send email to one mx server (three separate clients on that server) with a "connection timed out"

One client is an insurance broker, one a regional council and one a mining company, I just figured out today that all use the "mailcontrol.com" mx server.

Aug 15 15:26:35 server postfix/smtp[11342]: connect to cust11646-1.in.mailcontrol.COM[116.50.57.190]:25: Connection timed out
Aug 15 15:27:05 server postfix/smtp[11342]: connect to cust11646-2.in.mailcontrol.COM[116.50.58.190]:25: Connection timed out

Jul 26 11:00:43 server postfix/smtp[20287]: connect to cust28941-1.in.mailcontrol.com[116.50.57.190]:25: Connection timed out
Jul 26 11:01:13 server postfix/smtp[20289]: connect to cust28941-2.in.mailcontrol.com[116.50.58.190]:25: Connection timed out

And the third resolved to cust35828-1.in.mailcontrol.com, this one was a while ago and I can't find it in my logs

All other ins and outs are fine, all three issues are with the one server.

I have even tried putting postfix back to default, but had the same issue.

Any ideas what setting to tweak so I can send an email to anyone on mailcontrol.com server now and into the future?

Thanks

---

### Post by SeijiSensei on 2015-08-16
I suggest you check with mailcontrol.com.  Perhaps they are blocking you for some reason.  I can connect to port 25 on that IP address from my public mail server.  Have you checked your IP address at mxtoolbox.com?  Are you in any anti-spam lists?

---

### Post by Grant_Millar on 2015-08-16
Sensei

I can connect to port 25 at mailcontrol.com via telnet.

I am not in any blacklist, I checked that as one of the first things.

I will try the suppost team at mailcontrol and see if they have an answer, I doubt that I will be a high priority

Cheers

---

### Post by SeijiSensei on 2015-08-17
> **Grant_Millar said:**
> Sensei

I can connect to port 25 at mailcontrol.com via telnet.

I am not in any blacklist, I checked that as one of the first things.

I will try the suppost team at mailcontrol and see if they have an answer, I doubt that I will be a high priority

Cheers

If you can connect with telnet, then why the Postfix time out must happen during the transaction.

Try simulating an entire SMTP exchange where you send a message with to one of the problematic addresses:

```

$ telnet 116.50.57.190 25
[remote sends banner]
ehlo name.of.your.server
[reply]
mail from: you@yourdomain.com
[reply?]
rcpt to: someone@problematic-domain.com
[reply?]
data
This is a test message.
.
[does that go through?]

```

---

### Post by Grant_Millar on 2015-08-18
Sensei

I can telnet to "mailcontrol.com", but not to any of the problem IPs.

When connected to "mailcontrol.com" I cannot send email as I get a "relaying denied" message as I am trying to send mail to someone on a different domain.

I am having trouble registering with websense as the registration email cannot get through

Aug 19 07:47:28 server postfix/smtpd[21996]: warning: hostname esgsd5.websense.com does not resolve to address 204.15.65.154: No address associated with hostname
Aug 19 07:47:28 server postfix/smtpd[21996]: connect from unknown[204.15.65.154]
Aug 19 07:47:29 server postfix/smtpd[21996]: Anonymous TLS connection established from unknown[204.15.65.154]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)
Aug 19 07:47:29 server postfix/smtpd[21996]: NOQUEUE: reject: RCPT from unknown[204.15.65.154]: 554 5.7.1 Client host rejected: cannot find your hostname, [204.15.65.154]; from=<donotreply@websense.com> to=<XXXXXXXXXX@emsqld.com> proto=ESMTP helo=<esgsd1.websense.com>
Aug 19 07:47:30 server postfix/smtpd[21996]: disconnect from unknown[204.15.65.154]

---

### Post by SeijiSensei on 2015-08-18
It looks like your server does not have reverse DNS (IP =>hostname) correctly set up. Many servers will refuse to accept mail from machines that do not have matching forward and reverse DNS configured. This is a problem that can only be resolved between you and your ISP since the ISP has control over reverse resolution.

---

### Post by TopCoder01 on 2015-08-22
204.15.65.154 has a PTR record pointing to esgsd5.websense.com, but esgsd5.websense.com doesn't have an A record (so it's issuing a warning) - and looks like it rejects based of that reason also. 

I just created an account on websense, I was able to get the email. I did run it through [EMAIL="mailtest@unlocktheinbox.com"]mailtest@unlocktheinbox.com[/EMAIL] ([MailTester]("https://www.unlocktheinbox.com/mail-tester/")) - Everything looked great, except that it reported that the certificate on it's mail server is mismatched with all 4 MX Records. 

cust26029-5.in.mailcontrol.com
cust26029-6.in.mailcontrol.com
cust26029-1.in.mailcontrol.com
cust26029-2.in.mailcontrol.com

Just showing one of them below - data will just look redundant - since there were no differences - as you can see only port 25 appears to be accepting communication.

[TABLE="width: 100%"]
[TR="bgcolor: #5379B7"]
[TD="colspan: 2"][COLOR=#ffffff]Email Port Checks for: cust26029-5.in.mailcontrol.com[/COLOR][/TD]
[/TR]
[TR="bgcolor: #35467C"]
[TD][COLOR=#ffffff]Protocol[/COLOR][/TD]
[TD][COLOR=#ffffff]Results[/COLOR][/TD]
[/TR]
[TR]
[TD]SMTP (Port 25):[/TD]
[TD]Connection Established[/TD]
[/TR]
[TR]
[TD] - Extensions:[/TD]
[TD]ENHANCEDSTATUSCODES, PIPELINING, 8BITMIME, SIZE, DSN, ETRN, STARTTLS, DELIVERBY, HELP[/TD]
[/TR]
[TR]
[TD] - Server Greeting:[/TD]
[TD]cluster-e.mailcontrol.com ESMTP MailControl[/TD]
[/TR]
[TR]
[TD] - SSL Hostname:[/TD]
[TD]*.mailcontrol.com[/TD]
[/TR]
[TR]
[TD] - SSL Subject:[/TD]
[TD]CN=*.mailcontrol.com, O=Websense INC., L=San Diego, S=CA, C=US[/TD]
[/TR]
[TR]
[TD] - SSL Issuer:[/TD]
[TD]CN=DigiCert SHA2 High Assurance Server CA, OU=www.digicert.com, O=DigiCert Inc, C=US[/TD]
[/TR]
[TR]
[TD] - SMTP Banner Reverse DNS Check:[/TD]
[TD]Passed[/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000] - SSL Error:[/COLOR][/TD]
[TD][COLOR=#ff0000]Certificate Does Not Match Hostname[/COLOR][/TD]
[/TR]
[TR]
[TD] - SSL Key Size:[/TD]
[TD]2048[/TD]
[/TR]
[TR]
[TD] - SSLv3 Disabled:[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]MAIL Submission (Port 587):[/TD]
[TD]Unable to Establish Connection[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]SMTP SSL (Port 465):[/TD]
[TD]Unable to Establish Connection[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]POP3 (Port 110):[/TD]
[TD]Unable to Establish Connection[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]POP3 SSL (Port 995):[/TD]
[TD]Unable to Establish Connection[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]IMAP (Port 143):[/TD]
[TD]Unable to Establish Connection[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]IMAP SSL (Port 993):[/TD]
[TD]Unable to Establish Connection[/TD]
[/TR]
[/TABLE]

I doubled checked the findings with sslshopper.. 

[https://www.sslshopper.com/ssl-checker.html#hostname=cust26029-5.in.mailcontrol.com](https://www.sslshopper.com/ssl-checker.html#hostname=cust26029-5.in.mailcontrol.com)


[TABLE="class: checker_messages, width: 725"]
[TR]
[TD]**None of the common names in the certificate match the name that was entered (cust26029-5.in.mailcontrol.com). You may receive an error when accessing this site in a web browser. [Learn more about name mismatch errors]("https://www.sslshopper.com/ssl-certificate-name-mismatch-error.html").**[/TD]
[/TR]
[/TABLE]

If you talk to MailControl.com support, you might want to mention this to them also.

[SPF Wizard]("https://www.unlocktheinbox.com/spfwizard/") | [DMARC Wizard]("https://www.unlocktheinbox.com/dmarcwizard/") | [DKIM Wizard]("https://www.unlocktheinbox.com/dkimwizard/") | [Email Identifier]("https://www.unlocktheinbox.com/emailidentifieralignments/")

---

