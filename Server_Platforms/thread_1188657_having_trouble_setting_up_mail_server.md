---
title: "having trouble setting up mail server"
date: 2009-06-15
forum: Server Platforms
---

### Post by SodaAsh on 2009-06-15
hello i currently set up a mail server using postfix dovecot ssl but i cant seem to send and receive email.

i set up a domain name with DynDNS.com but im not sure how to set up the MX host... i followed there thing but it always says enter valid host name... do i need a MX host to make my mail server work or is there something else that i am doing wrong.

also i followed this website:     [http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p6](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p6)

---

### Post by briguy47 on 2009-06-16
> **SodaAsh said:**
> hello i currently set up a mail server using postfix dovecot ssl but i cant seem to send and receive email.

i set up a domain name with DynDNS.com but im not sure how to set up the MX host... i followed there thing but it always says enter valid host name... do i need a MX host to make my mail server work or is there something else that i am doing wrong.

also i followed this website:     [http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p6](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p6)


I recently setup a mail server using Postfix, Dovecot and SSL with DynDNS.  I didn't need to do ANYTHING with the MX host.  As long as you have the right ports forwarded through your firewall, you should be good to go.

Here are the default ports:

POP3 - port 110

IMAP - port 143

SMTP - port 25

HTTP - port 80

Secure SMTP (SSMTP) - port 465

Secure IMAP (IMAP4-SSL) - port 585

IMAP4 over SSL (IMAPS) - port 993

Secure POP3 (SSL-POP) - port 995

---

### Post by Cheesemill on 2009-06-16
You have to set up an MX record for your domain that points to your mail server, otherwise no-one will know which computer to send mail to for your domain.

This is usually done in the control panel of your DNS provider.

---

### Post by briguy47 on 2009-06-16
> **Cheesemill said:**
> You have to set up an MX record for your domain that points to your mail server, otherwise no-one will know which computer to send mail to for your domain.

This is usually done in the control panel of your DNS provider.

Forgive me if this sounds like a newb question, but is that required for every mail server.  The reason I ask, is that when I set up DynDNS to point to my domain/ip addy, I had a fully functioning mail server, but I'm sure that I never setup any MX record, largely because I don't know how. *blush*  Is it possible that there is a config on the local machine itself that might have taken care of this, that I might be forgetting?

I'm also interested, because I'm about to rebuild that server (Mail, Apache, FTP) from the ground up, and I don't want to hit that snag myself.

I appreciate the help!  :D

---

### Post by Cheesemill on 2009-06-16
Yes, this is a definite mail server requirement.

Every time someone sends you an email, their email server does a DNS lookup on your domain name to find out the address of your mail server (the so-called MX record).

Without an MX record for your domain there is no possible way for them to know which server handles your email. Period.

I suppose it is possible that DynDNS automatically sets up an MX record for you but you would have to check with them.

---

### Post by SodaAsh on 2009-06-17
okay i got it working but now i cant log into smtp... so i cant send any thing out... keeps telling me i enter the wrong password but i know i typed it correct ive been using this password for 20 years... the password for the email is the same as the user password or is it different? 

this is the error i get:

Unable to authenticate to SMTP server.
Bad authentication response from server.

Please enter SMTP password for "username" on
host xxxxxxxx.com

thank you

---

### Post by Bachstelze on 2009-06-17
Moved to Server Platforms.

---

### Post by SodaAsh on 2009-06-17
my mail log says this:

Jun 17 14:26:40 SERVER postfix/smtpd[3393]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun 17 14:26:40 SERVER postfix/smtpd[3393]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun 17 14:26:40 SERVER postfix/smtpd[3393]: warning: SASL authentication failure: Password verification failed
Jun 17 14:26:40 SERVER postfix/smtpd[3393]: warning: cpe-XX.XXX.XXX.XXX.socal.res.rr.com[XX.XXX.XXX.XXX]: SASL plain authentication failed: authentication failure
Jun 17 14:26:45 SERVER postfix/smtpd[3393]: disconnect from cpe-XX.XXX.XXX.XXX.socal.res.rr.com[XX.XXX.XXX.XXX]

---

