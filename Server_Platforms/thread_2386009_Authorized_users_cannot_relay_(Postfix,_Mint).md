---
title: "Authorized users cannot relay (Postfix, Mint)"
date: 2018-02-27
forum: Server Platforms
---

### Post by alavarre on 2018-02-27
How to authorize a SASL authenticated user to relay mail under Linux postfix smtpd?

Thank you for this forum.
~~~~~~~~~
We have two validated users for the mail server: [email]alavarre@mydomain.com[/email] and [email]andy@mydomain.com[/email].
• 	Each can receive mail (dovecot).
• 	Each can send mail to the other (postfix smtpd).
• 	Neither can send mail outside of the home domain (relay).
We  have enabled STARTTLS and it is working.
We have checked *main.cf*, in particular the *smtpd restrictions*. 
	We understand that we can enable relay from *mynetworks* 
	We do not want to add all the possible external IP addresses to *mynetworks*:
		rather would prefer to rely upon the user being authenticated on login by SASL. 
		*If he can log in to send mail within the domain he should likewise be authorized to relay traffic.*
~~~~~~~~~
The message returned to the client (evolution) is
	**Recipient address rejected: Server configuration problem **
We try a manual login using both *telnet* and *openssl*.
	These succeed, showing *starttls* is working and the users are SASL-accepted and can send mail within the domain.
		Connecting shows the certificate and TLS parameters.
		*ehlo* and *mail from* succeed:
			**mail from:<andy@privustech.com>**
			**250 2.1.0 Ok**
		*rcpt to:* fails
			**rcpt to:<alavarre@lavarre.org>**
			**554 5.7.1 <alavarre@lavarre.org>: Relay access denied**
~~~~~~~~~
We have checked *main.cf* and find nothing wrong.
	In particular, we have checked the *smtpd restrictions* and they appear to be in order:
	**smtpd_client_restrictions = 
	**smtpd_helo_restrictions = 
	**smtpd_sender_restrictions = 
	**smtpd_recipient_restrictions = 
	**smtpd_relay_restrictions =
			permit_mynetworks
			permit_sasl_authenticated
			reject_unauth_destination
	**smtp_sasl_auth_enable = yes
The last is most important, since we don't want to add all the possible external IP addresses to *mynetworks*, rather rely upon the user being authenticated on login by SASL. If he can log in to send mail within the domain he should likewise be authorized to relay traffic.

---

### Post by QIII on 2018-02-27
Hello!

Which release of Ubuntu are you using?

---

### Post by alavarre on 2018-02-28
Well, hello: checked /var/log/mail: unable to find saslauthd:

It was Disabled and Stopped! So Enabled and Start:
Now it works!

So end of drill.

The good news is I spent about six hours retweaking main.cf, making sure it is correct, and really getting to know  my machine better... :(

Thanks gain for the forum. Case closed.

---

