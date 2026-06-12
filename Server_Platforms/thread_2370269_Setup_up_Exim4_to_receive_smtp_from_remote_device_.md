---
title: "Setup up Exim4 to receive smtp from remote device and then use smtp.myisp.com to send"
date: 2017-09-01
forum: Server Platforms
---

### Post by dnube on 2017-09-01
Hi Folks,
I already have Exim4/Courier setup up to handle email (MX record points straight to my home server which is behind NAT firewall). Would like to enable my mobile devices to use this home server to send email via my isp smtp (ie. smtp.myisp.com). So, mobile device would use something like smtp.myhomeserveraddress.com and then my server would relay to my isp.

How do I achieve this?

Appreciate any and all pointers - the more specific the better.


Dave

---

### Post by SeijiSensei on 2017-09-01
Open a port (>1023) on your firewall and forward it to port 25 of the server.  Tell your mobile clients to use that for SMTP servers.  I have a slightly more elaborate setup than yours, but I send and receive mail from my phone using custom ports for SMTP and IMAP that forward back to my server.

I presume your mail server is configured to accept mail for your domain and deliver it locally (via the "[mydestination]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination")" directive in Postfix).  What does it do with mail for other domains now?  Does it send those messages directly to remote SMTP servers or forwards them through your ISP?  If the latter, you shouldn't need to do anything more.  If it is not so configured, use the "[relayhost](http://www.postfix.org/postconf.5.html#relayhost)" directive in Postfix to forward outbound mail to the ISP.

Oops, I see you're using Exim.  I can't help with that as my initial experiences with Exim many years ago were not happy ones.  I use sendmail primaily and Postfix secondarily.   You'll need to find the equivalent settings for mydestination and relayhost.

---

### Post by dnube on 2017-09-06
UPDATE:
Have been following this guide for configuring Exim4/Courier and Smarthost smtp:
[http://www.spencerstirling.com/computergeek/email.html](http://www.spencerstirling.com/computergeek/email.html)

including the "Smarthost client in CLEAR TEXT" section. Not sure I am interpreting the instructions properly, especially considering that my ISP does not require smtp authentication, and does not use security (ie. uses port 25). Also not sure about the alias issue (ie. smtp.sbcglobal.yahoo.com vs smtp-sbc.mail.yahoo.com) - tried using the "host" command on my own ISP provided smtp address, but I got an IP# instead of a FQDN. 

When I try to send email, via client, with this setup, I get a "The mail server responded: relay not permitted.". Not sure if this is a response from the Ubuntu/Exim4 server or from the ISP smtp server (probably the later).

Appreciate any further suggestions.

Thanks,
Dave

---

### Post by SeijiSensei on 2017-09-07
Have you contacted your ISP and asked about using their servers for forwarding?  It sounds like the server you chose isn't configured to forward mail from unknown domains.  

I often use telnet to test connections with remote mail servers.
```

$ [color=blue]telnet mailserver.example.com 25[/color]
[server displays  banner]
[color=blue]ehlo mailserver.mydomain.com[/color]
[server displays banner]
[color=blue]mail from: [email]me@mydomain.com[/email][/color]
[server: OK]
[color=blue]rcpt to: [email]someone@gmail.com[/email][/color]
[server may say OK or refuse]
[color=blue]data[/color]
[server replies]
[color=blue]This is a sample email message.
.[/color]
[server replies]
[color=blue]^][/color]
telnet>[color=blue]exit[/color]

```

---

