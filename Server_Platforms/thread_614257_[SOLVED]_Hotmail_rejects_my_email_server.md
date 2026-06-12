---
title: "[SOLVED] Hotmail rejects my email server"
date: 2007-11-15
forum: Server Platforms
---

### Post by ruibernardo on 2007-11-15
Hi folks,

I recently created a website to make updates and packages from the repositories available to users that do not have an internet connection and the one they have is not Ubuntu (Windows for example). I'm using a Gutsy LAMP server, drupal5 and the default mail server on ubuntu-server (postfix).

All is setup and running, but I'm running from a dynamic IP and using DynDNS. 

The real problem is that people have to register with an email account to be able to use the site, and many of them use hotmail, but hotmail rejects the mail that my server sends. :(
> Nov 16 00:42:12 server postfix/smtp[17691]: 5BE80C3D8: to=<someones_email@hotmail.com>, relay=mx1.hotmail.com[65.54.245.8]:25, delay=2.2, delays=0.49/0.11/1.4/0.21, dsn=5.0.0, status=bounced (host mx1.hotmail.com[65.54.245.8] said: 550 DY-001 **Mail rejected by Windows Live Hotmail for policy reasons. We generally do not accept email from dynamic IP's** as they are not typically used to deliver unauthenticated SMTP e-mail to an Internet mail server. [http://www.spamhaus.org](http://www.spamhaus.org) maintains lists of dynamic and residential IP addresses. If you are not an email/network admin please contact your E-mail/Internet Service Provider for help. Email/network admins, please visit [http://postmaster.live.com](http://postmaster.live.com) for email delivery information and support (in reply to MAIL FROM command))
Nov 16 00:42:12 server postfix/smtp[17691]: 5BE80C3D8: lost connection with mx1.hotmail.com[65.54.245.8] while sending RCPT TO
Is there a way to avoid this? Thanks!

---

### Post by Zeosa on 2007-11-15
You'll find quite a few others than hotmail do the same thing (heck, I do it on the smtp servers under my control too)

The only real way around it is to route your outbound mail through another smart host which isn't on a blocklist and isn't dynamic (such as your isp's)

---

### Post by ruibernardo on 2007-11-15
Thanks for your reply Zeosa. I'll check if my ISP can do this. If it can, I use my email account from my ISP for the outbound mail?

---

### Post by Zeosa on 2007-11-15
Depending on which MTA your running, it should be fairly trivial to set it up to relay via your ISP .....google 'smart host' along with the name of the software (postfix, sendmail etc) your using and you're sure to find instructions for setting it up .....

Depending on how your ISP handles mail, you may have to set up your box to authenticate to their server prior to sending.....

---

### Post by ruibernardo on 2007-11-16
Thank you for this info, Zeosa. Greatly appreciated.

---

### Post by MJN on 2007-11-16
Just to add to Zeosa's correct advise, given you're using Postfix the directive you're after is **relayhost = [name.of.relay.server]** (note from the docs that the [] brackets are required in order to force an A record lookup of the name given as opposed to an MX record).
 
Mathew

---

### Post by ruibernardo on 2007-11-30
Thank you all for your answers, they really helped me. 

I delayed the resolution of this problem, but half the users were using mail accounts from servers that rejected my DynDNS IP. To whoever have the same problem and find this thread here is how I solved my problem.

I created a CA certificate so I could connect to my ISP smtp server with TLS and I moved the new certificate to a directory inside the /etc/postfix/ directory:
```
sudo openssl req -new -x509 -nodes -out smtp-client.pem -keyout smtp-client.pem -days 10000
sudo mkdir /etc/postfix/tls
sudo cp ./CAcert.pem  /etc/postfix/tls/CAcert.pem
```I edited my main.cf file and added the options to use the certificate, enabled relayhost for the mail that was to be sent to the Internet, and mapped the user account and password on my ISP SMTP server.
```
relayhost = smtpa.netcabo.pt
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/saslpw
smtp_tls_CAfile = /etc/postfix/tls/CAcert.pem
tls_random_source = dev:/dev/urandom
# the following option is left blank intencionally so other authentication modes can work.
smtp_sasl_security_options =
smtp_tls_loglevel = 2
```I had to create the file that have the mail account name and password at my ISP SMTP server (/etc/postfix/saslpw). Created the file:
```
sudo nano /etc/postfix/saslpw
```And added something like:
```
smtp.myisp.tld my.mail.account@myisp.tld:account_password
```And created the hash if this file to be used by postfix:
```
sudo postmap /etc/postfix/saslpw
```This will create a saslpw.db.

To make the delivery of the mail that was to be sent to the Internet I had to use address and virtual mapping ("man generic" and "man virtual"). So I also added the options to use this on my main.conf file:
```
smtp_generic_maps = hash:/etc/postfix/generic
virtual_alias_maps = hash:/etc/postfix/virtual
```Created both files. In /etc/postfix/generic (delivered):
```
system_user@hostname my.mail.account@myisp.tld
```In /etc/postfix/virtual:
```
my.mail.account@myisp.tld system_user@hostname
```Once again I created the hash of both files:
```
sudo postmap /etc/postfix/generic
sudo postmap /etc/postfix/virtual
```Finally reloaded postfix to apply the new settings:
```
sudo /etc/init.d/postfix reload
```Still don't understand why I had to use both generic and virtual files, but the mail is delivered through my ISP and has my DynDNS domain in the address.

Thank you once again guys, I really learned a lot with this.

---

### Post by frankos44 on 2008-03-14
> **MJN said:**
> Just to add to Zeosa's correct advise, given you're using Postfix the directive you're after is **relayhost = [name.of.relay.server]** (note from the docs that the [] brackets are required in order to force an A record lookup of the name given as opposed to an MX record).
 
Mathew

Hi, on our server we use postfix just for outgoing mail from php only to remind our staff of a pending order.  

The server's domain is hosted at btconnect.com and we use the btconnect.com mail server for the companies general day to day email. 

I assume that Postfix is relaying through btconnect.com but the mail is either blocked or very much delayed.

In this case, do I need to run dpkg-reconfigure postfix as a smarthost?

---

### Post by MJN on 2008-03-14
We'd need to see the logs showing what's currently happening, and indeed a copy of the non-delivery report for when it fails.

Mathew

---

### Post by frankos44 on 2008-03-15
Here are the logs, thanks.

---

### Post by frankos44 on 2008-03-15
> **MJN said:**
> We'd need to see the logs showing what's currently happening, and indeed a copy of the non-delivery report for when it fails.

Mathew

Sorry the I had a senior moment and forgot the attachment.

---

### Post by MJN on 2008-03-15
Those logs show two successful deliveries to the BTConnect server...

..so what's the problem? :confused:

Mathew

---

### Post by frankos44 on 2008-03-15
> **MJN said:**
> Those logs show two successful deliveries to the BTConnect server...

..so what's the problem? :confused:

Mathew

Mail addressed to btopenworld.com always arrives Ok but mail send to marmaladeleasing.co.uk does not.

I realize the mail has left the server but its not being forwarded by marmaladeleasing.co.uk which is hosted at btconnect.com. I assume the relay at btconnect.com is rejecting it.

---

### Post by MJN on 2008-03-15
We'd need to see the non-delivery report as it could be due to one of any number of reasons (most likely anti-spam related).

Mathew

---

### Post by frankos44 on 2008-03-15
> **MJN said:**
> We'd need to see the non-delivery report as it could be due to one of any number of reasons (most likely anti-spam related).

Mathew

I think so too. Where is the non delivery reports stored?

---

### Post by MJN on 2008-03-15
They get sent as an e-mail to the sender by the mail server that failed to deliver the message.

Mathew

---

