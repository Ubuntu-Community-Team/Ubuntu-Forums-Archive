---
title: "Postfix SMTP mail is sent to SPAM"
date: 2015-01-29
forum: Server Platforms
---

### Post by aravind-vdsi on 2015-01-29
I have installed postfix mail server in ubuntu machine. I configured the mail server as well as DNS properly.


Mails are sent from our mail server properly, but all the mails are listed in the spam folder(in Yahoo & Outlook). It is listing properly in the inbox in Gmail.


I have implemented the following methodologies to prevent the SPAM, which is as follows,


	* SPF
	* DKIM
	* Domain Keys
	
After the above implementation, Headers of the email is as follows,


	Authentication-Results: hotmail.com; spf=pass (sender IP is xx.xx.xx.xx)   
    smtp.mailfrom=test@maildomain.com; dkim=pass header.d=maildomain.com; x-hmca=pass   
    header.id=test@maildomain.com
	DomainKey-Signature: a=rsa-sha1; s=mail; d=maildomain.com; c=simple; q=dns;	b=key
	DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=maildomain.com;s=mail;   
    t=1422532895;bh=W+pft8+RS+1CGEuNXIA20Br1EeZE1qaANUx3o6nvb3E=;h=From:
    To:Subject:From;b=key
	
I have checked the several email testing service to detect why our emails are marked as spam and the result is as follows,


	* Sent the mail to the "check-auth@verifier.port25.com" and got 
       the authentication report mail.
		==========================================================
		Summary of Results
		==========================================================
		SPF check:          pass
		DomainKeys check:   pass
		DKIM check:         pass
		Sender-ID check:    pass
		SpamAssassin check: ham


	* Tested the email with "https://www.mail-tester.com/" and got the score "9.3/10".


	* Checked our mail server IP address in 
      "http://whatismyipaddress.com/blacklist-check" and our IP address is 
       not blacklisted.


Note:


* Mailserver hosted in Amazon EC2 instance with a static IP address (connect to internet, and all traffic ports are opened for inbound and outbound in   security groups).


* Mail sending service limit has been increased properly(Support query has been raised to amazon and the mail restriction has been removed in our account).


* I am using self signed certificate in my Mail server.


Can any one let us know, how to prevent the email sent as spam. Is there anything, we need to look into our mail server configuration?

---

### Post by lisati on 2015-01-29
Do you have [reverse DNS]("http://en.wikipedia.org/wiki/Reverse_DNS_lookup") set up? Some email providers check it as part of their filtering process.

WhatIsMyIpAddress is a useful resource. I also use [MultiRBL.valli.org]("http://multirbl.valli.org") and a couple of others.

edit: I've also moved your thread to the server section, where it might have a better chance of getting a response than "Forum Feedback and Help"

---

### Post by SeijiSensei on 2015-01-29
Reverse DNS is pretty much mandatory these days.  If possible, the name<->IP matches should be identical in both directions.

Have you checked your IP at [http://mxtoolbox.com/blacklists.aspx?](http://mxtoolbox.com/blacklists.aspx?)

Can we see a representative SpamAssassin report giving the rules, if any, the message trips?  Something like this:
```
BAYES_95 3.20, CC_URI 2.00, DSN_NO_MIMEVERSION 2.00, MSGID_FROM_MTA_HEADER 0.00, RCVD_IN_BL_SPAMCOP_NET 1.35, RCVD_IN_MSPIKE_BL 0.01, RCVD_IN_MSPIKE_L5 3.80, RCVD_IN_RP_RNBL 1.31, RCVD_IN_XBL 0.38, SUBJ_STARTS_GET 1.00, URIBL_BLACK 1.70, URIBL_DBL_SPAM 2.50, URIBL_JP_SURBL 1.25, URIBL_SBL 1.62, URIBL_SBL_A 0.10, URIBL_WS_SURBL 1.61
```
This one scores a 23 on my server.  I've seen some spams push 50.  I start tagging at 4. (A couple of those rules like CC_URI are my own; the rest are standard SA.)

---

### Post by aravind-vdsi on 2015-01-29
Thanks for your response,

Reverse dns lookup for my mail server is also working fine. I have checked it in the following way,

  * nslookup maildomain.com --> It gives me the ip address
  * nslookup ipaddress --> It gives me maildomain.com

I have checked the following websites for the blacklist checking and my mail server is not blacklisted in all the result.

   * [http://multirbl.valli.org/](http://multirbl.valli.org/)
   * [http://mxtoolbox.com/blacklists.aspx](http://mxtoolbox.com/blacklists.aspx)

@SeijiSensei , I haven't made any configuration for SpamAssassin in my mailserver, Is it necessary to implement it in my mail server?

Is there any other configuration/change has to be made in our side ?

---

### Post by SeijiSensei on 2015-01-29
SpamAssassin is primarily used to filter inbound messages.  I was asking whether you knew how the messages you sent that were tagged as spam on other servers were scored.  That way you could see which features of the messages might have tripped the anti-spam rules on the recipients' servers.

---

### Post by TopCoder01 on 2015-08-23
Here's a list of other places you can test, by sending an email to:

[EMAIL="mailtest@unlocktheinbox.com"]mailtest@unlocktheinbox.com[/EMAIL]
[EMAIL="sa-test@sendmail.net"]sa-test@sendmail.net[/EMAIL]
[EMAIL="dkim-test@altn.com"]dkim-test@altn.com[/EMAIL] 
[EMAIL="check-auth@verifier.port25.com"]check-auth@verifier.port25.com[/EMAIL]
[EMAIL="autorespond+dkim@dk.elandsys.com"]autorespond+dkim@dk.elandsys.com[/EMAIL]
[EMAIL="dktest@exhalus.net"]dktest@exhalus.net[/EMAIL], 
[EMAIL="nelson-sbl-test@crynwr.com"]nelson-sbl-test@crynwr.com[/EMAIL]

Other Email Tools: [Mailtester]("https://www.unlocktheinbox.com/mail-tester/") | [SPF Wizard]("https://www.unlocktheinbox.com/spfwizard/") | [DMARC Wizard]("https://www.unlocktheinbox.com/dmarcwizard/") | [DKIM Wizard]("https://www.unlocktheinbox.com/dkimwizard/") | [Email Identifier]("https://www.unlocktheinbox.com/emailidentifieralignments/")

I always keep this last handy. Some are better then others - but it's good to get a second opinion.

---

