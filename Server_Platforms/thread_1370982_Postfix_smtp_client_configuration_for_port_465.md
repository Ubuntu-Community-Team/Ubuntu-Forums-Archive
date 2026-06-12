---
title: "Postfix smtp client configuration for port 465"
date: 2010-01-02
forum: Server Platforms
---

### Post by dmizer on 2010-01-02
Need some help configuring my postfix server to send mail over smtps port 465. My ISP (as is the case with many ISPs), is blocking outbound SMTP, so I need to configure postfix to relay my mail out through my ISPs SMTP servers.

I was able to get it to work with gmail, which uses port 587, by using SASL: [http://www.postfix.org/SASL_README.html#client_sasl](http://www.postfix.org/SASL_README.html#client_sasl) but that configuration is less than ideal as gmail drops the "reply to" address so when people receive my email, it looks like it's from gmail instead of from my server.

If I use my ISP SMTP servers as a relay the "reply to" address is not stripped, but the relay uses ssl over port 465 instead of TLS. According to the SASL readme:
> Postfix does not deliver mail via TCP port 465 (the obsolete "wrappermode" protocol). See TLS_README for a solution that uses the "stunnel" command. 

I've looked at the TLS_README and can't figure out what I need to do. Can someone point me at some concrete examples or give me some pointers on how to configure this?

Thank you.

---

### Post by Barriehie on 2010-01-03
> **dmizer said:**
> Need some help configuring my postfix server to send mail over TLS port 465. My ISP (as is the case with many ISPs), is blocking outbound SMTP, so I need to configure postfix to relay my mail out through my ISPs SMTP servers.

I was able to get it to work with gmail, which uses port 587, by using SASL: [http://www.postfix.org/SASL_README.html#client_sasl](http://www.postfix.org/SASL_README.html#client_sasl) but that configuration is less than ideal as gmail drops the "reply to" address so when people receive my email, it looks like it's from gmail instead of from my server.

If I use my ISP SMTP servers as a relay the "reply to" address is not stripped, but the relay uses TLS port 465 instead of 587. According to the SASL readme:


I've looked at the TLS_README and can't figure out what I need to do. Can someone point me at some concrete examples or give me some pointers on how to configure this?

Thank you.

I'm far from a postifx expert, I'm happy with mine running to/from localhost!, but this [[color="blue"]link[/color]](http://www.eglug.org/book/export/html/1923) might help.  It's pretty straightforward <sp>.

Edit: After looking at the manpage for stunnel it looks like you can specify the port to connect to.

---

### Post by dmizer on 2010-01-06
Thank you so much Barriehie. Unfortunately I'm still having trouble.

Well, it looks like the information on that page is quite old, but it pointed me at least partially in the right direction. After a lot of fiddling, I got stunnel to work successfully from the CLI with the telnet localhost 11125 command.

```
# telnet localhost 11125
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220-smtp.server.com ESMTP Exim 4.69 #1 Wed, 06 Jan 2010 11:42:22 -0500 
220-We do not authorize the use of this system to transport unsolicited, 
220 and/or bulk e-mail.
ehlo
250-smtp.server.com Hello hostname.ne.jp [***.***.***.***]
250-SIZE 52428800
250-PIPELINING
250-AUTH PLAIN LOGIN
250 HELP
^]
telnet> quit
Connection closed.
```

I tried configuring /etc/postfix/main.cf according to the howto you linked to and was not successful. I also tried to modify it according to the postfix TLS readme I linked earlier, and I can't get the two to work together. I just get a "connection timed out error":
```
Jan  7 01:26:35 japan postfix/smtp[14353]: connect to localhost[***.***.***.***]:11125: Connection timed out
```

My current /etc/stunnel/stunnel.conf 
```
[smtp-tls-wrapper]
accept = 11125
client = yes
connect = smtp.server.com:465
```
Relevant portion of my /etc/postfix/main.cf
```
# Outbound SMTP authentication
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
unknown_local_recipient_reject_code = 550
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
relayhost = [localhost]:11125
smtp_use_tls = no
```
Amd my (censored) /etc/postfix/sasl_passwd file
```
[localhost]:11125 user+name@smtp.server.com:password
```
I have also tried
```
[localhost] user+name@smtp.server.com:password
```
Any more ideas on how I can get this authentication to work? One thing that may be important is that my username has a plus sign (+) in it.

---

### Post by Barriehie on 2010-01-06
I just woke up and not much coffee yet... :)  Okay, when this weekend rolls around I'll explore this some some and see about trying some things on my end.  I've got postfix installed and working on this machine so after a backup I'll be good to go.

Barrie

---

### Post by dmizer on 2010-01-06
> **Barriehie said:**
> I just woke up and not much coffee yet... :)  Okay, when this weekend rolls around I'll explore this some some and see about trying some things on my end.  I've got postfix installed and working on this machine so after a backup I'll be good to go.

Barrie

Thanks for the help. I sincerely appreciate it.

One more thing I forgot to link. This Debian admin article has things explained very well, and is what I ultimately modeled my configuration on: [http://www.debian-administration.org/article/Postfix_Smarthost_using_Auth_and_SMTPS](http://www.debian-administration.org/article/Postfix_Smarthost_using_Auth_and_SMTPS)

As indicated above, however, it still does not work and I seem to be missing something fundamental in main.cf.

Thanks again.

---

### Post by Barriehie on 2010-01-06
8)

---

### Post by dmizer on 2010-01-08
Marking this solved because I managed to configure this for TLS using the sasl authentication method rather than trying to tunnel ssl through stunnel.

I finally figured out that the reason my ISP was not authenticating TLS over port 587 was because they are configured to use port 26 instead. #-o

Note:
Although I never got ssl to work, I prefer to use TLS anyway.

---

### Post by Barriehie on 2010-01-08
Glad you got it working!

---

