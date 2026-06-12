---
title: "SMTP Troubles"
date: 2011-04-30
forum: Server Platforms
---

### Post by s31523 on 2011-04-30
I searched the threads and the only article I found on this issue mentioned that I should relay through my ISP's SMTP server...  I was hoping my problem is different and just a configuration setting...

I followed the tutorial at [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Now, when I attempt to smtp I get the following:
```

$ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 server.com ESMTP Postfix (Ubuntu)
ehlo server.com
250-derver.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN CRAM-MD5 LOGIN NTLM DIGEST-MD5
250-AUTH=PLAIN CRAM-MD5 LOGIN NTLM DIGEST-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:test@server.com
250 2.1.0 Ok
rcpt to:someone@gmail.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
sending mail...
.
250 2.0.0 Ok: queued as BA3061A9C
421 4.4.2 server.com Error: timeout exceeded

```

I don't even know where to begin to debug this problem.  I can telnet to port 25 from outside the localhost on a machine on the outside network, so I think the ISP is NOT blocking port 25 and I have my router port forwarding to the server so I can connect, but the same error happens if I try to send mail.

Can someone point me in the right direction?

---

### Post by koenn on 2011-05-01
looks like the mail server at Google is refusing connections from your server. This is a common problem for mail servers with a dynamic IP adress, no PTR records in DNS, no SPF records, , etc., or a bad rep in anti-spam blacklists 
All of which you can avoid by relaying through your ISP's SMTP, because they have all of that sorted out already.

---

### Post by s31523 on 2011-05-02
OK, sounds plausible.  Thanks for the lead.

Any chance someone can provide more detail on configuring the server to do the mail relay through the ISP's smptp?

---

### Post by koenn on 2011-05-02
maybe:

Edit /etc/postfix/main.cf, and add or edit this line:
```
relayhost = smtp.yourisp.com
```
&& postfix restart

---

### Post by s31523 on 2011-05-02
Thanks, I will try this!  Of course I will need to find out if my ISP allows this and what there smtp information is...

---

### Post by s31523 on 2011-05-03
Before I call ATT (my ISP provider), which I hate doing because their customer service bites, I wanted to be certain what my problem is.

I tried to smtp mail to myself at the service I am running on to see if that worked.  I still get the same error, so I am not sure if relaying would work either.  I will dig up my mail logs and see what they say.

---

### Post by koenn on 2011-05-03
try their website

they keep redirecting me, but since you're a customer, uou can log in and avoid that.

The probably have some info there about smtp servers available to their customers etc.

---

### Post by s31523 on 2011-05-07
I am up an running after many attempts.

Definitely is related to my ISP (ATT) blocking smtp ports.  They seem to block more than just port 25.  I could not get through on port 587 either, which seems to be a common alternative.

ATT will allow rely through their mail server, but it is a tricky process.  The first attempt yielded an error in the mail.log that said the email address (mail from) was not a verified email address.  My server is operating under a different domain name than "att.net" so I wanted the email to be from the domain name of the server.  ATT does allow aliases which you can configure from their web-based email client to add other email names for the primary account, but the domain will be an .att.net domain.  So, I couldn't use ATT for what I wanted. If you wanted to rely using att.net email names, then this would work...

Then I remembered that the domain name I registered (via godaddy) has an email account and I have re-directed that domain to my ddns name that I also use.  So, I tried to relay through the dodaddy email servers.  The email account from godaddy comes with 250 relays a month, so this is sufficient.  

I tried the basic setup for postfix, and kept getting "connection timed out".  This was the case for port 25, and 587.  Godaddy shows their mail server will accept connections from port 80, and I know that port isn't blocked.  Voila!  That worked.  I am using standard, non authenticated mail.  I may try to add the authentication (TLS/SSL) but at this point Im just happy to have it working.  What a pain!

Starting with a clean postfix main.cf file I added the following to connect to the godaddy smtp server:
```

relayhost = [smtpout.secureserver.net]:80
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps=hash:/etc/postfix/sasl_passwd
smtp_sasl_mechanishm_filter=digest-md5
smtp_sasl_security_options=noanonymous

```

I then created the sasl_passwd file:
```

[smtpout.secureserver.net]:80 username:password

```

* Obviously the username:password above I replaced with my real username and passwword...

Then I changed permissions, and hashed then restarted postfix..
```

sudo chmod 600 /etc/postfix/sasl_passwd
sudo postmap hash:/etc/postfix/sasl_passwd
sudo /etc/init.d/postfix reload
sudo /etc/init.d/postfix restart

```

I telnet'd to localhost 25 and did a test email and it showed up... yay!



That was it.  It seems so simple!  I don't think it's possible to run standalone mailservers from residential ISP's and there is no way (I don't think) that receiving mail will work either...  That is, receiving mail under a different username/domain name.  I will play around with that at some point...

Thanks everyone!

---

### Post by SeijiSensei on 2011-05-07
[deleted]

---

### Post by s31523 on 2011-05-07
RE:
> 
relayhost = [smtpout.secureserver.net]:80

What's the point of this?  I used telnet to connect that host on port 80 and got an SMTP server reply.  What happened to standards ([http://www.iana.org/assignments/port-numbers)?](http://www.iana.org/assignments/port-numbers)?)


The point to this is to get postfic to work... My ISP blocks every other port.  (I did not try one of the other ports that godaddy said smtp can connect on).  I was desperate so I figured there is no way they (the ISP) can block port 80 so I tried that.  I realize port 80 is not "standard" but most ISP's (so it seems) are blocking the standard ports for things like ftp, smtp, etc. because they don't want people like us running servers on a residential line.

---

