---
title: "Cannot send mail using Dekko"
date: 2016-11-05
forum: Ubuntu Phone and Tablet
---

### Post by sitongia on 2016-11-05
I've configured Dekko on my Nexus 4 (Ubuntu Touch 15.04) using the same settings as my desktop. Receiving mail works. Sending mail returns an alert:

Sending Failed
Sending of the message failed with the following error: 5.7.0 authentication failed

When I look at dekko.dekkoproject.conf, some of the msa.smtp values are empty, even though I filled them in on the phone. So, I've edited that file to fill those fields in, and I still get the same error. For one thing, the conf file doesn't have a password variable, like the IMAP configuration does. That IMAP section has:

imap.AuthType=PlainAuth
imap.auth.pass=xxx
imap.auth.user=###
imap.extension.blacklist=@Invalid()
imap.filterSubscribed=false
imap.host=mail.zaclys.net
imap.method=SSL
imap.needsNetwork=true
imap.port=993
imap.proxy.system=true
imap.ssl.pemPubKey=...

but the SMTP section has:

msa.AuthType=PlainAuth
msa.method=SMTP
msa.smtp.auth.user=###
msa.smtp.burl=false
msa.smtp.host=mail.zaclys.net
msa.smtp.port=465
msa.smtp.starttls=true

Before I edited that, the smtp.auth.user was blank, the smtp.host was blank, the port number was wrong (and was not 25) and starttls was false.

Does anyone have SMTP working from their Touch device? 

I'm going to try adding a password variable.

---

### Post by wlbi on 2016-11-05
[B][COLOR=#000000]msa.AuthType=PlainAuth[/COLOR]
[/B]probably, you need an encrypted authentication.
In the settings of your smtp server, you can choose: no encryption, STARTTLS or SSL/TLS
Maybe you can try this and it will work then :-)

---

### Post by sitongia on 2016-11-06
@wlbi, can that be configured in the GUI? I do need SSL, but the authentication is username/password (so it is PlainAuth?). I'll check with Zaclys about that. What is the value that goes in msa.AuthType? Thanks.

---

### Post by sitongia on 2016-12-14
OTA-14 didn't fix this. I'm sure the settings are right. They work fine on two desktop OSs.

---

### Post by krusty8 on 2016-12-14
Did you raise a bug? Maybe the developers can help.

---

### Post by steve2602 on 2016-12-16
I set up email with my website server, as follows, on my Pro 5
Incoming server (username, password as per server)
IMAP
SSL
Port 993

Outgoing server (username, password as per server)
SSL
Port 465

Works okay (receiving and sending, except that sent emails, which get delivered, aren't copied into the sent folder -- need to look into that, see if it's a bug or my configuration).

---

### Post by sitongia on 2017-01-30
I finally figured this out... I had my account password in the password file for the SMTP server configuration in Dekko. The error message was about authentication. I happened to try erasing that password and... it works now! I'm pretty sure that my ISP requires a password. In Firefox, for example, I have an encrypted password requirement.

---

