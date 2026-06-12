---
title: "log files for postfix/sasl?"
date: 2009-06-21
forum: Server Platforms
---

### Post by zim2dive on 2009-06-21
I'm trying to debug an infrequent new mail failure..

I have Squirrelmail running on my webserver... imapd on the machine, so I have my own personal "gmail" setup at home... Trying to wean myself off my ISP addr, I switched to using my hosted web domain ...

so I modified my 5 year old postfix setup and added sasl per the specs given by the web host (hostmonster) so I could relay my outgoing mail thru them (I can't send out directly b/c most mail servers won't accept mail from a dynamic IP addr)

All has been working without a problem for months..... until the past few days... I send maybe 20 emails a day.  I'm get 2-3 per day now that fail and come back with
> host zzzzz[74.220.202.41] said:
550-cpe-066-yyy-102-125.xx.res.rr.com (foo.org) [66.gg.102.125] is
550-currently not permitted to relay through this server. Perhaps you have
not 550-logged into the pop/imap server in the last 30 minutes or do not
have SMTP 550 Authentication turned on in your email client. (in reply to
RCPT TO command) 

I've generated my password and tested the login by hand (telnet to port 25 and auth plain).

The text of the fail message makes me wonder whether my postfix is even trying to authenticate.  I dont seen anything in the mail.log file to indicate any authentication activity.  How can I get more information about the failing transactions?

---

